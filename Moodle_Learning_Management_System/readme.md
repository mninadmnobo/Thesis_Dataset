# Moodle Functional Testing Dataset

## About Moodle

Moodle is the world's most widely used open-source learning management system (LMS). It enables educators to create and manage online courses, deliver content, assess students, and facilitate collaboration. This dataset covers both the student and teacher perspectives as separate JSON files.

## Requirements

- Docker
- Docker Compose

## Note

The Moodle source code is included to ensure full offline reproducibility
of the benchmark environment.

## Start the System

```bash
docker compose up -d
```

The first build will take several minutes as it compiles Moodle from source.

## Access the Application

http://localhost:8080

## Credentials

| Role | Username | Password |
|------|----------|----------|
| Admin | admin | Admin@123 |
| Teacher | testteacher | Test@1234 |
| Teacher 2 | testteacher2 | Test@1234 |
| Student | teststudent | Test@1234 |
| Student 2 | teststudent2 | Test@1234 |

See `credentials.txt` for full enrollment details.

## Dataset

Two JSON files provide functional descriptions for each role:

### `moodle_student.json` (10 sections)
- Login, Dashboard, My Courses
- Course Page (View Only), Participants, Grades
- Assignment, Activities, Profile, Logout

### `moodle_teacher.json` (13 sections)
- Login, Dashboard, My Courses
- Course Page, Adding Activities, Course Settings
- Participants, Assignment (Teacher View), Assignment Submissions
- Advanced Grading, Gradebook, Profile, Logout

These descriptions serve as input for a multi-agent system that generates positive, negative, and edge test cases for automated web testing research.

## Folder Structure

```
moodle/
  docker-compose.yml          # Docker deployment config
  Dockerfile                  # Moodle container build
  docker-entrypoint.sh        # Container startup script
  setup-test-data.php         # Creates test users, courses, enrollments
  credentials.txt             # All test account details
  readme.md                   # This file
  moodle_student.json         # Student functional descriptions (JSON)
  moodle_student.md           # Student functional descriptions (Markdown)
  moodle_teacher.json         # Teacher functional descriptions (JSON)
  moodle_teacher.md           # Teacher functional descriptions (Markdown)
  moodle-src/                 # Moodle source code (Docker build context)
```
