# Troubleshooting

| **Problem** | **Likely Cause** | **Solution** |
| --- | --- | --- |
| Variable highlighted in red | Variable is undefined or unchecked. | Open the collection's **Variables** tab and tick the checkbox next to your variable. |
| `{{variable}}` sent as plain text | No environment selected. | Select the correct environment from the top-right dropdown. |
| Variable resolves to the wrong value | Name case does not match. | Confirm `{{variable}}` spelling and capitalization exactly matches the environment key. |
| Query parameters missing from URL | Parameters not added correctly. | Use the **Params** tab to add key-value pairs — Postman builds the URL automatically. |
| `400 Bad Request` | Invalid URL, body, or headers. | Check the URL for typos and confirm **Body** is set to **raw → JSON** with valid JSON. |
| `401 Unauthorized` | API key missing or not resolved. | Add `x-api-key: {{api_key}}` in the **Headers** tab and confirm the variable is defined. |
| `404 Not Found` | Endpoint URL does not exist. | Check the URL path for typos and confirm `{{base_url}}` points to the correct server. |
| Collection Runner request fails | Variables undefined or wrong environment. | Select the correct environment in the runner and tick all variable checkboxes in the **Variables** tab. |
| Import shows a conflict warning | Collection already exists in workspace. | Click **Import as Copy**. |
