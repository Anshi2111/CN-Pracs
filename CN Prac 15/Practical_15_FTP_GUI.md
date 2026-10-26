# Practical 15: Perform File Transfer and Access Using FTP

## Aim
To configure an FTP server and perform file upload and download using an FTP client.

## Software Requirements
- Windows operating system
- FileZilla Server
- FileZilla Client

## Procedure
1. Download and install FileZilla Server from the official website.
2. Open the FileZilla Server Administration Interface and connect to the local server at `127.0.0.1` using the administration port configured during installation.
3. Create an FTP user named `ftpstudent` and configure a password.
4. Create a folder named `C:\FTPSHARE` to store transferred files.
5. Under the user's mount points, set the virtual path to `/` and the native path to `C:\FTPSHARE`. Grant Read + Write access and enable the user.
6. Open FileZilla Client.
7. Enter the connection details:
   - Host: `127.0.0.1`
   - Username: `ftpstudent`
   - Password: the FTP user's password
   - Port: `21`
8. Connect to the server. When prompted about the server's self-signed certificate, verify it matches the certificate shown in the local FileZilla Server settings before trusting it for this local test.
9. In FileZilla Client, locate a test file in the Local site panel.
10. Upload the file by dragging it to the Remote site panel.
11. Verify the upload in the Successful transfers tab and check the server folder `C:\FTPSHARE`.
12. To test downloading, select the uploaded file in the Remote site panel and choose Download.

## Observations
- FTP server connection: Successful
- FTP user authentication: Successful
- File upload: Successful
- File download: Record as successful only after verifying the download.

## Result
The FTP server was configured locally using FileZilla Server, and FileZilla Client connected successfully. File upload was completed successfully. Download should be marked successful only after it is tested.

## Issues Faced
1. The Windows built-in FTP client returned `503 Use AUTH first` because the server required explicit FTP over TLS.
2. An initial login attempt failed with `530 Login incorrect`; the FTP user credentials were then corrected.
3. The sponsored FileZilla Client installer was blocked by Windows as potentially unwanted software. The client was subsequently opened and used successfully.
4. The server used a self-signed TLS certificate, which required verification before trusting it for the local connection.

## Precaution
Use only trusted networks and folders. Do not expose the FTP server to the internet for this exercise. Traditional FTP is unencrypted; use FTP over TLS where available.
