--- 
sidebar_position: 7

# Update a Job

This guide explains how to use the **UpdateJob** mutation to modify an existing job's details on the server.

## Mutation Description

The **UpdateJob** mutation allows you to update an existing job with details such as the job title, description, status, company, employment type, tags, and hiring stages.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Mutation Name**: `updateJob`

### Required Fields

To update a job, you need to provide the following details:

- **id**: The unique identifier (ID) of the job you wish to update.
- **inputUpdate**: The fields that need to be updated. These fields can include:
  - **title**: The updated title of the job.
  - **description**: The updated description of the job.
  - **status**: The updated status of the job (`IN_PROGRESS`, `FINISHED`, etc.).
  - **contractType**: The updated type of job contract (e.g., `Full-time`, `Part-time`).
  - **employmentType**: The updated type of employment (`ONSITE`, `REMOTE`, `HYBRID`).
  - **tags**: A list of tags associated with the job. Each tag includes:
    - **name**: The name of the tag.
    - **type**: The type of the tag (`SKILL`, `POSITION`).
    - **proficiencyLevel**: The proficiency level required for the tag.
  - **stages**: A list of recruitment stages associated with the job. Each stage includes:
    - **name**: The name of the stage.
    - **description**: The description of the stage.
    - **order**: The order of the stage in the hiring process.

### Example Mutation

Here is an example of how to update a job:

```graphql
mutation UpdateJob($id: String!, $inputUpdate: UpdateJobInput!) {
  updateJob(_id: $id, input: $inputUpdate) {
    _id
    title
    description
    status
    company {
      _id
    }
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
    updatedAt
  }
}
```

### Example Variables

```json
{
  "id": "672d5c22a495ad38c0f92a06",
  "inputUpdate": {
    "title": "Novo Título do Jobbbbb",
    "description": "Descrição atualizada do Job",
    "status": "FINISHED",
    "contractType": "Contrato Atualizado",
    "employmentType": "REMOTE",
    "tags": [
      { "name": "React", "type": "SKILL", "proficiencyLevel": 4 },
      { "name": "Teste", "type": "SKILL", "proficiencyLevel": 4 },
      { "name": "Teste 3", "type": "SKILL", "proficiencyLevel": 4 }
    ],
    "stages": [
      { "name": "Nova Entrevista", "description": "Entrevista com o time", "order": 1 }
    ]
  }
}
```

### Example Response

```json
{
  "data": {
    "updateJob": {
      "_id": "672d5c22a495ad38c0f92a06",
      "title": "Novo Título do Jobbbbb",
      "description": "Descrição atualizada do Job",
      "status": "FINISHED",
      "company": {
        "_id": "64a456f4e14d16bc9df12345"
      },
      "contractType": "Contrato Atualizado",
      "employmentType": "REMOTE",
      "tags": [
        {
          "name": "React",
          "type": "SKILL",
          "proficiencyLevel": 4
        },
        {
          "name": "Teste",
          "type": "SKILL",
          "proficiencyLevel": 4
        },
        {
          "name": "Teste 3",
          "type": "SKILL",
          "proficiencyLevel": 4
        }
      ],
      "stages": [
        {
          "name": "Nova Entrevista",
          "description": "Entrevista com o time",
          "order": 1
        }
      ],
      "updatedAt": "2024-11-07T10:00:00.000Z"
    }
  }
}
```

### Parameters

- **`id`**: The unique identifier of the job to update.
- **`inputUpdate`**: Object containing the fields to be updated for the job.

### Response Fields

- **`_id`**: Unique identifier for the updated job.
- **`title`**: The updated title of the job.
- **`description`**: The updated description of the job.
- **`status`**: The updated status of the job (`IN_PROGRESS` or `FINISHED`).
- **`company`**: Unique identifier for the company associated with the job.
- **`contractType`**: Updated type of contract (e.g., `Full-time`, `Part-time`).
- **`employmentType`**: Updated type of employment (`ONSITE`, `REMOTE`, `HYBRID`).
- **`tags`**: Array of updated job tags.
  - **`name`**: Name of the tag.
  - **`type`**: Type of the tag (`SKILL` or `POSITION`).
  - **`proficiencyLevel`**: Updated proficiency level required for the tag.
- **`stages`**: Array of updated recruitment stages.
  - **`name`**: Name of the recruitment stage.
  - **`description`**: Description of the recruitment stage.
  - **`order`**: Order of the recruitment stage in the process.
- **`updatedAt`**: Timestamp indicating the last time the job was updated.

## Notes

- Ensure that all required fields are provided when updating a job.
- The mutation enables you to update comprehensive job details, including title, description, tags, and recruitment stages.

If you need any additional customization or further information, feel free to reach out!