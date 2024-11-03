---
sidebar_position: 6
---

# Create a Job

This guide explains how to use the **CreateJob** mutation to add a new job to the server.

## Mutation Description

The **CreateJob** mutation allows you to create a new job with details such as the job title, company, employment type, tags, and hiring stages.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Mutation Name**: `createJob`

### Required Fields

To create a new job, you need to provide the following details:

- **company**: The unique identifier (ID) of the company to which the job belongs.
- **title**: The title of the job.
- **description**: The description of the job.
- **status**: The status of the job (`IN_PROGRESS` or `FINISHED`).
- **contractType**: The type of job contract (e.g., `Full-time`, `Part-time`).
- **employmentType**: The type of employment (`ONSITE`, `REMOTE`, `HYBRID`).

### Optional Fields

- **tags**: A list of tags associated with the job. Each tag includes:
  - **name**: The name of the tag.
  - **type**: The type of the tag (`SKILL` or `POSITION`).
  - **proficiencyLevel**: The proficiency level required for the tag.

- **stages**: A list of recruitment stages associated with the job. Each stage includes:
  - **name**: The name of the stage.
  - **description**: The description of the stage.
  - **order**: The order of the stage in the hiring process.

### Example Mutation

Here is an example of how to create a job:

```graphql
mutation CreateJob($input: CreateJobInput!) {
  createJob(input: $input) {
    _id
    company
    title
    status
    description
    contractType
    employmentType
    tags {
      name
      type
      proficiencyLevel
    }
    stages {
      name
      description
      order
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
    "company": "64a456f4e14d16bc9df12345",
    "title": "Software Engineer",
    "status": "IN_PROGRESS",
    "contractType": "Full-time",
    "description": "We are looking for a talented software engineer...",
    "employmentType": "REMOTE",
    "tags": [
      {
        "name": "JavaScript",
        "type": "SKILL",
        "proficiencyLevel": 4
      }
    ],
    "stages": [
      {
        "name": "Technical Interview",
        "description": "Technical interview with the engineering team",
        "order": 1
      }
    ]
  }
}
```

### Example Response

```json
{
  "data": {
    "createJob": {
      "_id": "64a123f4e14d16bc9df12345",
      "company": "64a456f4e14d16bc9df12345",
      "title": "Software Engineer",
      "status": "IN_PROGRESS",
      "contractType": "Full-time",
      "employmentType": "REMOTE",
      "description": "We are looking for a talented software engineer...",
      "tags": [
        {
          "name": "JavaScript",
          "type": "SKILL",
          "proficiencyLevel": 4
        }
      ],
      "stages": [
        {
          "name": "Technical Interview",
          "description": "Technical interview with the engineering team",
          "order": 1
        }
      ],
      "createdAt": "2024-10-20T10:00:00.000Z",
      "updatedAt": "2024-10-25T15:30:00.000Z"
    }
  }
}
```

### Parameters

- **`input`**: Object containing the fields to create a new job.

### Response Fields

- **`_id`**: Unique identifier for the created job.
- **`company`**: Unique identifier for the company associated with the job.
- **`title`**: Title of the job.
- **`status`**: Status of the job (`IN_PROGRESS` or `FINISHED`).
- **`description`**: Description of the job.
- **`contractType`**: Type of contract (e.g., `Full-time`, `Part-time`).
- **`employmentType`**: Type of employment (`ONSITE`, `REMOTE`, `HYBRID`).
- **`tags`**: Array of job tags.
  - **`name`**: Name of the tag.
  - **`type`**: Type of the tag (`SKILL` or `POSITION`).
  - **`proficiencyLevel`**: Proficiency level required for the tag.
- **`stages`**: Array of recruitment stages.
  - **`name`**: Name of the recruitment stage.
  - **`description`**: Description of the recruitment stage.
  - **`order`**: Order of the recruitment stage in the process.
- **`createdAt`**: Timestamp indicating when the job was created.
- **`updatedAt`**: Timestamp indicating the last time the job was updated.

## Notes

- Ensure that all required fields are provided when creating a job.
- The mutation enables you to create comprehensive job descriptions, including detailed tags and stages for the hiring process.

If you need any additional customization or further information, feel free to reach out!