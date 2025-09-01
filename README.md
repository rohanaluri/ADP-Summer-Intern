This project aims to extract important employee information (DOB, SSN, EmployeeID, Taxes, Deductions) from payroll PDF documents from vendors and output the information in structured JSON format. It consists of three files with contents as seen below:

Connecting to API with Integrated GUI:

  - Collects client_id, document_id, and vendor; confirms inputs; sends JSON payload to API https://56t4splb05.execute-api.us-east-1.amazonaws.com/extract/extract.

  - Displays extraction status and basic errors in a ProcessWindow; allows returning to home or exiting.

  - Dependancies: PyQt5, requests.

Initializing the LLM:

  - Maps vendors to local test PDFs via vendor_pdfs.

  - Defines standardized JSON schema for fields: Name, Employee ID, Pay Date, Earnings, Payroll Codes, Net Pay.

  - Instantiates AzureChatOpenAI (gpt-4-turbo, temperature=0, seed=12); requires AZURE_OPENAI_ENDPOINT, OPENAI_API_VERSION.

Source Code for Extraction and Accuracy:

  - Uses PyMuPDF (fitz) to read PDF text; builds vendor-specific prompts; calls LLM; cleans and parses JSON output.

  - Aggregates results per vendor and compares to ground_truths to report overall and per-vendor accuracy.

  - Tracks token usage/cost via get_openai_callback and expects llm, templates, examples, and vendor_pdf variables from configuration.
