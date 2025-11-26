# Question 1) What is the file that gave access to the attacker?

I attempted to use `jq` for filtering.

![alt text](image.png)

The question is "the file that gave access to the attacker," so I narrowed it down using EventID = 1 (process creation) and CommandLine (executable path and arguments).

After scrolling through the events, I found this suspicious one:

![alt text](image-1.png)

The long command includes the flags -nop (no profile), -w hidden (WindowStyle hidden), and -e (EncodedCommand).

![alt text](image-2.png)

Looking at `"ParentCommandLine": "\"C:\\Windows\\SysWOW64\\mshta.exe\" \"C:\\Users\\IEUser\\Downloads\\updater.hta\" {1E460BD7-F1C3-4B2E-88BF-4E770A288AF5}{1E460BD7-F1C3-4B2E-88BF-4E770A288AF5} ",`

The user downloaded `updater.hta` into the Downloads folder and clicked on it. However, this file was not executed directly but was interpreted by `mshta.exe`. `mshta.exe` read the PowerShell command inside and executed it.

Answer: updater.hta

# Question 2) What is the powershell cmdlet used to download the malware file and what is the port?

Since the question asks for the cmdlet used to download, I narrowed it down using this filter:

![alt text](image-3.png)

EventID = 3 (TCP/UDP connection), image = powershell

The output includes 2 events:

![alt text](image-4.png)

![alt text](image-5.png)

Applied additional filters:

![alt text](image-6.png)

Answer: Invoke-WebRequest, 6969