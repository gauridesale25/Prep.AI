
Breakdown of the Diagram:
Landing Page – User explores features, optional contact form stored in DB.

Authentication – Clerk manages OAuth sign-in.

Dashboard – Past interviews & questions accessible.

Create Interview – User provides job info → Gemini generates questions → saved to DB.

Start Interview – Webcam + TTS (text-to-speech) display questions.

Record Answer – User answers → Gemini transcribes + analyzes → stores transcript, feedback, score.

Feedback – User reviews performance.

Upgrade Plan – If needed, upgrade via pricing → Stripe → Dashboard refreshed.
<img width="1849" height="3840" alt="Mermaid Chart - Create complex, visual diagrams with text  A smarter way of creating diagrams -2025-09-02-155324" src="https://github.com/user-attachments/assets/edc3e28d-909b-4153-89ec-c7cec5ab0bdc" />

System Architecture Diagram:
<img width="846" height="466" alt="image" src="https://github.com/user-attachments/assets/393f3736-d5c1-4d26-8904-945807c74ba1" />


Entities: Four tables (MockInterview, Question, UserAnswer, Newsletter).

Attributes: Each column is listed with type + PK/FK.

Relationships:

One MockInterview → many Questions.

One MockInterview → many UserAnswers.

UserAnswer.mockIdRef → references MockInterview.mockId.

Newsletter loosely connects to MockInterview (optional, from contact form)
<img width="2228" height="3840" alt="Mermaid Chart - Create complex, visual diagrams with text  A smarter way of creating diagrams -2025-09-02-155909" src="https://github.com/user-attachments/assets/9503bcee-b47b-4290-8aa7-5dd9857cc4d4" />
