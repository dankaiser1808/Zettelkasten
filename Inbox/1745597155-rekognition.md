---
id: 1745597155-rekognition
aliases:
  - Rekognition
tags: []
---

# Rekognition
Rekognition works as a content recognition service. It can recognize videos or images and generate tags/ key words based on the content. This comes in handy if we want to label the videos or images for quicker filtering and search or moderate the content based on the resulting keywords since we might want to regulate inappropriate content. So all in all, it works as a monitoring, reviewing and management tool of user generated content, based on certain guidelines if needed.

A common workflow could look like this:

1. User Content is uploaded to S3
2. Lambda is triggered by upload, lambda sends content to rekognition
3. Rekognition scans content and gives us a confidence level based on guidelines.
4. Rekognition either stores the user content directly in the database or queues it for human review.


Features:
- Object and Scene Detection
- Facial Analysis and recognition
- Text in Image
- Activity Detection
- Unsafe Content Detection
- Celebrity recognition
- Custom Labels
- Integration with other AWS services
- Emotion Detection
- Real-Time Analysis

