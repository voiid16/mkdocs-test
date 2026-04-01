## Troubleshooting

**I see "Could not send request" or a network error**
: Check your internet connection. Make sure the URL is exactly `https://postman-echo.com/get`.

**The response body is empty or nothing appears**
: Make sure you clicked the **Body** tab in the **bottom** (response) panel — not the Body tab in the top (request) panel.

**My parameters are missing from the response `args`**
: Go to the **Params** tab and confirm the checkboxes next to `foo1` and `foo2` are **checked**. Unchecked rows are not sent with the request.

**I see a status code other than 200**
: Hover over the status code in Postman to see what it means. Double-check your URL for any typos.
