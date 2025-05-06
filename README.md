# Week-10 Assignment - MERN Stack Deployment to AWS

**Student ID:** SDA2002-Ibrahim  
**Repository:** https://github.com/Ibrahim-Technical/the-tenth-assignement-

## Project Overview

This project demonstrates the deployment of a full-stack MERN (MongoDB, Express, React, Node.js) blog application to AWS. It includes:

- Frontend hosted on S3 (React + Vite)
- Backend hosted on an EC2 instance
- MongoDB Atlas as the database
- Media storage handled via a dedicated S3 bucket
- PM2 used to ensure backend process persistence

## Technologies Used

- AWS EC2
- AWS S3
- MongoDB Atlas
- PM2
- Vite + React
- Node.js + Express

## Deployment Steps

1. **Clone Project Repositories**
   - Cloned the project to the EC2 Ubuntu instance.

2. **MongoDB Setup**
   - Created and configured a MongoDB Atlas cluster.
   - Whitelisted the EC2 IP and created a user with credentials.
   - Updated the `.env` file with the correct MongoDB URI.

3. **Backend Configuration and Launch**
   - Installed dependencies using `npm install`.
   - Configured `.env` file for API and media URL.
   - Started the server using `pm2 start`.

4. **Frontend Build and Deployment**
   - Navigated to the frontend directory.
   - Ran `npm run build` to generate the production-ready files.
   - Used AWS CLI to sync the `dist/` folder to the S3 bucket.
   - Applied proper bucket policy to allow public access.

5. **Media Bucket**
   - Created a separate bucket `ibrahim-blogapp-media` for file uploads.
   - Updated frontend `.env` to use media bucket URL.

6. **Testing**
   - Verified backend response via EC2 public IP and port 5000.
   - Ensured frontend loads correctly from the S3 website endpoint.
   - Confirmed media uploads and API interactions.

## Problems Faced and Solutions

- **Access Denied on S3 Frontend Bucket**  
  *Solution:* Updated bucket policy to allow `s3:GetObject` for all.

- **CORS Issues During API Calls**  
  *Solution:* Configured proper CORS middleware in Express backend.

- **MongoDB Connection Errors**  
  *Solution:* Ensured IP was whitelisted and credentials matched.

- **Frontend not Building**  
  *Solution:* Installed all dependencies and ensured environment variables were set before build.

- **Persistent Server Issues**  
  *Solution:* Used PM2 to run and monitor the backend as a daemon process.

## Deliverables

- `screenshots/`: Folder containing screenshots for each deployment step.
- This `README.md`: Documenting the entire workflow.

## Note

All AWS credentials (access keys) were excluded and the IAM user has been deleted post-deployment as instructed.
