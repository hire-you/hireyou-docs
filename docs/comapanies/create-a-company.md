---
sidebar_position: 4
---

# Create a Company

This guide explains how to use the **CreateCompany** mutation to add a new company to the server.

## Mutation Description

The **CreateCompany** mutation allows you to create a new company with details such as the company name, industry, website, location, employers, and stage templates.

### Endpoint

- **GraphQL Endpoint**: `/graphql`
- **Mutation Name**: `createCompany`

### Required Fields

To create a new company, you need to provide the following details:

- **name**: The name of the company.
- **industry**: The industry sector the company belongs to.
- **website**: The company's website URL.

### Optional Fields

- **location**: The physical location of the company.
- **employers**: A list of employers associated with the company. Each employer includes fields:
  - **name**: Employer's name.
  - **email**: Employer's email address.
  - **role**: Employer's role in the company.
  - **phone**: Employer's phone number.

- **stage_templates**: A list of recruitment stages associated with the company. Each stage includes:
  - **name**: Stage name.
  - **description**: Description of the stage.

### Example Mutation

Here is an example of how to create a company:

```graphql
mutation CreateCompany($input: CreateCompanyInput!) {
  createCompany(input: $input) {
    _id
    name
    industry
    website
    location
    employers {
      name
      email
      role
      phone
    }
    stage_templates {
      name
      description
    }
  }
}
```

### Example Variables

```json
{
  "input": {
    "name": "Tech Innovators",
    "industry": "Technology",
    "website": "https://techinnovators.com",
    "location": "New York, NY",
    "employers": [
      {
        "name": "Alice Johnson",
        "email": "alice@techinnovators.com",
        "role": "CTO",
        "phone": "123-456-7890"
      }
    ],
    "stage_templates": [
      {
        "name": "Initial Screening",
        "description": "First stage of the hiring process"
      }
    ]
  }
}
```

### Example Response

```json
{
  "data": {
    "createCompany": {
      "_id": "60d21b4667d0d8992e610c85",
      "name": "Tech Innovators",
      "industry": "Technology",
      "website": "https://techinnovators.com",
      "location": "New York, NY",
      "employers": [
        {
          "name": "Alice Johnson",
          "email": "alice@techinnovators.com",
          "role": "CTO",
          "phone": "123-456-7890"
        }
      ],
      "stage_templates": [
        {
          "name": "Initial Screening",
          "description": "First stage of the hiring process"
        }
      ]
    }
  }
}
```

### Parameters

- **`input`**: Object containing the fields to create a new company.

### Response Fields

- **`_id`**: Unique identifier for the created company.
- **`name`**: Name of the company.
- **`industry`**: Industry sector of the company.
- **`website`**: Company's website URL.
- **`location`** _(optional)_: Location of the company.
- **`employers`**: Array of employers within the company.
  - **`name`**: Name of the employer.
  - **`email`**: Email address of the employer.
  - **`role`**: Role of the employer in the company.
  - **`phone`**: Phone number of the employer.
- **`stage_templates`**: Array of recruitment stages.
  - **`name`**: Name of the recruitment stage.
  - **`description`**: Description of the recruitment stage.

## Notes

- This mutation enables you to easily create and structure a company's data, including its hiring stages and employer details.
- Make sure that all required fields are provided, as missing required fields will result in an error.

Feel free to reach out for further customization or additional fields needed in this mutation.