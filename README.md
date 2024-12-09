Face Authentication System Using SEAM
This is a React-based face authentication system that uses the face-api.js library for facial recognition. It integrates with a webcam to capture and verify faces against a registered database (e.g., linked to Aadhaar numbers) and provides real-time feedback, including spoof detection mechanisms.
Features
Aadhaar Number Validation: User enters an Aadhaar number which is validated against a registered database.
Face Recognition: Uses facial descriptors for matching faces against the registered users.
Spoof Detection: Detects spoofing attempts using blinking and head movement detection.
Real-time Feedback: Provides feedback about face detection status, spoofing detection, and authentication results.
Webcam Integration: Real-time webcam feed for face recognition and detection.
Technologies Used
React: Frontend framework for building the application UI.
face-api.js: A JavaScript library for face detection and recognition.
Azure: Used for hosting and loading face recognition models (ssdMobilenetv1, faceLandmark68Net, faceRecognitionNet).
ReactWebcam: For capturing real-time webcam feed.

Setup Instructions
Prerequisites
Node.js (v14 or above)
NPM or Yarn
Git
Steps to Run the Application Locally
Clone the repository:

 git clone https://github.com/your-username/face-authentication-system.git


Navigate to the project directory:

 cd face-authentication-system


Install dependencies:

 If you're using npm:

 npm install
 Or, if you're using yarn:

 yarn install


Run the application:

 Start the React development server:

 npm start
 Or:

 yarn start
 The app will be available at http://localhost:3000 in your browser.



Workflow Overview
1. State Management
Tracks the authentication process, matches faces, handles camera errors, and detects spoof attempts.
Manages face detection status, Aadhaar validation, and linked face data.
2. Aadhaar Input & Validation
User enters an Aadhaar number, which is validated against the registered face database.
Provides visual feedback (green/red border) for valid/invalid Aadhaar.
3. Face Matcher Initialization
Loads the face recognition models (ssdMobilenetv1, faceLandmark68Net, faceRecognitionNet) from Azure.
Creates a face matcher with a 0.45 similarity threshold using face descriptors from the registered faces dataset.
4. Webcam Access & Error Handling
Ensures webcam access, streams face detection, and handles errors if the camera is unavailable.

Face Detection & Authentication Workflow
5. Face Detection Process
Detects faces every 100ms:
No face → Prompts the user to look at the camera.
Multiple faces → Warns the user about multiple faces.
One face → Prepares for authentication.
6. Spoof Detection
Monitors blinking and head movement for spoof attempts.
Alerts if spoofing is detected based on inactivity (e.g., no blinking, static face).
7. Face Authentication
Load Registered Dataset: Fetches names.json from the server to retrieve user data and generates face descriptors for each registered image.


Authenticate Button: Enabled when:


Valid Aadhaar and linked face.
Single face detected, no spoofing.
Captures a screenshot, compares face descriptors, and authenticates if a match is found.
Handle Authentication: On successful authentication, sets authenticatedUser and redirects to /profile.



Models and Datasets
Face Recognition Models:


The system loads face recognition models (ssdMobilenetv1, faceLandmark68Net, faceRecognitionNet) from Azure to perform real-time face detection and recognition.
Registered Dataset:


names.json is used to fetch registered user data. Face descriptors are generated for each user's registered image and stored in registeredFaces for future authentication checks.

Running Tests
Unit tests: To run unit tests for your React app:

 npm test
 Or:

 yarn test


End-to-end tests: If you want to set up end-to-end testing, you can use libraries like Cypress or Jest to simulate interactions and ensure the face authentication process works as expected.



Deployment
To deploy this app on a server:
Build the app:

 npm run build


Deploy: Deploy the build/ directory to your preferred hosting platform (e.g., Vercel, Netlify, AWS, Azure).



Contributing
If you'd like to contribute to the project:
Fork the repository.
Create a new branch for your feature (git checkout -b feature-name).
Make your changes and commit them (git commit -am 'Add feature').
Push your branch (git push origin feature-name).
Create a pull request.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgements
face-api.js for the face detection and recognition models.
ReactWebcam for webcam integration.
Azure for hosting the face recognition models.
