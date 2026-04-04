# Using Environment Variables in Postman

## Overview

Environment variables allow you to store and reuse values across multiple requests without hardcoding them directly into your API calls. This is especially useful when working with base URLs, API keys, or user credentials that may change between environments such as development, staging, and production.

This task walks you through creating an environment, defining variables, and referencing them inside requests.

---

## Setting Up Environment Variables

1. In the left sidebar, click **Environments** to open the environment management panel.

    ![Postman UI](assets/task2/navigate_to_environment.jpg)

2. Click the **+** icon to create a new environment collection.

    ![Postman UI](assets/task2/create_an_environment.jpg)

3. Enter a descriptive name for your environment (e.g., `Postman Example Env`).

    ![Postman UI](assets/task2/setup_environment.jpg)

4. Add your variables by filling in the **Variable** and **Initial Value** columns. For example:

    | Variable    | Value                        |
    |-------------|------------------------------|
    | `url`       | `https://postman-echo.com`   |
    | `api_key`   | `myAPIKey`                   |
    | `user_name` | `myName`                     |
    | `user_role` | `Developer`                  |

    ![Postman UI](assets/task2/add_variable.jpg)

5. Optionally, assign a tag color to your environment for easier identification when switching between multiple environments.

    ![Postman UI](assets/task2/add_tag.jpg)

With this step completed, your environment is now fully configured.  
You have successfully created an Environment, added variables, and customized its appearance for easier identification.

Next, let’s explore how to use these environment variables inside your requests.


---

## Using Environment Variables in Requests
1. Click the **New** button on the right-hand side of the **My Workspace** top bar.

    ![Postman UI](assets/task2/click_new.jpg)

2. In the dialog that appears, select **HTTP** to create a new HTTP request.

    ![Postman UI](assets/task2/create_request.jpg)

3. In the top-right dropdown, select the environment you created (e.g., `Postman Example Env`). Postman will resolve all `{{variable}}` references using the values defined in that environment.

    ![Postman UI](assets/task2/choose_environment.jpg)

    !!! warning
        If no environment is selected, Postman will not resolve any `{{variable}}` references and the raw placeholder text will be sent in the request instead.

4. In the URL field, enter the following using the `{{variable_name}}` syntax:
```
{{url}}/get
```

    Click **Send**. Postman will substitute `{{url}}` with `https://postman-echo.com` before sending the request. You can confirm the request was sent successfully by the `200 OK` status shown in the response panel.

    ![Postman UI](assets/task2/setup_in_request.jpg)
    !!! warning
        If the variable is not resolved, double-check that the name inside `{{ }}` exactly matches the variable key defined in your environment, including spelling, capitalization, and special characters (e.g., `{{url}}` and `{{Url}}` are treated as different variables).

5. Navigate to the **Headers** tab. Set the **Key** to `x-api-key` and the **Value** to `{{api_key}}`. Click **Send**.

    ![Postman UI](assets/task2/set_header.jpg)

6. In the response panel, locate the `x-api-key` field and confirm it contains the value you defined in your environment variable.

    ![Postman UI](assets/task2/get_header_result.jpg)

    !!! note
        The `{{variable_name}}` syntax works in any field in Postman — URLs, headers, query parameters, and request bodies.

7. Switch the HTTP method to **POST** by clicking the method dropdown on the left of the URL bar and selecting **POST**. Then enter the following in the URL field:
```
{{url}}/post
```

    ![Postman UI](assets/task2/post_request_setup.jpg)

8. In the **Body** tab, click the left dropdown and select **raw**, then click the right dropdown and select **JSON**.

    ![Postman UI](assets/task2/setup_body_json.jpg)

9. Paste the following JSON into the body input field:
```json
{
  "username": "{{user_name}}",
  "role": "{{user_role}}"
}
```

    ![Postman UI](assets/task2/post_request_json.jpg)

10. Click **Send**. In the response panel, locate the `data` field and confirm that the environment variables have been resolved to their corresponding values:
```json
"data": {
    "username": "myName",
    "role": "Developer"
}
```

    ![Postman UI](assets/task2/post_result.jpg)

    !!! success
        Seeing your variable values reflected in the `data` field of the response confirms that Postman is correctly resolving environment variables in the POST request body.
---

## Conclusion

After completing this task, you should be able to:

- **Create and configure an environment** in Postman with custom variable and value pairs
- **Reference environment variables** using the `{{variable_name}}` syntax across URLs, headers, and request bodies

Environment variables are one of the most practical features in Postman. As your projects grow, centralizing configuration in environments will save time and reduce errors when managing multiple APIs or deployment targets.