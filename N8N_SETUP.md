# N8N Chatbot — Setup (5 minutes)

The chatbot in `engineering-suite.html` talks to OpenAI through one small n8n workflow.
Everything is pre-built — **you only add your OpenAI API key.**

## Steps

1. **Import the workflow**
   - Open your n8n → top-right menu (⋮) → **Import from File**
   - Choose `n8n-chatbot-workflow.json` (in this folder)

2. **Add your OpenAI credential**
   - Click the **OpenAI Chat** node → *Credential to connect with* → **Create new**
   - Pick **OpenAI API**, paste your API key, save. (That's the only thing you change.)

3. **Activate**
   - Toggle the workflow **Active** (top-right). This publishes the production webhook.

4. **Check the URL matches the website**
   - The webhook path is `engineering-chatbot`, so the production URL is:
     `https://<your-n8n>/webhook/engineering-chatbot`
   - The HTML is already set to: `https://oussama19.app.n8n.cloud/webhook/engineering-chatbot`
   - If your n8n host is different, update `N8N_WEBHOOK_URL` near the top of the
     `<script>` block in `engineering-suite.html`.

5. **Test**
   - Open the website, click the purple chat bubble (bottom-right), send a message.
   - You should get a reply within a few seconds.

## How it works (for reference)

```
Webhook (POST /engineering-chatbot)
   → Build System Prompt   (picks BOM / TC / General prompt based on payload.product,
                            and injects the on-screen context the website sends)
   → OpenAI Chat           (gpt-4o-mini · max 600 tokens · temp 0.4)
   → Respond to Webhook    (returns { "reply": "..." } to the website)
```

The website sends `{ message, context, product }`; the workflow returns `{ reply }`.
Model/temperature/token limit can be tweaked in the **OpenAI Chat** node if needed.
