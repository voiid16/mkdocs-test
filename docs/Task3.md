# Grouping Requests with Collections

## Overview

In this section, you will organize API requests using **Collections** — one of Postman's most powerful features for managing and running groups of related requests.

This section is organized into four parts:

- **Set Up** — Create a Collection, add a Folder, and configure a shared environment variable and headers (Steps 1–3).
- **Build the Requests** — Add GET, POST, PUT, and DELETE requests that cover a full CRUD workflow (Steps 1–4).
- **Run the Collection** — Use the Collection Runner to execute all requests at once.
- **Review the Results** — Read the runner output to verify everything worked.

By the end of this section, you will know how to organize related requests into a collection, share configuration across requests, and run a full CRUD test with one click.

!!! info "What is CRUD?"
    CRUD stands for **Create, Read, Update, Delete** — the four basic operations you perform on data with an API.

    | Operation | HTTP Method | What it does |
    |-----------|-------------|--------------|
    | **Create** | POST | Add new data |
    | **Read** | GET | Retrieve data |
    | **Update** | PUT | Replace existing data |
    | **Delete** | DELETE | Remove data |

!!! info "What is a Collection?"
    A Collection is a folder that holds related requests together. You can share configuration — like headers and variables — across every request in the collection, and run them all at once.

---

## Set Up

This section covers Steps 1–3: creating the Collection and Folder, setting the base URL variable, and adding a shared header.

---

**Step 1 — Create a New Collection**

1. In the left sidebar, find the **COLLECTIONS** section — it is visible by default near the top of the sidebar.
2. Click the **+** icon at the top of the sidebar (next to the filter icon and `...`).
3. Select **Collection** from the menu that appears.
4. A new collection appears under **COLLECTIONS** with its name highlighted and ready to edit.
5. Type `Grouping Requests` and press **Enter**.

![New Collection created in the sidebar under COLLECTIONS](assets/task3/newcollection.png "New Collection created in the sidebar under COLLECTIONS")

<!-- !!! info
    You can also hover over the **COLLECTIONS** heading — a **+** icon appears beside it. Click it to add a new collection directly. -->

---

**Step 2 — Add a Folder Inside the Collection**

Folders let you group requests by feature or resource type within the same collection.

1. Right-click the `Grouping Requests` collection in the sidebar.
2. Select **Add Folder**.
3. Name the folder `Users`.
4. Press **Enter** to confirm.

![Add Folder menu option and the new Users folder](assets/task3/newfolder.png "Add Folder menu option and the new Users folder")

!!! info
    Use folders to separate different resources or features — for example, a `Users` folder and an `Orders` folder inside the same collection.

---

**Step 3 — Set Up Environment Variables and Shared Headers**

Instead of typing the full URL into every request, you will store the base URL in a **variable**. You will also set a shared header that applies to every request in the collection.

**Part A — Create an Environment with `base_url`**

1. In the left sidebar, scroll down to find the **ENVIRONMENTS** section at the bottom.
2. Click the **+** icon that appears when you hover over the **ENVIRONMENTS** heading.
3. A new environment tab opens in the main area. Name it `Demo Environment` at the top of the editor.
4. In the variable table, add a row:
   - **Variable:** `base_url`
   - **Value:** `https://postman-echo.com`
5. Click **Save** (or press ++cmd+s++).
6. The environment now appears in the **ENVIRONMENTS** section with a **✓** checkmark, meaning it is active. If it does not show a checkmark, click the **⊙** icon to the right of its name to activate it.

![Environment editor showing base_url variable, with Demo Environment active in the sidebar](assets/task3/addvaluetoenv.png "Environment editor showing base_url variable, with Demo Environment active in the sidebar")

!!! info "What is `{{base_url}}`?"
    When you type `{{base_url}}` in a URL field, Postman replaces it with the value you saved in the environment. If the base URL ever changes, you only need to update it in one place.

**Part B — Add a Shared Header to the Collection**

In Postman v12, collection-level headers are set using a **pre-request script** in the collection's **Scripts** tab. The script runs automatically before every request in the collection.

1. Click the `Grouping Requests` collection name in the sidebar to open it.
2. Click the **Scripts** tab (in the tab row below the collection name).
3. Click **Pre-request** inside the Scripts tab.
4. Type the following script into the editor:

   ```javascript
   pm.request.headers.upsert({
       key: "Content-Type",
       value: "application/json"
   });
   ```

5. Click **Save** (or press ++ctrl+s++ / ++cmd+s++).

![Collection Scripts tab with pre-request script setting Content-Type header](assets/task3/prerequest.png "Collection Scripts tab with pre-request script setting Content-Type header")

<!-- !!! info "What does `upsert` mean?"
    `upsert` means **update if it exists, insert if it doesn't**. Using `upsert` is safer than `add` because it won't throw an error if the header is already present on an individual request. -->

!!! info
    This script runs automatically before **every request** in the collection. You will not need to manually add `Content-Type: application/json` to each request.

---

## Build the Requests

This section covers Steps 1–4: adding a GET, POST, PUT, and DELETE request inside the `Users` folder.

---

**Step 1 — Add a GET Request (Read)**

A GET request retrieves data from the server.

1. Right-click the `Users` folder in the sidebar.
2. Select **Add Request**.
3. Name it `GET - Read Users`.
4. Set the method to **GET**.
5. Enter the URL:
   ```
   {{base_url}}/get
   ```
6. Click the **Params** tab and add:
    - **Key:** `foo1` — **Value:** `bar1`
7. Click **Save**.

![GET request with base_url in the URL field and query params added](assets/task3/get.png "GET request with base_url in the URL field and query params added")

