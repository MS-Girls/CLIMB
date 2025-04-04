<p align="center">
<img height="120" alt="microsoft-logo" src="./assets/mst.png" />
<img height="120" alt="azure-logo" src="./assets/azurelogo.png" />
</p>

# <p align="center">CLIMB - CAREER LADDER IMPROVEMENT & MANAGEMENT BOT</p>

CLIMB is a comprehensive web application designed to help job seekers prepare effectively for their interviews. The platform provides tailored guidance through various features, including ATS score evaluation for resumes, company-specific question bank and topic-specific interview questions, resume-based interview questions, and AI-powered cover letter generation. By leveraging Azure AI services and modern web technologies, the application ensures an optimized and structured approach to interview preparation.
<br />
<br />

<p align="center">
 <a href="https://climbfe-fnf2d2fnc7cfg4a0.southindia-01.azurewebsites.net/" target="_blank"><img src="./assets/site.png" alt="site" height="40" /></a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="https://www.youtube.com/watch?v=e-3YUCDzJn0" target="_blank"><img src="./assets/youtube.png" alt="demovideo" height="40" /></a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="./assets/CLIMB_ppt.pdf" target="_blank"><img src="./assets/ppt.jpeg" alt="ppt" height="40" /></a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="https://github.com/MS-Girls/CLIMB" target="_blank"><img src="./assets/github.png" alt="github" height="40" /></a>
</p>

