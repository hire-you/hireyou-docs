---
sidebar_position: 8
---

# Create an Application

This guide explains how to use the **CreateApplication** mutation to create a new application.

## Mutation Description

The **CreateApplication** mutation allows you to create a new application, which includes details about the candidate, job, application stages, and additional information.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Mutation Name**: `createApplication`

### Input Fields

- **candidate** (ID, required): The ID of the candidate applying.
- **job** (ID, required): The ID of the job for which the candidate is applying.
- **applicationDate** (Date, required): The date when the application is made.
- **status** (string, required): The current status of the application (`IN_PROGRESS` or `FINISHED`).
- **stages** (array of objects, optional): List of stages for the application process.
  - **name** (string, required): Name of the stage.
  - **description** (string, required): Description of the stage.
  - **order** (integer, required): Order of the stage in the process.
  - **assign_roles** (array of IDs, optional): IDs of assigned recruiters/interviewers.
  - **assignments** (array of IDs, optional): IDs of assignments or tasks.
  - **feedback** (object, optional): Feedback details for the stage.
    - **aiFeedback** (string, optional): Feedback provided by AI.
    - **interviewerFeedback** (string, optional): Feedback provided by the interviewer.
  - **approved** (boolean, optional): Indicates if the candidate was approved at this stage.

### Example Mutation

Here is an example of how to create a new application:

```graphql
mutation CreateApplication($input: CreateApplicationInput!) {
  createApplication(input: $input) {
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
```

### Example Variables

```json
{
  "input": {
    "candidate": "64a123f4e14d16bc9df67890",
    "job": "64a456f4e14d16bc9df12345",
    "applicationDate": "2024-11-01T10:00:00.000Z",
    "status": "IN_PROGRESS",
    "stages": [
      {
        "name": "Initial Screening",
        "description": "First round of screening with HR",
        "order": 1,
        "assign_roles": ["64a789f4e14d16bc9df98765"],
        "assignments": ["64a987f4e14d16bc9df54321"],
        "feedback": {
          "aiFeedback": "Candidate shows strong alignment with company culture.",
          "interviewerFeedback": "Good communication skills, needs improvement in technical knowledge."
        },
        "approved": true
      }
    ]
  }
}
```

### Example Response

```json
{
  "data": {
    "createApplication": {
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
          "assign_roles": ["64a789f4e14d16bc9df98765"],
          "assignments": ["64a987f4e14d16bc9df54321"],
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
  }
}
```

### Response Fields

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

- Ensure all required fields are provided in the mutation.
- The **stages** field can be used to define specific stages and feedback within the application process.

If you need further assistance, feel free to reach out!

