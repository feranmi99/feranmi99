- 👋 Hi, I’m Oluwaferanmi
- 👀 I’m interested in collaboration and working with group 
- 🌱 I’m currently learning laravel
- 💞️ I’m looking to collaborate on full-stack developer 
- 📫 How to reach me 08149445103

<!---
feranmi99/feranmi99 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
/*
Run this model in Javascript

> npm install @mistralai/mistralai
*/
import { Mistral } from '@mistralai/mistralai';

// To authenticate with the model you will need to generate a personal access token (PAT) in your GitHub settings. 
// Create your PAT token by following instructions here: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
const token = process.env["GITHUB_TOKEN"];

export async function main() {
  const client = new Mistral({
    apiKey: token,
    serverURL: "https://models.inference.ai.azure.com"
  });

  const response = await client.chat.complete({
    model: "Codestral-2501",
    messages: [
      { role:"system", content: "" },
      { role:"user", content: "What is the capital of France?" }
    ],
    temperature: 0.8,
    max_tokens: 2048,
    top_p: 0.1
  });

  console.log(response.choices[0].message.content);
}

main().catch((err) => {
  console.error("The sample encountered an error:", err);
});
