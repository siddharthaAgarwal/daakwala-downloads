# Gmail setup and reconnect

The same instructions are available inside Settings → Set up Gmail. This release
requires each user to supply their own Google Cloud Desktop OAuth client. Creating
a credentials file alone does not authorize access to an account.

## First-time setup

1. Open [Google Cloud Console](https://console.cloud.google.com/) and create/select a project.
2. Under APIs & Services → Library, enable Gmail API.
3. Under Google Auth platform → Branding, enter an app name, support email, and developer contact.
4. Under Audience, choose External for personal Gmail. In Testing, add your sending
   Gmail account under Test users. Recipient contacts do not belong in that list.
5. Under Data Access, add only `https://www.googleapis.com/auth/gmail.send`.
6. Under Clients, create a Desktop app OAuth client and download its JSON.
7. In Daakwala Settings, use Import OAuth JSON and select that file. Alternatively,
   use Import Gmail credentials in the desktop launcher before starting the dashboard.
8. Click Connect Gmail, choose the sending account in Google, review the send-email
   permission, and approve it if it matches your intent. Return to Daakwala.
9. Once authorization is ready, add contacts, upload a PDF, replace the sample email,
   dry run, review the actual recipients/content, and explicitly confirm a batch.

No password or app password is required. No email is sent during import/connect.
The example JSON is not usable credentials. Do not import a token, Web client,
or service-account file. Do not enable billing or request quota increases for setup.
Work accounts may require administrator approval. Google may change menu labels;
consult the [official setup guide](https://developers.google.com/workspace/gmail/api/quickstart/python).

## Reconnect / choose account

Stop active sending and wait for it to settle. Click Reconnect / choose account
and confirm the fresh consent flow. This opens account selection even when an old
token is still usable. Approve only the intended sender. The prior token is replaced
only after successful consent; contacts, template versions, and sent history remain.
History is shared across sender changes in this single-account app, so previously
sent addresses remain excluded even when you select a different sender.

Reconnect when access is revoked/expired, you changed your OAuth client, or you
want to choose the account again. External OAuth apps in Testing generally have
seven-day refresh-token expiry with Gmail send access. See
[Google token expiration](https://developers.google.com/identity/protocols/oauth2#expiration).
Check connection reuses/refreshes valid local authorization and need not open a
browser. Neither operation establishes message delivery or resets Gmail limits.

## Where files go

Settings shows the actual private data directory. Packaged Windows uses
`%LOCALAPPDATA%/Daakwala`; macOS uses `~/Library/Application Support/Daakwala`.
Source launches use the project folder unless DAAKWALA_DATA_DIR is set. The imported
client is saved as credentials.json and authorization creates token.json locally.
Do not share, commit, or include these files in distributed downloads.

## Errors and next steps

| Problem | Next step |
| --- | --- |
| Missing credentials | Import the actual downloaded Desktop OAuth client JSON. |
| Access denied / test-user restriction | Add the sender to Audience → Test users in the same project, or consult your administrator. |
| Invalid grant / revoked token | Reconnect and complete consent with the intended sender. |
| Redirect mismatch | Replace a Web client with a Desktop client and reconnect. |
| No browser / timeout | Check internet/default browser, close stale consent windows, retry within the 60-second consent timeout. |
| Security warning / app blocked | Stop and verify the project, account, and scope using Google guidance. Do not disable protections or bypass blocks. |
| Restriction / quota error during send | Stop and inspect the account/error guidance; reconnecting does not reset limits. |

Never copy authorization URLs, codes, credentials, or tokens into support requests.
Connected means local authorization is ready; Gmail can still reject subsequent
requests. The app does not read inbox or delivery status.
