# EaseFilter Folder Locker

EaseFilter Folder Locker is a comprehensive Windows file and folder protection solution built on the **EaseFilter File Control, Encryption, and Process Filter Driver SDK**. It provides developers and administrators with the ability to lock, hide, encrypt, and restrict access to sensitive files and folders in real time, preventing unauthorized access, modification, and data exfiltration.

<Image alt="Concept illustration of a folder secured with a padlock" caption="Secure your sensitive files and folders" src="https://www.easefilter.com/images/folderlocker-architecture.jpg"/>

---

## 🚀 Key Capabilities

*   **Lock & Restrict Access:** Prevent unauthorized users or processes from opening, reading, writing, renaming, or deleting files. Enforce access rules selectively by process, user, or application behavior.
*   **Hide Files and Folders:** Completely camouflage sensitive items from Windows Explorer and other applications, protecting them against accidental discovery or deletion.
*   **Granular Control with Filter Rules:** Configure security policies using file names, folder paths, or wildcard patterns. Apply specific read-only, deny-write, or full-access restrictions.
*   **User & Process-Based Exclusions:** Whitelist trusted users or processes to bypass restrictions—perfect for allowing system services to operate while blocking untrusted or unknown applications.
*   **Real-Time Monitoring & Alerts:** Receive instant telemetry and notifications on unauthorized access attempts for robust auditing and compliance tracking.
*   **Secure File Sharing with DRM:** Embed Digital Rights Management (DRM) policies directly into the file header. Share files internally or externally while maintaining control over expiration times and allowed access rights.

---

## 🏗️ Technical Architecture

Folder Locker is built for enterprise-grade security, operating deep within the Windows OS to ensure policies cannot be bypassed by user-mode applications.

<Image alt="Zero Trust Security Architecture diagram showing identity, verification, and access monitoring" caption="Zero Trust Implementation at the Kernel Level" src="image_agent_tag_1249373748123186047"/>

### 1. Kernel-Mode Minifilter Framework
Built on the Windows File System Minifilter driver model, providing maximum stability and compatibility across Windows 7 through Windows 11 and Windows Server. 
*   **I/O Interception:** Intercepts and manages I/O Request Packets (IRPs) for `CreateFile`, `ReadFile`, `WriteFile`, and `SetInformation` before they reach the storage stack.
*   **Process & Context Awareness:** Automatically identifies the Process ID, User SID, and Application Name associated with every file I/O request.

### 2. Zero-Trust Security & Anti-Ransomware
*   **Kernel-Level Default Deny:** Policies remain active even if the user possesses Local Admin rights, preventing malicious privilege escalation.
*   **Anti-Ransomware Logic:** Programmatically block mass-rename or mass-deletion events in real-time before data is compromised.

### 3. Transparent File Encryption (TFE)
*   **On-the-Fly AES-256:** FIPS 140-2 compliant encryption utilizing the Microsoft CNG library with hardware acceleration (AES-NI).
*   **Dual-View Isolation:** Unauthorized processes see only raw ciphertext, while authorized processes seamlessly read decrypted plaintext—requiring zero modifications to your applications.

---

## 🛠️ Usage & Configuration

### 1. Folder Lock Setup
To protect your files, add a target folder to the locker and configure its baseline access rights. You can toggle permissions to allow or deny:
*   File creation, deletion, writing, and reading.
*   File renaming and security attribute modifications.
*   Execution, copying out, network access, and file hiding.

### 2. Granular Access Control
Click **Add User Rights** or **Add Process Rights** to establish specific overrides. For instance, you can deny read access to `Everyone` but grant explicit read/write access to your proprietary application (`myapp.exe`) or a specific IT admin SID.

### 3. Creating Encrypted Share Files (DRM)
Use the embedded Transparent File Encryption to create shareable files with built-in digital rights. 
*   Set an expiration time for the file.
*   Authorize specific users, processes, or computers.
*   Restrict downstream actions (e.g., prevent the file from being copied, edited, or printed).

### 4. File Audit & Access Reports
Track the status of all shared and protected files. Audit logs provide visibility into:
*   Who accessed the file (User/Process).
*   When and from where the file was accessed.
*   Whether the access request was authorized or denied, and the specific rule that triggered the denial.

---
## [A C# Folder Locker Example](https://www.easefilter.com/Forums_Files/FolderLocker.htm)
 
The folder locker example was implemented with the Transparent File Encryption and Control Filter Driver SDK. With the folder locker you can prevent your protected files being read,written,deleted, renamed, copied out of the protected folder, allow you to authorize or deny the file access to specific user or process, also allow you to hide the files or automatically encrypt/decrypt the files on the fly. 

