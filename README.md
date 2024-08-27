Here’s a detailed guide for getting the API key (OAuth2 token) with Postman:

# Coupa API Data Extraction Tool

This repository contains a Python script and Postman collection that allows you to extract data from the Coupa API.

## Step 1: Get the API Key (OAuth2 Token) with Postman

### Prerequisites:

1. **Postman**: Ensure that you have Postman installed on your system. You can download it from [Postman Downloads](https://www.postman.com/downloads/).
   
    - OS instruccion when OS is provided.

2. **Coupa OAuth2 Credentials**: You will need:
    - `client_id`
    - `client_secret`
    - `scope`
    - `token_url` (which will be in the format `https://customer-name.coupahost.com/oauth2/token`)

### Steps:

1. **Open Postman**: Launch Postman on your system.

2. **Import the Coupa Postman Collection**:
    - Download the Postman collection provided in this repository (or as per the Coupa documentation).
    - In Postman, click on the "Import" button in the top left corner.
    - Select the collection file (JSON or XML based on your setup) and click "Import".

3. **Set Up an Environment in Postman**:
    - In the Postman app, click on the "Environments" tab.
    - Click "New" and select "Environment".
    - Enter the following variables with their corresponding values:

| Variable        | Value                                      |
|-----------------|--------------------------------------------|
| `URL`           | `https://customer-name.coupahost.com/api`  |
| `token_url`     | `https://customer-name.coupahost.com/oauth2/token` |
| `client_id`     | Your OAuth client ID                       |
| `client_secret` | Your OAuth client secret                   |
| `scope`         | Your OAuth scope                           |

Save the environment with a meaningful name, like `Coupa API Environment`.

4. **Request the OAuth2 Token**:
    - Select the appropriate environment you just created from the environment dropdown.
    - In the Postman collection, find the token request.
    - Ensure the correct `client_id`, `client_secret`, `token_url`, and `scope` are populated by referencing the environment variables you set.
    - Click on the "Send" button to make the request. If successful, you will receive an OAuth2 token in the response.

5. **Save the Token**:
    - Once you receive the token, copy it.
    - You will use this token in the Authorization header for all subsequent API requests to authenticate your calls.

### Example Request for Token:

Here’s an example of how your request for the token should look in Postman:

- **Method**: `POST`
- **URL**: `{{token_url}}`
- **Body (form-data)**:
  - `grant_type`: `client_credentials`
  - `client_id`: `{{client_id}}`
  - `client_secret`: `{{client_secret}}`
  - `scope`: `{{scope}}`

### Using the Token for API Requests:

Once you have the token, you will include it in the headers of your API requests to authenticate them. In Postman, this is how you do it:

- For each API request, go to the **Authorization** tab.
- Select **Bearer Token**.
- Paste the token you received into the token field.

Now you're ready to make authenticated API requests to Coupa.

## Next Steps:

Proceed to extract data from Coupa API endpoints, such as PO lines, requisition lines, and headers. Continue to the next section in this guide to run the Python script for extracting and saving the data.
```

### Explanation:
- The steps detail how to use Postman to authenticate with the Coupa API and retrieve an OAuth2 token.
- It includes the necessary environment setup and API request configuration in Postman.
- Once the token is retrieved, you can use it for subsequent API calls by setting it as the bearer token.
