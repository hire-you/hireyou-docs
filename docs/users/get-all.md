---
sidebar_position: 9
---

# Get All Users

This guide explains how to use the **GetAllUsers** query to retrieve a paginated list of users in the system.

## Query Description

The **GetAllUsers** query allows you to retrieve user details, including their metadata, filters, and records.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Query Name**: `getAllUsers`

### Input Arguments

- **page** (integer, optional): The page number to retrieve. Default is `1`.
- **limit** (integer, optional): The number of items per page. Default is `10`.

### Example Query

Here is an example of how to retrieve a list of users:

```graphql
query GetAllUsers($page: Int, $limit: Int) {
  getAllUsers(page: $page, limit: $limit) {
    _id
    name
    email
    authUserId
    role
    createdAt
    updatedAt
  }
}
```

### Example Variables

```json
{
  "page": 1,
  "limit": 10
}
```

### Example Response

```json
{
  "data": {
    "getAllUsers": {
      "_metadata": {
        "page": 1,
        "pageSize": 10,
        "totalElements": 100
      },
      "filters": [],
      "records": [
        {
          "_id": "64c123f4e14d16bc9df67890",
          "name": "John Doe",
          "email": "john.doe@example.com",
          "authUserId": "auth0|abcd1234",
          "role": "CANDIDATE",
          "createdAt": "2024-10-01T10:00:00.000Z",
          "updatedAt": "2024-10-05T15:30:00.000Z"
        },
        {
          "_id": "64c456f4e14d16bc9df12345",
          "name": "Jane Smith",
          "email": "jane.smith@example.com",
          "authUserId": "auth0|efgh5678",
          "role": "RECRUITER",
          "createdAt": "2024-10-03T12:00:00.000Z",
          "updatedAt": "2024-10-07T16:45:00.000Z"
        }
      ]
    }
  }
}
```

### Response Fields

- **`_metadata`**: Pagination details.
  - **`page`**: Current page number.
  - **`pageSize`**: Number of items per page.
  - **`totalElements`**: Total number of users.
- **`filters`**: Array of filters applied (if any).
- **`records`**: Array of user records.
  - **`_id`**: Unique identifier for the user.
  - **`name`**: Name of the user.
  - **`email`**: Email address of the user.
  - **`authUserId`**: Authentication ID of the user.
  - **`role`**: Role of the user (`CANDIDATE`, `RECRUITER`, or `ADMIN`).
  - **`createdAt`**: Timestamp indicating when the user was created.
  - **`updatedAt`**: Timestamp indicating the last time the user information was updated.

### Notes

- Use pagination arguments (`page` and `limit`) to control the size of the response.
- This query returns metadata to help manage large datasets efficiently.

If you need further assistance, feel free to reach out!

