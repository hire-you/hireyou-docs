---
sidebar_position: 10
---

# Create a User

This guide explains how to use the **CreateUser** mutation to create a new user in the system.

## Mutation Description

The **CreateUser** mutation allows you to create a new user, including specifying their name, email, role, and authentication details.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Mutation Name**: `createUser`

### Input Fields

- **name** (string, required): The name of the user.
- **email** (string, required): The email address of the user.
- **auth_user_id** (string, required): The authentication ID for the user.
- **role** (string, required): The role of the user (`CANDIDATE`, `RECRUITER`, or `ADMIN`).

### Example Mutation

Here is an example of how to create a new user:

```graphql
mutation CreateUser($input: CreateUserInput!) {
  createUser(input: $input) {
    _id
    name
    email
    auth_user_id
    role
    created_at
    updated_at
  }
}
```

### Example Variables

```json
{
  "input": {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "auth_user_id": "auth0|abcd1234",
    "role": "CANDIDATE"
  }
}
```

### Example Response

```json
{
  "data": {
    "createUser": {
      "_id": "64c123f4e14d16bc9df67890",
      "name": "John Doe",
      "email": "john.doe@example.com",
      "auth_user_id": "auth0|abcd1234",
      "role": "CANDIDATE",
      "created_at": "2024-11-01T10:00:00.000Z",
      "updated_at": "2024-11-01T10:00:00.000Z"
    }
  }
}
```

### Response Fields

- **`_id`**: Unique identifier for the user.
- **`name`**: Name of the user.
- **`email`**: Email address of the user.
- **`auth_user_id`**: Authentication ID of the user.
- **`role`**: Role of the user (`CANDIDATE`, `RECRUITER`, or `ADMIN`).
- **`created_at`**: Timestamp indicating when the user was created.
- **`updated_at`**: Timestamp indicating the last time the user information was updated.

### Notes

- Ensure all required fields are provided in the mutation.
- The **auth_user_id** must be unique for each user.

If you need further assistance, feel free to reach out!