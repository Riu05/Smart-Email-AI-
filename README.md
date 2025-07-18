Smart Email Assistant

 Features

- REST API endpoint for generating email replies
- Integration with Google Gemini API (via environment variable)
- Dynamic tone support (Professional, Friendly, Casual, etc.)
- CORS enabled for frontend & extension access
- Clean and modular Spring Boot structure

---

 Tech Stack

- **Java 17**
- **Spring Boot**
- **Maven**
- **WebClient (Spring WebFlux)** – for non-blocking HTTP
- **Jackson** – for JSON parsing
- **Lombok** – to reduce boilerplate
- **Google Gemini API** – for AI reply generation

---

API Endpoint

POST /api/email/generate

 Environment Variables
Set the following values in your IntelliJ Run Configuration or system:


GEMINI_API_KEY=your-gemini-api-key
Your application.properties should include:

gemini.api.key=${GEMINI_API_KEY}
gemini.api.url=https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent
spring.cors.allowed-origins=*
server.port=8080
Run the App

# In project root
mvn clean install
mvn spring-boot:run
Make sure your environment variable is active during the run.

Project Structure

email-writer-sb/
├── controller/
│   └── EmailController.java
├── model/
│   └── EmailRequest.java
├── service/
│   └── EmailService.java
├── config/
│   └── WebClientConfig.java
├── util/
│   └── GeminiResponseParser.java
├── application.properties
 What It Does
This backend receives email content + tone, builds a custom prompt, sends it to the Gemini API, parses the reply, and returns it cleanly. Used by both the React frontend and the Chrome extension.

 Built By Riya Singh



Security Note
This project follows environment variable-based secrets management. Never hardcode API keys in public repos.

Testing
Test API using Postman




