---
sidebar_position: 7
---

# Setup File Storage

To support the built-in content management system for the blog, we need a reliable file storage solution. I recommend using Backblaze due to its affordability, although Amazon S3 is also a viable option. This tutorial will guide you through setting up Backblaze.

# Video Tutorial
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/an_iWNAh5c8?si=19aF8xNR2G_y4ShA" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

# Written Tutorial

### 1. Register for Backblaze

- Visit [Backblaze](https://www.backblaze.com/) and register for a new account if you don’t already have one.

### 2. Create a New Bucket

- Click the "Create Bucket" button.
- Settings: Since this bucket will store public media and blog images, there is no need to make the bucket private or encrypted. Ensure that public encryption is turned off.

### 3. Create and Apply API Keys

- Create a Backblaze API Key:
  - Navigate to the "Account" section and then to "Application Keys."
  - Click “Add New Application Key.”
  - Settings: Name the key, select the bucket, and allow read and write access. All other settings can be left as default or blank.

- Once your keys are generated, update your `.env` file in your app:
  - `AWS_ACCESS_KEY_ID = [keyID]`
  - `AWS_SECRET_ACCESS_KEY = [applicationKey]`

### 4. Change Site Config Variables

- Return to your bucket in Backblaze and click the "Upload/Download" button.
- Upload a small test image file (e.g., jpg or png) to grab the public link information.
- Once uploaded, note the following values from the image link:
  - `bucket name`
  - `bucket URL`
  
- Update your `site-config.ts` file with these values.

### 5. Test Image Upload

- With your application running (`npm run dev`), navigate to your application in your browser at `http://localhost:3000`.
- Access the admin dashboard at `http://localhost:3000/admin` (you must be an admin to access this page).

Test the image upload functionality to ensure everything is set up correctly.


