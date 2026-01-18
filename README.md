# Student-gradebook
This project focuses on the design and development of a Student Gradebook Single Page Application (SPA) implemented as a web application using React.js
Student Gradebook — MVP (SPA)

A lightweight Single Page Application (SPA) for managing a student gradebook (students, courses, assignments, and grades) with an interactive dashboard and local data persistence. The project is designed as an MVP and runs entirely in the browser.

Features
Core Modules

Dashboard

Class average (%)

Course averages (%)

Assignment averages (raw score average)

Student overall performance (%)

Students

Add / edit / delete students

Email validation + duplicate email prevention

Search by name or email

Courses

Add / rename / delete courses

Prevent deletion when assignments exist for a course

Assignments

Add / edit / delete assignments

Course filter

Prevent invalid max points and missing fields

Grades

Editable grade-entry grid (student × assignment)

Filters by course and student

Score clamping (0 → maxPoints)

Data Management

Export JSON backup (gradebook.json)

Import JSON restore

Reset to demo dataset

Data Persistence

Uses browser localStorage (key: gradebook:v1) to store all application data locally. 

index

Accessibility & UI

Responsive layout, clean UI styling, and accessible tab navigation (ARIA attributes included for tabs). 

index

Tech Stack

HTML5 / CSS3

JavaScript

React 18 (CDN)

ReactDOM (CDN)

Babel Standalone (CDN) for JSX in-browser
All dependencies are loaded via CDN and bundled in a single HTML file. 

index

Getting Started
Option A: Run directly (simplest)

Download or clone this repository

Open index.html in your browser (Chrome/Edge recommended)

Note: Some browsers may restrict certain features when opening files directly. If you face issues, use Option B.

Option B: Run with a local web server (recommended)

From the project folder:

Using Python

python -m http.server 8080


Then open:

http://localhost:8080

Using Node

npx serve .

Usage Guide

Go to Students → add students (name + valid email required)

Go to Courses → add courses (e.g., Math, Biology)

Go to Assignments → create assignments (course, title, max points, due date)

Go to Grades → enter scores in the grid

Check Dashboard to see computed averages

Use Data tab to export/import backups

Data Model (Schema)

The app maintains the following structure:

{
  "students": [{ "id": "...", "name": "...", "email": "..." }],
  "courses": [{ "id": "...", "name": "..." }],
  "assignments": [{ "id": "...", "courseId": "...", "title": "...", "maxPoints": 100, "dueDate": "YYYY-MM-DD" }],
  "grades": [{ "id": "...", "studentId": "...", "assignmentId": "...", "score": 0 }]
}

Validation Rules (Implemented)

Student name required

Student email must be valid format

Student email must be unique

Assignment requires:

valid courseId

non-empty title

maxPoints > 0

Grades:

Automatically clamped: 0 <= score <= maxPoints

Built-in Smoke Tests

On load, the app runs basic console smoke tests for average calculations and logs:

Smoke tests: OK ✔️ (when successful) 

index

Open your browser dev tools → Console to view results.

Project Structure

This MVP is intentionally simple:

index.html — contains UI, styles, React components, state management, localStorage persistence, and basic tests (single-file SPA). 

index

Roadmap / Next Improvements

Replace CDN + Babel with a production build (Vite/CRA) for performance

Add authentication and roles (teacher/admin)

Add weighted grading and configurable grading scales (A–F)

Add CSV import/export for roster/grades

Add chart visualizations (performance trends)

Add automated unit tests (Jest/Vitest)
