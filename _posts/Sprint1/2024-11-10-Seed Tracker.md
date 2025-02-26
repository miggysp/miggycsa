---
layout: post
title: Seed Tracker
courses: {'csa': {'week': 21}}
type: ccc
comments: True
---

<iframe src="https://drive.google.com/file/d/1bzdbtELmoROzjF4t1ouYr7ogAQNR4l4Z/preview" width="640" height="480" allow="autoplay"></iframe>

# Seed Tracker

## Introduction

Seed Tracker is an intelligent grading and progress-tracking system designed to help students and teachers monitor academic performance efficiently. Using automated data analysis and real-time feedback, Seed Tracker ensures that students stay on top of their learning progress.

## Key Features

Real-Time Grade Monitoring: Tracks student scores and provides instant updates.

Automated Performance Analysis: AI-driven insights highlight strengths and weaknesses.

Assignment & Test Tracking: Logs and visualizes performance trends over time.

Mobile Integration: Access reports and notifications on your phone.

Custom Alerts: Get notified about upcoming deadlines and grade changes.

## CSS Styling
General Design: The styles make the form look clean and modern with rounded corners, subtle shadows, and distinct color accents (red for buttons, blue for text). Flexbox is used to center the content vertically and horizontally.

Modals: Each modal (like seedStarterModal, classroomConductModal, etc.) is hidden by default with the modal-overlay class (display: none). When activated, they appear in the center of the screen with a semi-transparent background.

Buttons: There are buttons for increasing and decreasing scores for different categories like "Seed Starter" and "Classroom Conduct." The buttons have hover effects to change color.

## JavaScript Logic
Score management:

scores object stores the scores for each category (Seed Starter, Classroom Conduct, etc.).
adjustScore(id, change) is used to increase or decrease the score for each category. The score is updated with the changes and displayed.
updateTotalSeed() is called to update the total score based on the individual category scores.
Modal interaction:

openModal(id) and closeModal(id) control the visibility of each modal. When a button is clicked, it triggers openModal with the respective modal ID (e.g., seedStarterModal).
The modal allows the user to adjust scores for each category using buttons like +1.0, +0.5, etc.
Form Submission:

submitEntry() sends the student's data (ID, name, subject, activity log, and score) to a backend server via a POST request. It uses fetch to send the data to a Java backend (localhost:8085/api/seeds/). If successful, the entry ID is shown on the page.
Backend Connection:

The testBackendConnection() function checks if the backend is working by sending a GET request to localhost:8085/api/seeds/. It logs the result in the console.
## Backend Integration
Sending Data: When the "Submit Entry" button is clicked, the form data (including the total seed value) is compiled into an object (entryData) and sent as a JSON payload to the backend API (POST /api/seeds/).
Server Response: After submission, if the backend is successful, it returns the entry.id, which is displayed on the page. Otherwise, an error message is shown.
## User Interaction
Input Validation: Before submission, it checks if the necessary fields (Student ID, Name, Subject, and Activity Log) are filled out. If not, an error message appears.

Modal Controls: In each modal, you can adjust the score for different categories using both small incremental buttons (e.g., +0.01, +0.25) and larger buttons to add or subtract more substantial amounts.

## Key Functions
adjustScore(id, change): This is the core function to update scores.
submitEntry(): Handles submitting the form and sending the data to the server.
openModal(id) and closeModal(id): Control opening and closing the modals for score adjustment.
testBackendConnection(): Tests if the backend is available by sending a GET request.