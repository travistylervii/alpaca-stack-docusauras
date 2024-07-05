---
sidebar_position: 10
---

# Setup OpenAi API / GPT

## Video Tutorial
### Setup OpenAI Integration
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/1DptalaXRCo?si=QOuuEk3MpZOtkMkl" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

## Written Tutorial
To integrate the OpenAI API into your project, follow these steps:

### 1. Sign Up for OpenAI API
- Visit [OpenAI](https://openai.com/) and navigate to the projects and OpenAI API login page.
- Register for an account.

### 2. Create API Key

- Once registered, log in to the API dashboard and create a new project.
- After creating a new project, click the “API keys” button on the left side menu.
- On the top right, click the “Create new secret key” button to generate a new key.
- Copy the generated API key.

### 3. Update Environment Variables

- Open the `.env` file in your app's source code.
- Add the following line to the `.env` file, replacing `[your-key]` with the key you copied:

```typescript
OPENAI_API_KEY=[your-key]
```

### 4. Test the Integration
- You can now use the ChatGPT function inside the `/lib/chatGPT` folder in the app.
- Test it out using a server component to ensure everything is set up correctly.


