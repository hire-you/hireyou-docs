---
sidebar_position: 7
---

# Get All Applications

This guide explains how to use the **GetAllApplications** query to retrieve a paginated list of applications from the server.

## Query Description

The **GetAllApplications** query allows you to retrieve a paginated list of applications, which includes details such as the candidate, job, status, application stages, and timestamps.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Query Name**: `getAllApplications`

### Parameters

- **page** (integer, optional): Page number for pagination (default is 1).
- **limit** (integer, optional): Number of records per page (default is 10).

### Example Query

Here is an example of how to retrieve a paginated list of applications:

```graphql
query GetAllApplications($page: Int, $limit: Int) {
  getAllApplications(page: $page, limit: $limit) {
    records {
      _id
      candidate
      job
      applicationDate
      status
      stages {
        name
        description
        order
        assign_roles
        assignments
        feedback {
          aiFeedback
          interviewerFeedback
        }
        approved
      }
      createdAt
      updatedAt
    }
  }
}
```

### Example Variables

```json
{
  "page": 1,
  "limit": 5
}
```

### Example Response

```json
{
  "data": {
    "getAllApplications": {
      "records": [
        {
          "_id": "64b456f4e14d16bc9df12345",
          "candidate": "64a123f4e14d16bc9df67890",
          "job": "64a456f4e14d16bc9df12345",
          "applicationDate": "2024-11-01T10:00:00.000Z",
          "status": "IN_PROGRESS",
          "stages": [
            {
              "name": "Initial Screening",
              "description": "First round of screening with HR",
              "order": 1,
              "assign_roles": [
                "64a789f4e14d16bc9df98765"
              ],
              "assignments": [
                "64a987f4e14d16bc9df54321"
              ],
              "feedback": {
                "aiFeedback": "Candidate shows strong alignment with company culture.",
                "interviewerFeedback": "Good communication skills, needs improvement in technical knowledge."
              },
              "approved": true
            }
          ],
          "createdAt": "2024-11-01T10:00:00.000Z",
          "updatedAt": "2024-11-02T15:30:00.000Z"
        }
      ]
    }
  }
}
```

### Response Fields

- **`records`**: Array of application records.
  - **`_id`**: Unique identifier for the application.
  - **`candidate`**: ID of the candidate who applied.
  - **`job`**: ID of the job associated with the application.
  - **`applicationDate`**: The date when the application was made.
  - **`status`**: The current status of the application (`IN_PROGRESS` or `FINISHED`).
  - **`stages`**: Array of stages related to the application.
    - **`name`**: Name of the application stage.
    - **`description`**: Description of the application stage.
    - **`order`**: Order of the application stage in the process.
    - **`assign_roles`**: Array of IDs representing assigned recruiters/interviewers.
    - **`assignments`**: Array of IDs representing tasks or assignments.
    - **`feedback`**: Feedback provided at each stage.
      - **`aiFeedback`**: Feedback provided by AI.
      - **`interviewerFeedback`**: Feedback provided by the interviewer.
    - **`approved`**: Whether the candidate was approved at this stage.
  - **`createdAt`**: Timestamp indicating when the application was created.
  - **`updatedAt`**: Timestamp indicating the last time the application was updated.

### Notes

- You can specify the **page** and **limit** to control pagination.
- The **records** field contains the list of applications. Only the records need to be queried directly.
- Metadata regarding pagination will be handled automatically.

If you need further assistance, feel free to reach out!

