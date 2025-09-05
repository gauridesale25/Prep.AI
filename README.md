## 📝 System Workflow

### 1. Landing Page  
- Users explore platform features.  
- Optional **Contact Form** data is stored in the database.  

### 2. Authentication  
- Handled via **Clerk** for secure OAuth sign-in.  

### 3. Dashboard  
- Users can view past interviews and generated questions.  

### 4. Create Interview  
- User provides job details.  
- **Gemini API** generates relevant interview questions.  
- Questions are saved to the database.  

### 5. Start Interview  
- Interview begins with **webcam + TTS (Text-to-Speech)** for question delivery.  

### 6. Record Answer  
- User responds via webcam/microphone.  
- **Gemini** transcribes and analyzes the response.  
- Transcript, feedback, and score are stored in the database.  

### 7. Feedback  
- User can review detailed performance reports and insights.  

### 8. Upgrade Plan  
- Users can upgrade via **Pricing Page → Stripe Integration**.  
- Dashboard updates automatically after successful payment.  



## System Architecture

### Overview
The system is designed to support mock interviews with automatic question handling, user responses, scoring, and newsletter integration.

### Components

- **Frontend (React.js)**
  - Provides UI for mock interview selection, answering questions, and viewing feedback.
  - Handles form submissions for newsletter subscription.

- **Backend (Node.js / Express)**
  - API endpoints for mock interviews, questions, answers, and newsletter.
  - Business logic for evaluating user answers, storing feedback, and managing sessions.

- **Database (PostgreSQL)**
  - Stores mock interview data, questions, user answers, and newsletter subscriptions.

- **AI/ML Layer **
  - Evaluates user answers (transcripts, feedback, scoring).
  - Provides recommendations for improvement.


<img width="846" height="466" alt="image" src="https://github.com/user-attachments/assets/393f3736-d5c1-4d26-8904-945807c74ba1" />
## Database Schema

### Entities & Attributes

- **MockInterview**
  - `mockId` (Primary Key, INT, AUTO_INCREMENT)
  - `jobTitle` (VARCHAR)
  - `createdAt` (TIMESTAMP)

- **Question**
  - `questionId` (Primary Key, INT, AUTO_INCREMENT)
  - `mockIdRef` (Foreign Key → MockInterview.mockId)
  - `questionText` (TEXT)

- **UserAnswer**
  - `answerId` (Primary Key, INT, AUTO_INCREMENT)
  - `mockIdRef` (Foreign Key → MockInterview.mockId)
  - `questionIdRef` (Foreign Key → Question.questionId)
  - `answerText` (TEXT)
  - `transcript` (TEXT)
  - `feedback` (TEXT)
  - `score` (INT)

- **Newsletter**
  - `newsletterId` (Primary Key, INT, AUTO_INCREMENT)
  - `email` (VARCHAR)
  - `mockIdRef` (Optional Foreign Key → MockInterview.mockId)

---

### Relationships

- One **MockInterview** → Many **Questions**
- One **MockInterview** → Many **UserAnswers**
- `UserAnswer.mockIdRef` → references **MockInterview.mockId**
- **Newsletter** loosely connects to **MockInterview** (optional, from contact form)

<img width="2228" height="3840" alt="Mermaid Chart - Create complex, visual diagrams with text  A smarter way of creating diagrams -2025-09-02-155909" src="https://github.com/user-attachments/assets/9503bcee-b47b-4290-8aa7-5dd9857cc4d4" />
