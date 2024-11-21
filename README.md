# demo-pdf-lib-generator
This application allows users to generate PDF files from JSON input containing an article title, article content, and an image. The app can run locally using Serverless Offline or be deployed to AWS Lambda.

# Features
- Generate a PDF file with title, content, and an image.
- Provide a URL to download the generated PDF file.
- Can be run locally using Serverless Offline.
- Can be deployed to AWS Lambda.

# Prerequisites
- Node.js (version 14 or newer).
- AWS CLI (for deployment to AWS).
- Serverless Framework (for managing and deploying the app).
- An AWS account with proper access to Lambda and API Gateway.

# Installation
1.  Local Installation
    - To run this app locally, make sure you have Node.js and Serverless Framework installed.
    - Steps:
      1. Clone the repository:
         ```
         git clone https://github.com/username/repository-name.git
         cd repository-name
         ```
      2. Install dependencies: Make sure you're in the project folder and run the following to install the dependencies:
         ```
         npm install
         ```
      3. Install Serverless Offline Plugin: Install the serverless-offline plugin to run the Lambda
         ```
         npm install serverless-offline --save-dev
         ```
      4. Start the Local Server: Run the app locally using Serverless Offline:
         ```
         sls offline start
         ```
2.   Running the App Locally
     - To create a PDF locally, you can send a POST request to the endpoint http://localhost:3000/dev/local/create-pdf using Postman or curl.
     - Sample Request:
       - Use the following JSON body to send a request:
         ```
         {
              "title": "Article Title This contains the title of the article",
              "content": "This is the article content that will be displayed in the PDF. Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
              "imageUrl": "https://via.placeholder.com/300.jpg"
         }
         ```
       - Successful JSON response:
         ```
         {
              "message": "PDF created successfully",
              "pdfUrl": "http://localhost:3000/dev/local/files/<file-name>.pdf"
         }
         ```
3.  Downloading the PDF File
    - After the PDF is created, you can use the URL provided in the pdfUrl to download the generated PDF:
      ```
      http://localhost:3000/dev/local/files/<file-name>.pdf
      ```

# Deploying to AWS
  To deploy this app to AWS, you will need to have AWS CLI installed and configured with the proper credentials.

  - Steps:
    1. Ensure AWS CLI is configured: If not already configured, set up your AWS CLI credentials using the following command:
       ```
       aws configure
       ```
    2. Deploy the app to AWS: Use the following command to deploy the app to AWS Lambda:
       ```
       sls deploy
       ```
    3. Access the app on AWS: Once the deployment is complete, you will receive an API Gateway URL. Use this URL to send requests to the deployed API.
    4. Accessing the PDF on AWS
       - After deploying to AWS, you can use the URL to access the generated PDF:
         ```
         https://your-api-id.amazonaws.com/dev/local/files/<file-name>.pdf
         ```
