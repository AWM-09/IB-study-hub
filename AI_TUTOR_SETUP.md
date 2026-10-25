# AI tutor deployment

The static GitHub Pages site cannot run the server-side AI endpoint. Deploy this repository to Vercel (or another Node.js serverless host) to enable `/api/teach`.

## Setup

1. Sign in to Vercel and import the GitHub repository `AWM-09/IB-study-hub`.
2. In the Vercel project, open **Settings → Environment Variables** and add:
   - `OPENAI_API_KEY`: your OpenAI API key. Keep this secret; never put it in `index.html` or commit it to GitHub.
   - `TUTOR_ACCESS_CODE`: a long, private passphrase you choose. You will enter this into the AI tutor box on your own device.
   - Optional: `OPENAI_MODEL`: the model to use. Defaults to `gpt-5.5`.
3. Redeploy after saving the environment variables.
4. Open the Vercel deployment URL, upload your material, enter the `TUTOR_ACCESS_CODE` in the AI tutor panel and click **Save code on this device**.
5. Choose **Teach me this topic in depth**. The AI tutor will generate a detailed lesson from the extracted contents. Choose **Test me on this material** to generate a practice set.

## Important

- The AI tutor uses the OpenAI API. API usage is billed separately from a ChatGPT subscription and requires API access/billing on the OpenAI Platform.
- Do not share your API key or commit it to the repository. Only store it as a server-side environment variable.
- The access code is a basic personal-use gate, not a full user account system. Keep it private and rotate it if you believe it has been shared.
- The tutor can only teach from text extracted from the uploaded file. Scanned PDFs and images need OCR, which is not currently included.
- The model is instructed to flag uncertain facts and avoid inventing dates, but you should still verify high-stakes factual details and compare lessons with your class materials.
- GitHub Pages will not run `api/teach.js`. Use the Vercel deployment URL for the AI tutor, unless you separately configure another serverless backend and point the frontend at it.
