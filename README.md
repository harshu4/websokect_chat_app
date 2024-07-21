# WebSocket-Based SCCS Chatroom Application

**Group 1 
    - Zhihao Cheng 
    - Shahzeb
    - Sabrina Afrine Sathi
    - Zhisong Chen**

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Protocol Stack](#protocol-stack) 
4. [Project Structure](#project-structure)
5. [App Architecture](#app-architecture)
5. [Installation Instructions](#installation-instructions)
6. [Usage Guide](#usage-guide)
7. [Configuration](#configuration)
8. [WebSocket Protocol Details](#websocket-protocol-details)
10. [Security Considerations](#security-considerations)
11. [Performance Optimization Techniques](#performance-optimization-techniques)
15. [Acknowledgments](#acknowledgments)

## Introduction

This project is a WebSocket-based overlay chat application ([github repo](<https://github.com/Shahzeb892/Chat_App_WebSocket.git>)) utilizing customized protocol, inspired from XMPP, for real-time messaging for inter and intra groups communication. This application has a server implemented in Node.js and a client application built with Electron and Vue.js, designed to offer end-toend encrypted and efficient communication in both group and private chat with user-friendliy UI. Morver, The application aims to provide a seamless and responsive user experience across different platforms including Windows, macOS, and Linux.

## Features
The chat application has following features:

- Real-time messaging using WebSockets
- User authentication and authorization
- Public and private chat rooms
- End-to-end message encryption and security
- Storage with SQLite database
- User-friendly interface with Electron and Vue.js
- Supports multiple user sessions
- Cross-platform support (Windows, macOS, Linux)

## Technologies Used

1. **Node.js:** JavaScript runtime for server-side operations. Chosen for its efficient, event-driven architecture, ideal for real-time applications requiring high performance and scalability.

2. **WebSocket:** Full-duplex communication protocol over a single TCP connection enabling real-time, bi-directional data exchange between server and client with low latency.

3. **Custom Protocols:** Tailored messaging and presence protocols defined in `util/protocol.js` file and are used for managing the communication between the server and clients.

4. **SQLite:** Lightweight, disk-based database for storing user data and chat logs. Selected for its simplicity, reliability and ease of Node.js integration.

5. **Electron:** Framework for developing cross-platform desktop applications with JavaScript, HTML, and CSS using web technologies, combining Chromium and Node.js into a single runtime,.

6. **Vue.js:** Progressive JavaScript framework for building the responsive user interfaces, used to create the front-end due to its simplicity and reactive data-binding capabilitie.

7. **NPM:** Node Package Manager for efficient handling of project dependencies, facilitating easy installation and management of third-party libraries.

## Protocol Stack
Below is the protocol stack used in the Chat application:

![Protocol Stack](<Readme_Images/Protocol Stack.png>)


## Project Structure

📂 **XMPPChatroom-main/**  
├── 📁 **JsServer/**                *Server-side code*  
│   ├── 📁 **client/**              *Client service logic*  
│   ├── 📁 **database/**            *Database scripts and files*  
│   ├── 📁 **server/**              *Server service logic*  
│   ├── 📁 **task/**                *Task queue management*  
│   ├── 📁 **util/**                *Utility functions*  
│   ├── 📁 **test/**                *Test scripts*  
│   ├── 📄 **configuration.json**   *Server configuration*  
│   ├── 📄 **index.js**             *Entry point for the server*  
│   ├── 📄 **package.json**         *NPM dependencies and scripts*  
│   └── 📄 **package-lock.json**    *Lock file for NPM dependencies*  
└── 📁 **SCCSChatRoom/**            *Client-side code*  
    ├── 📁 **build/**               *Build resources*  
    ├── 📁 **resources/**           *Static resources*  
    └── 📁 **src/**                 *Source code*  
        ├── 📁 **main/**            *Main process*  
        ├── 📁 **preload/**         *Preload scripts*  
        └── 📁 **renderer/**        *Renderer process (Vue.js application)*  

## App Architecture

The follow diagrams explains the workflow of client and server code with functions and attribute details in each script/file.

![Client Side Code](<Readme_Images/Client End.png>)

![Server Side Code](<Readme_Images/Server End.png>)
 
## Installation Instructions

### Prerequisites

1. Install Node.js v14.x or later (NPM v6.x or later)

#### Installing Node.js / NPM On Windows:

   ```bash
   install nodejs from https://nodejs.org/en/download/package-manager
   ```
   If there is a start error then run the following commad to install the npm CLI globally.

   ```bash
   npm install -g npm
   ```
   Verify the installation by opening a command prompt or PowerShell and running:

   ```bash
   node -v
   npm -v
   ```
#### Installing Node.js / NPM On Mac:

   ```bash
   brew install node
   ```
   Verify the installation by checking the versions of Node.js and npm.

   ```bash
   node --version
   npm --version
   ```
### Installation Steps

2. **Clone Github Repo**
   ```bash
   git clone https://github.com/Shahzeb892/websokect_chat_app.git
   cd websocket_chat_app
   ```

2. **Install server dependencies:**

   ```bash
   cd JsServer
   npm install
   ```

3. **Install client dependencies:**

   ```bash
   cd ../SCCSChatRoom
   npm install
   ```

## App Usage Guide

### Starting the Server

```bash
cd ../JsServer
node ./index.js #For Mac / Linux
node .\index.js #For Windows
```

### Starting the Client Application

```bash
cd ../SCCSChatRoom
npm run dev
```

## SCCS Chatroom Application Login/Sign up Window

After suceesfully install dependan, the SCCS chatroom application presents a user-friendly login interface with a welcom message. The login screen includes the following fields:

- **Nickname (Optional):** Users can enter a preferred nickname.
- **Username:** Required field for the user's account name.
- **Password:** User's password must be atleast 8 characters.
- **Server IP:** IP address of the SCCSchat server.
- **Server Port:** The default port number is **_4567_** for client-server couumunication, therefore, It is recommended to maintain this configuration unless there is a specific requirement to establish communication on an alternative port.

![alt text](Readme_Images/login.png)

### Sign up Process

In order to create an account, enter a unique username, a password (minimum 8 characters), and the server IP address. Upon successful registration, a confirmation message will be displayed on the window as shown below.

![Sign up](<Readme_Images/Sign up.png>)

If any errors occur or invalid information is entered during the registration process, error messages will be displayed as shown below, indicating the specific reason for the account creation failure.

![Sign up failure](<Readme_Images/Sign up failed.png>)

### Login Process

After successfully creating an account, click the login button to access the application. Upon successful authentication, the SCCS chatroom window will appear. If login fails, an error message will be displayed. 

![alt text](<Readme_Images/Login failed.png>)

## Application Chatroom Interface

The SCCS chatroom interface features a dual-panel design, with the user list on the left and the chat area on the right. Key features include:
 
1. **User Information:** Displays the client's nickname, JID and server IP at the top.

2. **Public Chatroom:** It is a group chat among all online users on the network.

3. **Online Users List:** Provides a real-time display of all currently connected users, including their nicknames and JIDs.

4. **Messaging System:**   
a. _User Selection:_ Choose the recipient (individual user or public chatroom) before composing a message.  
b. _Recipient Indicator:_ The selected recipient's name is displayed at the top of the chat box.  
c. _Send Functionality:_ Click the "Send" button to transmit the message. 

5. **File Attachment:**  
a. _Attachment Selection:_ Click the arrow icon adjacent to the send button to choose a file.  
b. _File Size Limitation:_ Ensures attached files do not exceed 10 KB.  
c. _File Sending:_ Use the send button to transmit the attached file.

![alt text](<Readme_Images/SCCS Chatroom.png>)

## Configuration For Server-to-Server (S2S)

In order to enable cross-server communication, add the domain and IP address of the other groups' servers in the configuration file. This is shown in the example below, where the details of groups 11, 3, 4, 6, and 2 are added. settings for the server are found in `JsServer/configuration.json`. Adjust these settings to suit your environment after connecting to the same subnet in the network.

```json
{
    "server": [
        {   # Other Groups Servers Details Examples
            "domain": "s11",                  
            "address":"10.13.101.178"
        },
        {
            "domain": "s3",
            "address":"10.13.83.163"
        }
        ,
        {
            "domain": "s4",
            "address":"10.13.101.145"
        }
        ,
        {
            "domain": "s6",
            "address":"10.13.81.121"
        }
        ,
        {
            "domain": "s2",
            "address":"10.13.89.245"
        }
  ],
  # Application Server Details
  "defaultServerPort": "5555",
  "defaultClientPort": "4567",
  "defaultDomainName": "s1",
}
```  

## Security Considerations

- **Encryption:** All messages are end-to-encd encrypted
- **Environment Variables:** Stored sensitive data like encryption keys in environment variables.
- **Authentication:** Implemented strong passwords policy and *secure remote protocol8 is employed for autentication.
- **Validation:** Ensured proper validation and sanitization of all user inputs.
- **Secure Data Storage** Passwords are hashed with salt then stored in the database.

## Performance Optimization Techniques

- **Task Queues:** Use task queues to manage background tasks efficiently.
- **Database Indexing:** Implement indexing in the SQLite database for faster query execution.
- **Connection Pooling:** Use WebSocket connection pooling to manage multiple connections efficiently.

## Troublingshooting Guide

- Use appropriate commands for your operating system (macOS or Windows), as syntax and file paths may differ between platforms.
- Ensure Node.js and npm are updated to the latest compatible versions to avoid dependency conflicts and leverage new features.
- Maintain the original file and directory structure of the project to prevent import errors and ensure proper functionality.
- Verify network stability and ensure required IP addresses are accessible, as unstable connections or blocked IPs can disrupt the application's communication.
- Check for port conflicts and modify the configuration if necessary, ensuring the designated ports (5555, 4567) is available for the application's use.
- Configure firewalls and antivirus software to allow the application's network traffic, creating exceptions if needed to prevent communication blockages.

## License Information

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.

## Acknowledgments

- **[Cheng](https://github.com/FrogGuaGua)**: Initial project setup, server-side implementation, and incorporation of the most challenging backdoor (Backdoor Number 3).
- **[Shahzeb](https://github.com/Shahzeb892)**: Client-side implementation, UI design, and incorporation of the moderately difficult backdoor (Backdoor Number 2).
- **[Chen](https://github.com/TheMartyrAmbiguousFable)**: Database management, security features, and incorporation of the least difficult backdoor (Backdoor Number 1).
- **[Sabrina](https://github.com/Sabrinaafrine)**: Testing, performance optimization, documentation, and backdoor exploitation.
- Third-party libraries and resources used in this project.