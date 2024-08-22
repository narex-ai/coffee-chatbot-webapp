# Coffee Chatbot WebApp

## Overview
An interactive chatbot built with Next.js that answers user questions about coffee. Designed for seamless web interaction, it delivers quick, informative responses while tracking user interactions.

## Features
- Conversational AI interface for coffee-related questions
- Real-time interaction through a web interface
- Request/response traces captured with Monocle
- Traces stored securely in AWS S3 for analysis

## Tech Stack
- **Frontend & Backend:** Next.js
- **Hosting & Storage:** AWS (S3 for traces)
- **Observability:** Monocle

## Deployment
1. Clone the repository  
2. Install dependencies:
```bash
   npm install
```
3. Configure AWS credentials for S3
4. Run the development server:

```bash
npm run dev
```
5. Access the app at http://localhost:3000

## Usage
- Type your coffee-related question into the chat interface
- Receive AI-powered answers instantly
- Interaction traces are automatically pushed to S3 for monitoring

## Contributing
Contributions are welcome! Please open issues or pull requests for improvements or feature requests.