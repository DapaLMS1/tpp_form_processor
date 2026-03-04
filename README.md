TPP Editor Prototype - Phase 1

This project is a high-fidelity web prototype designed to streamline the completion of Training Plan Proposals (TPP) using AI-assisted data extraction. It allows users to upload legacy PDF or image-based documents and automatically maps the contents to a modern, responsive web form.

Key Features

Intelligent Field Mapping: Utilizes a "Fuzzy Matching" logic to connect extracted data to form fields, even when naming conventions differ (e.g., "Mailing Address" vs "Street Address").

AI-Powered OCR: Integrated with Gemini 2.5 Flash to process complex document layouts, identifying both text inputs and categorical data (radio button selections).

Gap Analysis Reporting: Includes a "Mapping Report" feature that notifies the user if fields were identified in the source document that do not exist on the current web form, ensuring data integrity.

Responsive Accordion UI: A clean, sectioned interface built with Tailwind CSS that organizes long-form TPP data into manageable logical blocks.

Technical Architecture

1. Data Extraction Pipeline

The application captures the document as a Base64 string and transmits it to the Gemini API. We provide a "Schema Hint" in the system prompt, which includes all the data-field keys present in the DOM. This guides the AI to prioritize the specific data structure required by the UI.

2. Fuzzy Matching Logic

The mapping engine performs the following steps:

Normalization: Both the extracted keys and the DOM attributes are converted to lowercase and stripped of non-alphanumeric characters.

Field Matching: Direct matches are applied to data-field attributes.

Option Matching: For radio buttons, the system matches both the group name and the specific value (e.g., mapping "M" to the "Male" radio option).

3. Error Handling & Resilience

Exponential Backoff: Implements a retry mechanism (up to 5 attempts) for API communication to handle rate limits or network instability.

Visual Feedback: Real-time status updates and spinners keep the user informed during the extraction process.

How to Use

Open the index.html file in a browser.

Expand the accordion sections to view the empty fields.

Upload a PDF or Image of a TPP document in the upload area.

Wait for the AI to process the document.

Review the auto-populated fields and any "Unmapped Fields" reported in the yellow notification box.

Future Roadmap

Stage 2: Integration with Firestore for cross-session persistence.

Stage 3: Collaborative editing and digital signature workflows.
