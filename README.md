# Spring AI Microservice Example
This project demonstrates how to integrate a Spring Boot-based microservice with AI models (such as OpenAI or Groq) using the Spring AI library.

## 🧱 Prerequisites
Docker (must be installed and running)

An API key from either OpenAI or Groq

## 🛠️ Setup Steps
### 1. Create or Integrate a Microservice
You can either create a new microservice or integrate Spring AI into an existing one.
Add the following dependency to your build.gradle.kts file:

dependencies {
    // Use this for both OpenAI and Groq models
    implementation("org.springframework.ai:spring-ai-openai-spring-boot-starter:0.7.1")
}
### 2. Generate an API Key
You’ll need an API key to connect to an AI model provider.

OpenAI (Paid):
Go to https://platform.openai.com and generate an API key.
Pricing depends on model (e.g., GPT-4 vs GPT-3.5).

Groq (Free):
Visit https://console.groq.com/keys, sign in (Google login supported), and click “Create API Key”.
⚠️ You can only view the key once, so store it securely.

### 3. Configure Your application.properties
Update your application.properties file based on the provider you're using:

For OpenAI:
properties
Copy
Edit
spring.ai.openai.api-key=PASTE_YOUR_API_KEY_HERE
spring.ai.openai.chat.model=gpt-4-turbo
For Groq:
spring.ai.openai.api-key=PASTE_YOUR_API_KEY_HERE
spring.ai.openai.base-url=https://api.groq.com/openai
spring.ai.openai.chat.options.model=llama3-70b-8192
spring.ai.openai.chat.options.temperature=0.7
### 4. Implement the Service Layer
You can create a new service or extend an existing one.
Ensure you import the necessary classes:

import org.springframework.ai.openai.OpenAiChatModel;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
Example initialization:

private final OpenAiChatModel chatModel;
private static final Logger logger = LoggerFactory.getLogger(YourServiceClass.class);
To call the AI model:

String response = chatModel.call("Give me career advice for a backend developer.");
### 5. Create the Controller
The controller follows the same principles as a regular Spring Boot controller.
Inject your service and expose an endpoint to interact with the AI.
