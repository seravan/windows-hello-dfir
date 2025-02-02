# windows-hello-dfir
Documentation for windows hello authentication logs. This documentation is an attempt to answer the challenge from David Cowen: https://www.hecfblog.com/2025/02/daily-blog-737-sunday-funday-2225.html

### What is Windows Hello
Windows Hello is a biometric auhtnetication system from Microsoft that lets users authenticate and login into their devices via facial recognition, fingerprint, PIN. More about windows hello: https://www.microsoft.com/en-us/windows/tips/windows-hello

### Windows Hello Authentication Logs.
In windows, we can view logs related to the biometric service via event viewer.
Location : Applications and Services > Microsoft-Windows-Biometrics/Operational.
Facical Recognition - event id : 1019
Finger print - event id : 1004

The above event IDs only indicates successfull interaction of biometric service with respective sensor. Although these events are recorded when a user logs into a device, the sole presence of these events does not indicate a login. Third party apps can also use Windows Hello API that would record these events. We can compare these events to 4624 Logon events in Windows Logs > Security. This correlation can help us determine if fingerprint / face ID were used for a logon.

Below is an example for login using facial recognition feature. Here the logon type is 7, you can see similar results for other logon types using fingerprint/facial recognition. (I have locked my device and unlocked it Win + L):

<img width="613" alt="image" src="https://github.com/user-attachments/assets/eb4bff1c-1c0f-43be-8b83-944d94db146b" /> <img width="625" alt="image" src="https://github.com/user-attachments/assets/b9aa2349-13f0-4b47-a700-ec2ad5ce3874" />



PIN - event id : 