![Folder locker](https://www.easefilter.com/images/folderlocker.png)

## Lock your files with the folder locker settings

To protect your files, first you need to add a protected folder to the locker, then configure the access rights of the folder: to allow or disallow the file deletion, file writing, file execution, file creation, file renaming, security change, file being copied out, file reading, file being accessed from network, hiding the files, file encryption.

![Folder locker setting](https://www.easefilter.com/images/FolderLockerSettings.PNG)

## Control your files by setting access control rights to specific users or processes

To set the access rights to the specific users or processes by clicking "Add User Rights" and "Add Process Rights" buttons: to allow or disallow the file deletion, file writing, file execution, file creation, file renaming, security change, file being copied out, file reading, file being accessed from network, hiding the files, file encryption.

![user access control](https://www.easefilter.com/images/useraccessrights.png)

[Read more about folder locker example](https://www.easefilter.com/Forums_Files/FolderLocker.htm)


## EaseFilter File System Filter Driver SDK Reference
| Product Name | Description |
| --- | --- |
| [Cloud File System SDK](https://www.easefilter.com/cloud/cloud-file-system-sdk.htm) | EaseFilter Cloud File System SDK Introduction. |
| [CloudTier Storage Tiering SDK](https://www.easefilter.com/cloud/storage-tiering-sdk.htm) | EaseFilter Storage Tiering Filter Driver SDK Introduction. |
| [File Monitor SDK](https://www.easefilter.com/kb/file-monitor-filter-driver-sdk.htm) | EaseFilter File Monitor Filter Driver SDK Introduction. |
| [File Control SDK](https://www.easefilter.com/kb/file-control-file-security-sdk.htm) | EaseFilter File Control Filter Driver SDK Introduction. |
| [File Encryption SDK](https://www.easefilter.com/kb/transparent-file-encryption-filter-driver-sdk.htm) | EaseFilter Transparent File Encryption Filter Driver SDK Introduction. |
| [Registry Filter SDK](https://www.easefilter.com/kb/registry-filter-drive-sdk.htm) | EaseFilter Registry Filter Driver SDK Introduction. |
| [Process Filter SDK](https://www.easefilter.com/kb/process-filter-driver-sdk.htm) | EaseFilter Process Filter Driver SDK Introduction. |
| [EaseFilter SDK Programming](https://www.easefilter.com/kb/programming.htm) | EaseFilter Filter Driver SDK Programming. |

## EaseFilter SDK Sample Projects
| Sample Project | Description |
| --- | --- |
| [CloudTier Storage Tiering Demo](https://www.easefilter.com/cloud/cloudtier-storage-tiering-demo.htm) | A HSM File System Filter Driver Demo. |
| [CloudTier S3 Tiering Demo](https://www.easefilter.com/cloud/cloudtier-s3-intelligent-tiering-demo.htm) | CloudTier S3 Intelligent Tiering Demo. |
| [Cloud File DR S3 Demo](https://www.easefilter.com/cloud/cloud-file-dr-demo.htm) | Cloud File DR S3 Demo. |
| [Amazon S3 File Explorer Demo](https://www.easefilter.com/cloud/s3-browser-demo.htm) | Amazon S3 File Explorer Demo. |
| [Auto File DRM Encryption](https://www.easefilter.com/kb/auto-file-drm-encryption-tool.htm) | Auto file encryption with DRM data embedded. |
| [Transparent File Encrypt](https://www.easefilter.com/kb/AutoFileEncryption.htm) | Transparent on access file encryption. |
| [Secure File Sharing with DRM](https://www.easefilter.com/kb/DRM_Secure_File_Sharing.htm) | Secure encrypted file sharing with digital rights management. |
| [File Monitor Example](https://www.easefilter.com/kb/file-monitor-demo.htm) | Monitor file system I/O in real time, tracking file changes. |
| [File Protector Example](https://www.easefilter.com/kb/file-protector-demo.htm) | Prevent sensitive files from being accessed by unauthorized users or processes. |
| [FolderLocker Example](https://www.easefilter.com/kb/FolderLocker.htm) | Lock file automatically in a FolderLocker. |
| [Process Monitor](https://www.easefilter.com/kb/Process-Monitor.htm) | Monitor the process creation and termination, block unauthorized process running. |
| [Registry Monitor](https://www.easefilter.com/kb/RegMon.htm) | Monitor the Registry activities, block the modification of the Registry keys. |
| [Secure Sandbox Example](https://www.easefilter.com/kb/Secure-Sandbox.htm) |A secure sandbox example, block the processes accessing the files out of the box. |
| [FileSystemWatcher Example](https://www.easefilter.com/kb/FileSystemWatcher.htm) | File system watcher, logging the file I/O events. |
| [ZeroTrust Example](https://www.easefilter.com/kb/zero-trust-file-access-control-demo.htm) | Zero trust file access control with encryption feature. |

## Filter Driver Reference

* [Understand MiniFilter Driver](https://www.easefilter.com/kb/understand-minifilter.htm)
* [Understand File I/O](https://www.easefilter.com/kb/File_IO.htm)
* [Understand I/O Request Packets(IRPs)](https://www.easefilter.com/kb/understand-irps.htm)
* [Filter Driver Developer Guide](https://www.easefilter.com/kb/DeveloperGuide.htm)
* [MiniFilter Filter Driver Framework](https://www.easefilter.com/kb/minifilter-framework.htm)
* [Isolation Filter Driver](https://www.easefilter.com/kb/Isolation_Filter_Driver.htm)

## License

This repository contains two distinct licensing categories:

1. **Wrapper/Implementation Code (MIT License):** 
   The source code, scripts, and configuration files provided directly in this repository are licensed under the [MIT License](LICENSE). You are free to modify, distribute, and use this specific integration code.

2. **EaseFilter SDK (Commercial License):**
   This project requires the EaseFilter SDK (including its binaries, filter drivers, and core libraries) to function. The EaseFilter SDK is **proprietary commercial software** and is strictly excluded from the MIT License.   
   To use the EaseFilter SDK for commercial purposes or in a production environment, you must obtain a valid commercial license directly from [EaseFilter](https://www.easefilter.com/license.pdf).


## Support
If you have questions or need help, please contact support@easefilter.com 

[Home](https://www.easefilter.com/) | [Solution](https://www.easefilter.com/solutions.htm) | [Download](https://www.easefilter.com/download.htm) | [Demos](https://www.easefilter.com/online-fileio-test.aspx) | [Blog](https://blog.easefilter.com/) | [Programming](https://www.easefilter.com/kb/programming.htm)
