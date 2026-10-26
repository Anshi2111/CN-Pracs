# Practical 15: Perform File Transfer and Access Using FTP

## Aim
To configure an FTP server and perform file upload and download using an FTP client.

## Software Requirements
- Windows operating system
- FileZilla Server
- FileZilla Client

## Procedure

1. Download and install FileZilla Server.
2. Connect to the local server using `127.0.0.1` and the configured administration port.
3. Create an FTP user named `ftpstudent` and set a password.
4. Create a folder named `C:\FTPSHARE`.
5. Configure the user's mount point with virtual path `/` and native path `C:\FTPSHARE`. Enable Read + Write access.
6. Open FileZilla Client and enter:
   - Host: `127.0.0.1`
   - Username: `ftpstudent`
   - Password: The FTP user's password
   - Port: `21`
7. Connect to the server. Verify the server certificate before trusting it.
8. Select a test file in the Local site panel.
9. Drag the file to the Remote site panel to upload it.
10. Verify the file appears in the remote folder and the Successful transfers tab.
11. To download, right-click the remote file and select **Download**.
12. Verify the downloaded file exists in the local folder.

## Alternative Method: Windows Command Prompt

If a compatible FTP server is available, open Command Prompt and connect:

```cmd
ftp <server-ip>
```

For a server running on the same computer:

```cmd
ftp 127.0.0.1
```

After successful login, use:

```text
dir
pwd
put test.txt
get test.txt
bye
```

- `dir` — Lists remote files.
- `pwd` — Displays the remote directory.
- `put test.txt` — Uploads a file.
- `get test.txt` — Downloads a file.
- `bye` — Disconnects.

**Note:** The built-in Windows FTP client failed with this setup because the server required explicit FTP over TLS. FileZilla Client was used successfully instead. Do not report the terminal method as successful.

## Observations
- FTP server connection: Successful.
- FTP user authentication: Successful after correcting the credentials.
- File upload: Successful.
- File download: Verify before marking successful.

## Issues Faced
1. The Windows FTP client displayed `503 Use AUTH first` because the server required FTP over TLS.
2. An initial login attempt failed with `530 Login incorrect`; the credentials were corrected.
3. Windows blocked an initial sponsored installer as potentially unwanted software.
4. The server used a self-signed TLS certificate that required verification.

## Precautions
- Use only trusted networks and authorized folders.
- Do not expose the FTP server to the internet for this exercise.
- Traditional FTP is unencrypted; use FTP over TLS where available.

## Result
The local FTP server was configured using FileZilla Server, and FileZilla Client connected successfully. File upload was completed successfully. Record download as successful only after verification.
