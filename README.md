# Serverless-AI-Powered-Healthcare-Diagnostic-Pipeline-with-AWS-Gemini-AI-API

The healthcare industry is generating more diagnostic data than ever, but manual interpretation remains a bottleneck. To bridge this gap, I’ve built a fully automated, serverless medical report analysis system on AWS, integrated with Google’s Gemini API.
Here’s how the architecture works and why it’s a game-changer for digital health workflows:
1. Secure Ingestion: A hospital staff member uploads a patient report via a web portal. To ensure security, the system uses AWS API Gateway and a Lambda function to generate an S3 Presigned URL. This allows the client to upload the file directly to a private S3 bucket without exposing the backend.
2.  Event-Driven Metadata: Simultaneously, patient metadata (Name, Doctor, ID) is stored in Amazon DynamoDB, ensuring a decoupled and highly available data layer.
3.  The AI Trigger: As soon as the PDF hits Amazon S3, an asynchronous event notification triggers the core AI-Processor Lambda.
Text Extraction: Using the PyPDF2 library, the system extracts raw clinical data from the report.
Biomarker Analysis: The extracted fields are sent to the Gemini API. I engineered a custom prompt that instructs the model to identify specific biomarkers and flag them as Normal or Abnormal based on clinical ranges.
4. Diagnostic Reasoning: Beyond simple flagging, Gemini synthesizes the findings into a Diagnostic Summary. It explains why certain values are concerning while intelligently filtering out "minute noise"—minor deviations that aren't clinically significant.
5. Instant Notification: Once the analysis is complete, results are written to a second DynamoDB table, and Amazon SNS sends an automated email to the assigned doctor with the full AI-generated interpretation.

This project was a deep dive into building production-ready AI pipelines on the cloud. I’m excited about the potential of Generative AI to act as a diagnostic assistant, reducing the cognitive load on healthcare professionals.
Video Link: https://drive.google.com/file/d/1z6nMvKmFX9F4vTCIu2hq6jOggKlqbx1S/view?usp=sharing