!!! info
    Using `{{base_url}}` instead of the full URL means all your requests stay consistent. If the server address changes, update it in the environment — not in every request.

---

**Step 2 — Add a POST Request (Create)**

A POST request sends new data to the server.

1. Right-click the `Users` folder and select **Add Request**.
2. Name it `POST - Create User`.
3. Set the method to **POST**.
4. Enter the URL:
   ```
   {{base_url}}/post
   ```
5. Click the **Body** tab.
6. Select **raw** and choose **JSON** from the format dropdown on the right.
7. Enter the following JSON body:
   ```json
   {
     "name": "Alice",
     "email": "alice@example.com"
   }
   ```
8. Click **Save**.

![POST request with raw JSON body entered](assets/task3/post.png "POST request with raw JSON body entered")

!!! info
    The **Body** tab is where you send data with POST, PUT, and PATCH requests. The `Content-Type: application/json` header you set on the collection automatically tells the server the body is JSON.

---

**Step 3 — Add a PUT Request (Update)**

A PUT request replaces existing data on the server.

1. Right-click the `Users` folder and select **Add Request**.
2. Name it `PUT - Update User`.
3. Set the method to **PUT**.
4. Enter the URL:
   ```
   {{base_url}}/put
   ```
5. Click the **Body** tab, select **raw**, and choose **JSON**.
6. Enter the following body:
   ```json
   {
     "name": "Alice Updated",
     "email": "alice_updated@example.com"
   }
   ```
7. Click **Save**.

![PUT request with updated JSON body](assets/task3/put.png "PUT request with updated JSON body")

!!! info "PUT vs PATCH"
    **PUT** replaces the entire resource with the new data you send.
    **PATCH** updates only the specific fields you include.
    Use PUT when you want to fully overwrite a record.

---

**Step 4 — Add a DELETE Request (Delete)**

A DELETE request removes data from the server.

1. Right-click the `Users` folder and select **Add Request**.
2. Name it `DELETE - Delete User`.
3. Set the method to **DELETE**.
4. Enter the URL:
   ```
   {{base_url}}/delete
   ```
5. Leave the **Body** as **none**.
6. Click **Save**.

![DELETE request with base_url URL and no body](assets/task3/delete.png "DELETE request with base_url URL and no body")

!!! info
    DELETE requests typically do not include a body — the URL identifies the resource to remove. Some APIs use a path parameter (for example, `/users/123`) to specify which record to delete.

---

## Run the Collection

**Step 1 — Run the Collection with Collection Runner**

The Collection Runner sends all your requests in sequence and records the result for each one.

1. Right-click the `Grouping Requests` collection in the sidebar.
2. Select **Run collection**.
3. A run configuration tab opens in the main area. Review the settings:
    - **Environment:** Confirm `Demo Environment` is shown.
    - **Iterations:** Leave as `1` (runs each request once).
    - **Delay:** Leave as `0` ms, or enter `200` ms if you want a short pause between requests.
    - **Sequence:** Confirm the requests are listed in this order:
        1. `GET - Read Users`
        2. `POST - Create User`
        3. `PUT - Update User`
        4. `DELETE - Delete User`
4. Click the **Run** button to start.

![Collection run configuration tab before clicking Run](assets/task3/runconfig.png "Collection run configuration tab before clicking Run")
<!-- 
!!! info
    You can drag requests in the run list to reorder them for this run only. This does not affect their order in the collection. -->

---

## Review the Results

**Step 1 — Read the Run Results**

When the run finishes, Postman opens a **Run results** tab automatically. The page title shows **"[Collection name] - Run results"**.

At the top, a summary bar shows:

| Field | What it means |
|-------|--------------|
| **Source** | How the run was triggered — shows `Runner` |
| **Environment** | The environment used — should show `Demo Environment` |
| **Iterations** | How many times the requests ran — should show `1` |
| **Duration** | Total time for the run |
| **All tests** | Number of test assertions that ran |
| **Errors** | Number of requests that failed to send |

<!-- Below the summary, each request is listed under **Iteration 1**:

```
GET    Users > GET - Read Users      https://postman-echo.com/get?foo1=bar1    200  128ms
POST   Users > POST - Create User    https://postman-echo.com/post             200   86ms
PUT    Users > PUT - Update User     https://postman-echo.com/put              200   87ms
DELETE Users > DELETE - Delete User  https://postman-echo.com/delete           200   83ms
``` -->

Below the summary, each request is listed. Each row shows the method, folder path, request name, URL sent, **status code**, response time, and response size.

![Run results tab showing all four requests with 200 status codes](assets/task3/runresults.png "Run results tab showing all four requests with 200 status codes")

!!! info "What do the status codes mean?"

    | Code | Meaning |
    |------|---------|
    | **200** (green) | The request worked — the server responded successfully |
    | **4xx** (red) | Something is wrong with your request — check the URL, body, or headers |
    | **5xx** (red) | The server encountered an error |

<!-- !!! info "Why does it say 'No tests found'?"
    Each request shows **No tests found** because we have not written any test scripts yet. This is expected. The requests still ran and returned `200`, which means the CRUD workflow is working correctly. -->

!!! info
    To re-run, click **New Run** in the top-right corner of the results tab. To view past runs, click **View all runs**.

---

## Conclusion

By the end of this section, you will have successfully learned the following:

- How to create a Collection and organize requests inside a Folder.
- How to use `{{base_url}}` to manage the server address in one place.
- How to set shared headers at the collection level.
- How to build GET, POST, PUT, and DELETE requests that cover a full CRUD workflow.
- How to use the Collection Runner to execute and verify all requests at once.

Congratulations! You have built and run your first complete CRUD API workflow in Postman.

---
