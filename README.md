# Daakwala — The cold-emailer

Official desktop downloads for Windows and macOS. Daakwala runs locally and opens its dashboard in your browser. No Python or Node installation is required.

## Download

Get the application from [GitHub Releases](https://github.com/siddharthaAgarwal/daakwala-downloads/releases).

| Your computer | Download |
| --- | --- |
| Windows 64-bit | `Daakwala-Windows-x64.zip` |
| Mac with Apple Silicon (M-series) | `Daakwala-macOS-arm64.zip` |
| Mac with Intel processor | `Daakwala-macOS-x86_64.zip` |

The first release is an **unsigned beta**. Windows may show a publisher warning and macOS may prevent opening it. The macOS packages are not Apple-notarized. Do not disable security protections to run the app; if your computer blocks it, wait for a signed release. Successful build checks do not establish publisher trust or guarantee compatibility with every computer.

## Start

1. Extract the complete ZIP. On Windows, keep the `Daakwala` folder intact and open `Daakwala.exe` inside it. On macOS, move `Daakwala.app` to Applications.
2. Read the included license. Open the launcher and click **Start Daakwala**. Keep the launcher open while using the dashboard.
3. Follow [Gmail setup and reconnect](GMAIL_SETUP.md) to create and import your own Desktop OAuth credentials and connect your sending account. Credentials are not included.
4. Add your contacts, upload your own PDF attachment, and replace the sample template. Review a dry run before explicitly confirming a send.

Nothing sends automatically on startup. Default limits are up to 40 per batch, a 30-second gap, and up to 100 successful sends per local day. These limits do not guarantee protection from Gmail restrictions or charges.

Your contacts, template history, settings, and sent history stay in your local data folder: `%LOCALAPPDATA%/Daakwala` on Windows or `~/Library/Application Support/Daakwala` on macOS. Back up that folder with the application stopped. Never share its credentials or tokens.

See [the user guide](USER_GUIDE.txt) for more instructions. Port 8000 must be available.

## Ownership and permissions

Copyright © 2026 Siddhartha Agarwal. Personal, noncommercial use is permitted under the [Daakwala Personal-Use License](LICENSE). Modification, redistribution, resale, or commercial use requires the owner's written permission, subject to the license and applicable law. Third-party components retain their own licenses, included with each application package.

This repository contains release documentation and downloadable applications. The application source is maintained in a separate private repository. GitHub's automatically generated “Source code” archives contain only this public repository's documentation; choose the platform ZIP to run Daakwala.

For problems or permission requests, [open an issue](https://github.com/siddharthaAgarwal/daakwala-downloads/issues). Include your operating system and a description of the problem. Do not post email addresses, contacts, resumes, message contents, credentials, tokens, authorization codes, or unredacted logs.