## **Table of Contents**
1. [Features](#features)
2. [Azure Services Used](#azure-services-used)
3. [Technologies Used](#technologies-used)
4. [Tools Used](#tools-used)
5. [Architecture](#architecture)
    - [Frontend](#frontend)
    - [Backend](#backend)
6. [Team Members](#team-members)
7. [Development](#development)
8. [License](#license)

## **FEATURES**

#### 1. ATS Score Checking & Resume Optimization

- Analyzes resumes for Applicant Tracking System (ATS) compatibility.
- Provides a score based on structure, keywords, formatting, and readability.
- Suggests improvements to enhance visibility in job applications.

#### 2. Company-Specific Online Assessment (OA) Questions

- Curated OA questions for various companies.
- Helps in practicing real-world coding and problem-solving questions.
- Enhances preparation for company-specific hiring challenges.

#### 3. Topic-Specific Interview Questions

- Provides technical interview questions based on the selected topics.
- Covers DSA, system design, databases, OOPs, web development, AI/ML, and more.
- Helps in structured interview preparation.

#### 4.  Resume-Based Interview Questions

- Generates personalized interview questions based on experience, projects, and skills.
- Helps in preparing relevant answers before the actual interview.
- Suggests improvements to the answers thus given.

#### 5. AI-Powered Cover Letter Generation

- Generates customized cover letters based on resume content, job role and job description.
- Includes a Copy to Clipboard feature for easy pasting and usage.
- Adapts the content and structure to match different job roles and industries.

## **AZURE SERVICES USED**

#### 1. Azure Blob Storage

Azure Blob Storage is used to store resumes and other documents securely, enabling fast retrieval for processing. It provides cloud storage, ensuring that user-uploaded files are efficiently managed and accessible when needed

#### 2.  Azure Document Intelligence (OCR)

Azure Document Intelligence, specifically the ```read``` model has been utilised to extract and process text from the resumes. The extracted content is then sent to the AI-model for personalized interview preparation.

#### 3. Azure AI Foundry

Utilised Azure AI Foundry, specifically the ```Phi-4-mini-instruct``` model, that powers the generation of contextual interview questions and cover letters. It enables the application to provide AI-driven responses by understanding user input and generate accurate solutions.


#### 4. Azure App Service

Responsible for containerized deployment of frontend (Next.js application) and backend (ASP.NET Core server) with Docker for efficiency in an automated manner using Github Actions, by leveraging Docker hub.

## **TECHNOLOGIES USED**

#### 1. Next.js

Next.js is used for building the frontend, providing a fast user experience with server-side rendering and static site generation. It ensures seamless navigation and improved performance.

#### 2. Tailwind CSS and Material UI

Used Tailwind CSS for a flexible and utility-first approach to styling, while Material UI provides pre-built, accessible components for a modern and interactive design.

#### 3. C# and ASP.NET Core

C# and ASP.NET Core power the backend, providing a robust and scalable architecture. ASP.NET handles API requests, processes business logic, and integrates with Azure services for data retrieval and processing.

#### 4. Docker

Docker is used for containerizing the application, making it easy to deploy across different environments while maintaining consistency and reducing complexity of environment setup.

#### 5. Docker Hub

Docker Hub serves as the central repository for storing and managing Docker images, enabling efficient deployment of the application

#### 6. Github Actions

Utilised to instantiate CI/CD pipeline inorder to ensure smooth development, automated testing and deployment. It streamlines the development workflow by reducing manual intervention

#### 7. Git and GitHub

Git and GitHub are used for version control and collaboration, allowing seamless tracking of code changes, efficient team collaboration, and secure code management.

## **TOOLS USED**

#### 1. Visual Studio Code

Visual Studio Code (VS Code) is a lightweight and versatile code editor used for writing, debugging, and managing code across multiple programming languages. It offers features like syntax highlighting, auto-completion and extensions to enhance productivity.

#### 2. GitHub Copilot

GitHub Copilot is an AI-powered coding assistant that helps developers by suggesting code snippets, autocompleting functions, and generating entire blocks of code. It enhances productivity by reducing repetitive tasks and providing real-time coding assistance.

## **ARCHITECTURE**

<img alt="architecture" src="./assets/architecture_dig.png" width="750" />

### BACKEND

The backend built using C# and ASP.NET Core provides REST endpoints for the frontend to implement the various features, thus managing the flow between frontend and Azure Services.

#### 1. Resume Storage and Retrieval

When a user uploads a resume via the frontend, it is attached to a FormData element and sent to the backend via a POST request. The backend then uploads the resume to Azure Blob Storage Container. This is implemented in the ```Blob Storage Service``` in the dotnet backend

#### 2. Text Extraction (OCR)

The uploaded resume is retrieved from Azure Blob Storage Container and the URL is then passed to Azure Document Intelligence ```read``` model inorder to extract content from the document. This is implemented in the ```OCR Service``` in the dotnet backend

#### 3. Querying and Response Generation

Once the resume content and the user provided inputs are ready, the backend interacts with the ```Phi-4-mini-instruct``` model via structured prompts to generate relevant content. This model is made available via Azure AI Foundry and is implemented in the ```Chat Services``` module of the backend. The following tasks are then implemented:

- **ATS Analysis & Resume Feedback:** The resume text is analyzed to provide insights and improvement suggestions.
- **Cover Letter Generation:** The AI generates a professional cover letter based on the extracted resume details.
- **Topic-Specific & Resume based Interview Questions:** The backend sends user-defined topics, job roles and the resume to the model, which generates domain-specific questions.
- **Answer Evaluation:** For structured interview preparation, the AI model assesses user-provided answers and returns feedback on correctness, clarity, and depth.

#### 4. REST API Endpoints

All of these functionalities are constructed into REST API Endpoints to facilitate seamless communication between the frontend and the backend services

### FRONTEND

#### 1. Chat Interface

The frontend includes a conversational chat interface that enables users to give inputs to the backend. It also provides links to the questions on the OA practise module of the application

#### 2. Document Upload

Users can upload resumes using an intuitive drag-and-drop or file selection interface. A real-time progress indicator provides feedback on the upload status

#### 3. Feature Overview and Navigation

The frontend includes a centralized dashboard that provides a clear overview of all available features, thus enabling the user to navigate seamlessly between different functionalities of the application

## **TEAM MEMBERS**

#### 1. R S Kierthana : [LinkedIn](https://www.linkedin.com/in/kierthana-rajesh-8b8b42256/) [GitHub](https://github.com/KierthanaRS)

#### 2. Priyanka S : [LinkedIn](https://www.linkedin.com/in/priyanka-s-4b324b26b/) [GitHub](https://github.com/PRIYANKAS3110)

#### 3. S Ramya : [LinkedIn](https://www.linkedin.com/in/ramyas467/) [GitHub](https://github.com/ramya487)

## **DEVELOPMENT**

There are two methods that are available to set up the server. One is to set up the server in the local environment and the other one is to use docker. The individual frontend and the backend repositories outline the steps to do the same

## **LICENSE**
CLIMB is licensed under MIT license, thus allowing permissive usage for your needs. For more information, refer to the [LICENSE](LICENSE) file
