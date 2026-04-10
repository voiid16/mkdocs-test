# Sending a GET Request

## Overview

In this section, you will send a GET request to the [**Postman Echo**](./glossary.md) API.

This section is organized into three parts:

- **Build the Request** — Create a new request, set the method, enter the URL, and configure the query parameters, body, and headers.
- **Send & Review** — Send the request and read the response.
- **Save the Request** — Save the request to a collection for future use.

By the end of this section, you will know how to send a real HTTP request and understand what the response tells you.

<!-- !!! info "What is a GET request?"
    A GET request asks a server to **send you data**. It is the most common type of HTTP request — like asking a website to show you a page. -->

<!-- !!! info "What is Postman Echo?"
    Postman Echo is a simple API provided by Postman for testing HTTP requests. -->

---

## Build the Request

Building a request involves setting up all the necessary components for an API call, including choosing the method, entering the URL, and configuring the params, body, and headers. This ensures the request is properly prepared before it is sent.

<!-- --- -->

<!-- **Step 1 — Create a New Request** -->

1. Open the **Postman desktop app** and click the **"+"** button at the top of the screen to open a new tab to create a new request.

    ![Click the + button to open a new tab](assets/task1_send_request/step1_newtab.png "Click the + button to open a new tab")

2. Find the **"GET"** on the left side of the URL bar. Confirm it shows **GET**. If not, click the dropdown and select **GET**. By default, Postman sets every new request to **GET**.

    ![Method dropdown showing GET selected](assets/task1_send_request/step2_get.png "Method dropdown showing GET selected")

3. Click the **URL bar** and type the following URL:
    ```
    https://postman-echo.com/get
    ```

4. Click the **"Params"** tab below the URL bar. 

    In the first empty row, enter **Key:** `foo1` and **Value:** `bar1`. 

    In the next row, enter **Key:** `foo2` and **Value:** `bar2`. 

    The URL bar updates automatically to show:

    ```
    https://postman-echo.com/get?foo1=bar1&foo2=bar2
    ```

    ![Params tab with two rows filled in](assets/task1_send_request/step4_params.png "Params tab with two rows filled in")

5. Click the **"Body"** tab below the URL bar. Confirm **"none"** is selected and leave the **request body** as empty.

    <!-- *For GET requests, the body should always be set to none.* -->
    ![Body tab set to none](assets/task1_send_request/step5_bodynone.png "Body tab set to none")

6. Click the **"Headers"** tab below the URL bar. 

    In the first empty row, add:
    
    - **Key:** `Accept`
    - **Value:** `application/json`

    The **Accept** header tells the server what type of response the client expects, and `application/json` means the client wants the response in JSON format.

<!-- *Add the Accept header in the Headers tab. Postman auto-fills suggestions as you type.* -->
![Headers tab with Accept header added](assets/task1_send_request/step6_header.png "Headers tab with Accept header added")


---

## Send & Review

This section involves sending the configured API request to the server and examining the response returned by the server. This includes checking whether the request was successful through the status code, and reviewing the response data to understand what the server returned.

1. Click the **"Send"** button on the right side of the URL bar. 

    Postman sends the request to `https://postman-echo.com/get?foo1=bar1&foo2=bar2`. The response appears in the bottom half of the screen.


2. Check the **status code** after the **Response** panel appears at the bottom of the screen.

    Look at the top of the response panel. You should see: `200 OK`. This means the request worked. The server received your request and sent data back.

3. Click the **Body** tab and you should see JSON data like this:

   ```json
   {
     "args": {
       "foo1": "bar1",
       "foo2": "bar2"
     },
     "headers": {
       "host": "postman-echo.com",
       "accept": "application/json"
     },
     "url": "https://postman-echo.com/get?foo1=bar1&foo2=bar2"
   }
   ```
   ![Response panel appears after clicking Send button](assets/task1_send_request/step8_200OK.png "Response panel appears after clicking Send button")

---

## Save the Request

Saving lets you open and resend the request any time without setting it up again.

1. Click the **"Save"** button at the top right of the request editor.

    ![Save button at the top right of the request tab](assets/task1_send_request/step9_save.png "Save button at the top right of the request tab")

2. Fill in the details in the **SAVE REQUEST** dialog:

    - **Request name:** `GET - Query Params`
    - **Collection:** Click **"New Collection"**, name it `My First Collection`, and click **"Create"**. Or select an existing collection.

3. Click **"Save"**.

![Save Request dialog with name and collection fields](assets/task1_send_request/step9_newcollection.png "Save Request dialog with name and collection fields")
<!-- *Enter a name for the request and choose a collection to save it in.* -->

Your request now appears in the left sidebar under your collection. Click it any time to reload it.

!!! info "What is a Collection?"
    A collection is a folder that holds related requests together.
    You can organize, share, and run all requests in a collection at once.

---

## Conclusion

By the end of this section, you will have successfully learned the following:

- How to create and configure a GET request in Postman.
- How to add query parameters, headers, and check the body.
- How to read and understand the server response.
- How to save a request to a collection.

Congratulations! You sent your first API request!

---
