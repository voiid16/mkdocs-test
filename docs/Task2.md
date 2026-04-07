# Using Environment Variables in Postman

## Overview

Environment variables allow you to store and reuse values across multiple requests without hardcoding them directly into your API calls. This is especially useful when working with base URLs, API keys, or user credentials that may change between environments such as development, staging, and production.

This task walks you through creating an environment, defining variables, and referencing them inside requests.

---

## Setting Up Environment Variables

1. In the left sidebar, click **"Environments"** to open the environment management panel.
![Postman Environment Page](assets/task2/1.png "Open the Environments panel")


2. Click the **"+"** icon to create a new environment collection.

![Create Environment Collection](assets/task2/2.png "Click the plus icon to create a new environment")

3. Enter a descriptive name for your environment (e.g., `Postman Example Env`).

    ![Name the Environment](assets/task2/3.png "Enter a name for the environment")

4. Add your variables by filling in the **"Variable"** and **"Value"** columns. For example:

    | Variable    | Value                        |
    |-------------|------------------------------|
    | `url`       | `https://postman-echo.com`   |
    | `api_key`   | `myAPIKey`                   |
    | `user_name` | `myName`                     |
    | `user_role` | `Developer`                  |

    ![Add Environment Variables](assets/task2/4.png "Add variables and values to the environment")

5. Optionally, assign a tag color to your environment for easier identification when switching between multiple environments.

    ![Environment Tag Color](assets/task2/5.png "Assign a color tag to the environment")

With this step completed, your environment is now fully configured.  
You have successfully created an Environment, added variables, and customized its appearance for easier identification.

Next, let’s explore how to use these environment variables inside your requests.


---

## Using Environment Variables in Requests
1. Click the **"New"** button on the right-hand side of the **"My Workspace"** top bar.

    ![Create New Request](assets/task2/6.png "Click the New button to create a request")

2. In the dialog that appears, select **"HTTP"** to create a new HTTP request.

    ![Select HTTP Request](assets/task2/7.png "Choose HTTP to create a new request")

3. In the top-right dropdown, select the environment you created (e.g., `Postman Example Env`). Postman will resolve all `{{variable}}` references using the values defined in that environment.

    ![Select Environment](assets/task2/8.png "Select the environment for the request")

    !!! warning
        If no environment is selected, Postman will not resolve any `{{variable}}` references and the raw placeholder text will be sent in the request instead.

4. In the URL field, enter the following using the `{{variable_name}}` syntax:
```
{{url}}/get
```

    Click **"Send"**. Postman will substitute `{{url}}` with `https://postman-echo.com` before sending the request. You can confirm the request was sent successfully by the `200 OK` status shown in the response panel.

    ![Send GET Request](assets/task2/9.png "Send a GET request using the environment variable URL")

    !!! warning
        If the variable is not resolved, double-check that the name inside `{{ }}` exactly matches the variable key defined in your environment, including spelling, capitalization, and special characters (e.g., `{{url}}` and `{{Url}}` are treated as different variables).

5. Navigate to the **"Headers"** tab. Set the **"Key"** to `x-api-key` and the **"Value"** to `{{api_key}}`. Click **"Send"**.

    ![Set Header API Key](assets/task2/10.png "Add x-api-key header using environment variable")

6. In the response panel, locate the `x-api-key` field and confirm it contains the value you defined in your environment variable.

    ![Verify API Key Header](assets/task2/11.png "Confirm the API key value in the response")

    !!! note
        The `{{variable_name}}` syntax works in any field in Postman — URLs, headers, query parameters, and request bodies.

7. Switch the HTTP method to **"POST"** by clicking the method dropdown on the left of the URL bar and selecting **"POST"**. Then enter the following in the URL field:
```
{{url}}/post
```

 ![Setup POST Request](assets/task2/12.png "Change method to POST and set the request URL")

8. In the **"Body"** tab, click the left dropdown and select **"raw"**, then click the right dropdown and select **"JSON"**.

    ![Set Body to JSON](assets/task2/13.png "Configure the request body as raw JSON")

9. Paste the following JSON into the body input field:
```json
{
  "username": "{{user_name}}",
  "role": "{{user_role}}"
}
```

    ![POST Request JSON Body](assets/task2/14.png "Insert JSON body using environment variables")

10. Click **"Send"**. In the response panel, locate the `data` field and confirm that the environment variables have been resolved to their corresponding values:
```json
"data": {
    "username": "myName",
    "role": "Developer"
}
```

    ![Verify POST Response Data](assets/task2/15.png "Confirm variables are resolved in the response")

    !!! success
        Seeing your variable values reflected in the `data` field of the response confirms that Postman is correctly resolving environment variables in the POST request body.
---

## Conclusion

After completing this task, you should be able to:

- **Create and configure an environment** in Postman with custom variable and value pairs
- **Reference environment variables** using the `{{variable_name}}` syntax across URLs, headers, and request bodies

Environment variables are one of the most practical features in Postman. As your projects grow, centralizing configuration in environments will save time and reduce errors when managing multiple APIs or deployment targets.