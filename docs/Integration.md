# API Manager Integration Documentation

This documentation provides guidance on integrating the API Manager API into your application for managing APIs with authentication.

## API Base URL

The base URL for accessing the API Manager API endpoints is:

```
https://api.apimanagement.com/v1
```

## Authentication

The API Manager API requires authentication using API keys. Each request must include an API key in the headers for authentication.

## Endpoints

### 1. List APIs

Endpoint to retrieve a list of all APIs managed by the system.

- **URL:** `/apis`
- **Method:** GET
- **Headers:** `Authorization: ApiKey <API_KEY>`
- **Response:** Array of API objects including ID, name, description, base URL, and other details.

### 2. Get API Details

Endpoint to retrieve details of a specific API by its ID.

- **URL:** `/apis/{id}`
- **Method:** GET
- **Headers:** `Authorization: ApiKey <API_KEY>`
- **Parameters:** `{id}` - ID of the API.
- **Response:** API object containing details such as name, description, base URL, authentication type, and access control settings.

### 3. Add API

Endpoint to add a new API to the system.

- **URL:** `/apis`
- **Method:** POST
- **Headers:** `Authorization: ApiKey <API_KEY>`
- **Request Body:** JSON object containing API details such as name, description, base URL, authentication type, and access control settings.
- **Response:** ID of the newly added API and success message.

### 4. Update API

Endpoint to update details of an existing API by its ID.

- **URL:** `/apis/{id}`
- **Method:** PUT
- **Headers:** `Authorization: ApiKey <API_KEY>`
- **Parameters:** `{id}` - ID of the API.
- **Request Body:** JSON object containing updated API details (name, description, base URL, etc.).
- **Response:** Success message indicating that the API details have been updated.

### 5. Delete API

Endpoint to delete an API from the system by its ID.

- **URL:** `/apis/{id}`
- **Method:** DELETE
- **Headers:** `Authorization: ApiKey <API_KEY>`
- **Parameters:** `{id}` - ID of the API.
- **Response:** Success message indicating that the API has been deleted.

## Error Handling

The API Manager API returns appropriate HTTP status codes along with error messages in case of errors. Handle these errors in your application accordingly.

## Example Usage

Below is an example of how to use the API Manager API with Python's requests library:

```python
import requests

# API Manager API base URL
base_url = 'https://api.apimanagement.com/v1'
# Replace '<API_KEY>' with your actual API key
api_key = '<API_KEY>'

# Function to list all APIs
def list_apis():
    url = f'{base_url}/apis'
    headers = {'Authorization': f'ApiKey {api_key}'}
    response = requests.get(url, headers=headers)
    if response.status_code == 200:
        return response.json()
    else:
        return f'Error: {response.status_code} - {response.text}'

# Example usage
apis = list_apis()
print('List of APIs:', apis)
```

## Conclusion

This documentation provides the necessary information to integrate the API Manager API into your application for managing APIs with authentication. Follow the guidelines and examples provided to effectively manage APIs in your system.
