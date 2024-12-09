# Face Authentication System Using SEAM

This is a React-based face authentication system leveraging the face-api.js library for facial recognition. It integrates with a webcam to capture and verify faces against a registered database (e.g., linked to Aadhaar numbers) and provides real-time feedback, including spoof detection mechanisms.

## Features
- Aadhaar Number Validation: Validates user-input Aadhaar numbers against a registered database.
- Face Recognition: Matches user faces with registered profiles using facial descriptors.
- Spoof Detection: Detects spoofing attempts through blinking and head movement detection.
- Real-time Feedback: Displays feedback on face detection status, spoof detection, and authentication results.
- Webcam Integration: Provides a real-time webcam feed for face recognition and detection.

## Technologies Used
- React: Frontend framework for building the application UI.
- face-api.js: JavaScript library for face detection and recognition.
- Azure: Hosts and loads face recognition models (ssdMobilenetv1, faceLandmark68Net, faceRecognitionNet).
- ReactWebcam: Captures real-time webcam feed.

## Setup Instructions

### Prerequisites
- Node.js (v14 or above)
- NPM or Yarn
- Git

### Steps to Run the Application Locally
1. Clone the repository:
   ```
   git clone https://github.com/your-username/face-authentication-system.git
   ```

2. Navigate to the project directory:
   ```
   cd face-authentication-system
   ```

3. Install dependencies:
   - Using npm:
     ```
     npm install
     ```
   - Or, using yarn:
     ```
     yarn install
     ```

4. Run the application:
   - Start the React development server:
     ```
     npm start
     ```
   - Or:
     ```
     yarn start
     ```
   - The app will be available at http://localhost:3000 in your browser.

## Workflow Overview
1. State Management: Tracks authentication progress, matches faces, handles camera errors, and detects spoof attempts.
2. Aadhaar Input & Validation: Validates Aadhaar numbers and provides visual feedback (green/red border) for validity.
3. Face Matcher Initialization: Loads face recognition models and initializes a face matcher with a 0.45 similarity threshold.
4. Webcam Access & Error Handling: Manages webcam access, streams detection data, and handles camera-related errors.

## Face Detection & Authentication Workflow
1. Face Detection Process:  
   Detects faces every 100ms:  
   - No face: Prompts the user to look at the camera.  
   - Multiple faces: Warns about multiple faces.  
   - Single face: Prepares for authentication.

2. Spoof Detection:  
   Monitors blinking and head movement. Alerts on spoof attempts (e.g., no blinking or static face).  

3. Face Authentication:  
   - Fetches `names.json` to retrieve user data and generate face descriptors.  
   - Authenticates users based on Aadhaar validation, single-face detection, and anti-spoof measures.  
   - Captures a screenshot, compares descriptors, and authenticates matches. Redirects authenticated users to `/profile`.

## Models and Datasets
- Face Recognition Models:  
  Loads models (ssdMobilenetv1, faceLandmark68Net, faceRecognitionNet) from Azure for real-time face detection and recognition.
- Registered Dataset:  
  Uses `names.json` to fetch registered user data. Generates and stores face descriptors for authentication.

## Running Tests
- Unit Tests:  
  To run unit tests:
  ```
  npm test
  ```
  Or:
  ```
  yarn test
  ```

- End-to-end Tests:  
  Use libraries like Cypress or Jest to simulate interactions and validate the face authentication process.

## Deployment
1. Build the app:
   ```
   npm run build
   ```

2. Deploy the `build/` directory to a hosting platform such as Vercel, Netlify, AWS, or Azure.

## Contributing
1. Fork the repository.
2. Create a new branch for your feature:
   ```
   git checkout -b feature-name
   ```
3. Make your changes and commit them:
   ```
   git commit -am 'Add feature'
   ```
4. Push your branch:
   ```
   git push origin feature-name
   ```
5. Create a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgements
- face-api.js for face detection and recognition models.
- ReactWebcam for webcam integration.
- Azure for hosting face recognition models.
