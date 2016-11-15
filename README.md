# facebook-graph-api
Obtaining a permanent **access token** for a Facebook Page

Obtaining an **access token** for a Facebook Page can be a bit tricky so I've decided to compile my own steps on obtaining an **access token**.


Steps in Obtaining Permanent Access Token:

Step 1:
    Create your own app in https://www.developers.facebook.com/

Step 2:
    Open Graph Explorer https://developers.facebook.com/tools/explorer/

Step 3:
    On Application dropdown, select the application you've created.

Step 4:
    Click Get Token > Get User Token, on "permissions" pop up
    check manage_pages and publish_pages in "Events, Groups & Pages"
    section. Click Get Access Token.

Step 5:
    Click "Get Token" and click the page you desire at "Page Access Tokens"
    * It will generate a new token. *

Step 6:
    Click the information icon at the beginning of the access_token input
    field then click "Open in Access Token Tool"

Step 7:
    On "Access Token Page" (new tab). Click on "Extend Access Token"
    button. (Then enter password.) (This will generate a "long-lived access token.")

Step 8:
    Open a terminal and run this curl command. (Use the long-lived token)

    ```bash
    curl "https://graph.facebook.com/me/accounts?access_token={token}"
    ```

    In case it returns this error.
    ```json
        {
            "error": {
                "message": "(#100) Tried accessing nonexisting field
                    (accounts) on node type (Page)",
                "type": "OAuthException",
                "code": 100,
                "fbtrace_id": "xxxxxxxx"
            }
        }
        ```
        
    Go back to "Access Token Debugger" page enter your long-lived token in the field and click debug.
    Copy the User ID (numbers only) and change me to User ID.

    Run this command in terminal:
    ```bash
        curl "https://graph.facebook.com/{user_id}/accounts?access_token={token}"
    ```

Step 9:
    On the response of the curl, find the access token value.
    Go to "Access Token Page" and enter the access token in input field, then click Debug.

    On Expires row it should say "Never".
