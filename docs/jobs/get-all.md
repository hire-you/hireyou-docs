---
sidebar_position: 5
---

# Get All Jobs

This guide explains how to use the **GetAllJobs** GraphQL query to retrieve job information from the server, including detailed metadata for pagination.

## Query Description

The **GetAllJobs** query allows you to fetch a paginated list of jobs from the server. Each job object contains detailed information about the job, including company details, tags, and stages.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Query Name**: `getAllJobs`

### Available Fields

The response includes:
- **_metadata**: Pagination metadata such as the current page, page size, and the total number of elements.
- **filters**: A list of filters applied (currently not used).
- **records**: A list of jobs with detailed information, including tags and stages.

### Example Query

Here is an example of how to query for jobs with pagination parameters `page` and `limit`:

```graphql
query GetAllJobs($page: Int = 1, $limit: Int = 10) {
  getAllJobs(page: $page, limit: $limit) {
    _metadata {
      page
      pageSize
      totalElements
    }
    records {
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
}
```

### Example Response

```json
{
  "data": {
    "getAllJobs": {
      "_metadata": {
        "page": 1,
        "pageSize": 10,
        "totalElements": 100
      },
      "records": [
        {
          "_id": "64a123f4e14d16bc9df12345",
          "company": "64a456f4e14d16bc9df12345",
          "title": "Software Engineer",
          "status": "IN_PROGRESS",
          "description": "We are looking for a talented software engineer...",
          "contractType": "Full-time",
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
          ],
          "createdAt": "2024-10-20T10:00:00.000Z",
          "updatedAt": "2024-10-25T15:30:00.000Z"
        }
      ]
    }
  }
}
```

### Parameters

- **`page`** _(optional)_: The page number to retrieve (default: 1).
- **`limit`** _(optional)_: The number of records to retrieve per page (default: 10).

### Response Fields

- **`_metadata`**: Provides pagination information.
  - **`page`**: Current page number.
  - **`pageSize`**: Number of records per page.
  - **`totalElements`**: Total number of available records.
- **`filters`**: Array of strings (default: empty).
- **`records`**: Array of job objects.
  - **`_id`**: Unique identifier of the job.
  - **`company`**: Unique identifier of the company associated with the job.
  - **`title`**: Title of the job.
  - **`status`**: Current status of the job (e.g., `IN_PROGRESS` or `FINISHED`).
  - **`contractType`**: Type of contract (e.g., `Full-time`, `Part-time`).
  - **`description`**: Description of the job.
  - **`employmentType`**: Type of employment (e.g., `ONSITE`, `REMOTE`, `HYBRID`).
  - **`tags`**: Array of job tags.
    - **`name`**: Name of the tag.
    - **`type`**: Type of the tag (`SKILL` or `POSITION`).
    - **`proficiencyLevel`**: Proficiency level required for the tag.
  - **`stages`**: Array of stages in the hiring process.
    - **`name`**: Name of the stage.
    - **`description`**: Description of the stage.
    - **`order`**: Order of the stage in the process.
  - **`createdAt`**: Timestamp indicating when the job was created.
  - **`updatedAt`**: Timestamp indicating the last time the job was updated.

## Notes

- This query provides a paginated response to efficiently handle large amounts of job data.
- You can adjust the `page` and `limit` arguments to control the number of records returned.
- The `_metadata` field is automatically included to assist with pagination.

If you need further customization or additional details for this query, feel free to reach out!

