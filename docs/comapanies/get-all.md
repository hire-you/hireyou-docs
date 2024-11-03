---
sidebar_position: 3
---

# Get All Companies

This guide explains how to use the **GetAllCompanies** GraphQL query to retrieve company information from the server, including detailed metadata for pagination.

## Query Description

The **GetAllCompanies** query allows you to fetch a paginated list of companies from the server. Each company object contains detailed information about the company, its employers, and stage templates associated with it.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Query Name**: `getAllCompanies`

### Available Fields

The response includes:
- **_metadata**: Pagination metadata such as the current page, page size, and the total number of elements.
- **filters**: A list of filters applied (currently not used).
- **records**: A list of companies with detailed information, including employer details and stage templates.

### Example Query

Here is an example of how to query for companies with pagination parameters `page` and `limit`:

```graphql
query GetAllCompanies($page: Int = 1, $limit: Int = 10) {
  getAllCompanies(page: $page, limit: $limit) {
    _metadata {
      page
      pageSize
      totalElements
    }
    records {
      _id
      name
      industry
      website
      location
      stageTemplates {
        name
        description
      }
    }
  }
}
```

### Example Response

```json
{
  "data": {
    "getAllCompanies": {
      "_metadata": {
        "page": 1,
        "pageSize": 10,
        "totalElements": 50
      },
      "records": [
        {
          "_id": "60d21b4667d0d8992e610c85",
          "name": "Tech Innovators",
          "industry": "Technology",
          "website": "https://techinnovators.com",
          "location": "New York, NY",
          "stageTemplates": [
            {
              "name": "Initial Screening",
              "description": "First stage of the hiring process"
            }
          ]
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
- **`records`**: Array of company objects.
  - **`_id`**: Unique identifier of the company.
  - **`name`**: Name of the company.
  - **`industry`**: Industry sector of the company.
  - **`website`**: Company's website URL.
  - **`location`** _(optional)_: Location of the company.
  - **`stageTemplates`**: Array of stage templates for recruitment.
    - **`name`**: Name of the stage.
    - **`description`**: Description of the stage.

## Notes

- This query provides a paginated response to efficiently handle large amounts of data.
- You can adjust the `page` and `limit` arguments to control the amount of data returned.
- The `_metadata` field is automatically included for pagination purposes.

Feel free to reach out if you need further information or customization options for this query.

