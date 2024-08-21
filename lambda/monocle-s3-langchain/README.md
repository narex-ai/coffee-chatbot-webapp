# Monocle S3 Langchain Lambda

## Prerequisites

1. Update the credentials in `template.yaml` before deploying:
   - BUCKET_NAME: Your S3 bucket name
   - OPENAI_API_KEY: Your OpenAI API key
   - MONOCLE_AWS_ACCESS_KEY_ID: AWS access key for S3
   - MONOCLE_AWS_SECRET_ACCESS_KEY: AWS secret key for S3

## Vector Store Setup

1. Add your text content to `coffeeText.js`

2. Generate embeddings using OpenAI API:
   ```bash
   # Install OpenAI package
   npm install openai

   # Create a script to generate embeddings
   node generateEmbeddings.js
   ```

   Example generateEmbeddings.js:
   ```javascript
   const OpenAI = require('openai');
   const fs = require('fs');
   const { coffeeText } = require('./coffeeText');

   const openai = new OpenAI({
     apiKey: 'your-api-key'
   });

   async function generateEmbeddings() {
     const response = await openai.embeddings.create({
       model: "text-embedding-ada-002",
       input: coffeeText,
     });
     
     const embeddings = response.data[0].embedding;
     fs.writeFileSync('coffeeEmbedding.json', JSON.stringify(embeddings, null, 2));
   }

   generateEmbeddings();
   ```

3. Store the generated embeddings in `coffeeEmbedding.json`

## Deployment

Deploy the application using AWS SAM:

1. Build the application:
   ```bash
   sam build
   ```

2. Deploy to AWS:
   ```bash
   sam deploy --guided
   ```

3. Follow the prompts to configure your deployment:
   - Stack Name: Choose a name for your CloudFormation stack
   - AWS Region: Choose your target region
   - Confirm changes before deploy: Yes
   - Allow SAM CLI IAM role creation: Yes
   - Save arguments to configuration file: Yes

4. Wait for the deployment to complete. SAM will provide the Lambda function's ARN in the outputs.