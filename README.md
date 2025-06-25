# AI Business Chatbot Builder

Welcome to the **AI Business Chatbot Builder**! This project is a Python-based implementation of an AI-powered chatbot designed for small businesses. It combines a simple knowledge base with an AI model to provide helpful and friendly responses to common business-related questions.

---

## Code Features

### 1. Knowledge Base Integration

* A predefined dictionary holds business details, FAQs, and contact information.
* Example:

  ```python
  knowledge_base = {
      "business_name": "Pages & Chapters Bookstore",
      "business_type": "Bookstore",
      "about": "A cozy bookstore offering new and used books, reading events, and a quiet café with coffee and pastries",
      "common_questions": {
          "What are your hours?": "We’re open Monday-Saturday 9 AM - 7 PM, Sunday 10 AM - 5 PM",
          "Where are you located?": "We’re at 456 Book Lane, near the city library",
      },
      "contact_info": {
          "phone": "555-READ-456",
          "email": "hello@pagesandchapters.com",
          "website": "www.pagesandchapters.com"
      }
  }
  ```

### 2. AI Model Integration

* Uses the Hugging Face `DialoGPT-small` model to generate AI responses.
* Configured for focused and natural replies.

  ```python
  model_name = "microsoft/DialoGPT-small"
  tokenizer = AutoTokenizer.from_pretrained(model_name)
  model = AutoModelForCausalLM.from_pretrained(model_name)
  ```

### 3. Chatbot Logic

* Matches user questions to predefined answers or generates responses using AI.
* Example function:

  ```python
  def enhanced_chatbot_response(query):
      if not query or not query.strip():
          return "Please ask me a question about our business!"

      query_lower = query.lower().strip()

      # Check for matching FAQs
      for question, answer in knowledge_base["common_questions"].items():
          if question.lower() in query_lower:
              return answer

      return "I’m here to help with questions about our business!"
  ```

### 4. Simple Web Interface

* Built with Gradio to provide an easy-to-use chat interface.
* Example:

  ```python
  interface = gr.Interface(
      fn=enhanced_chatbot_response,
      inputs="text",
      outputs="text",
      title="AI Business Chatbot",
      description="Ask me about our business!"
  )
  ```

---

## Libraries Used

* **transformers**: For the AI model.
* **torch**: For backend AI computations.
* **gradio**: For creating the web interface.

---

## Design Highlights

* **Customizable**: Easily update the knowledge base with your business details.
* **Fallback Support**: Handles questions even if the AI model is unavailable.
* **User-Friendly**: Simple logic ensures clear and helpful responses.
