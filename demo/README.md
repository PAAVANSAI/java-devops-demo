# Demo - Spring Boot AWS DevOps App

A simple Spring Boot web application that displays **"Welcome to AWS DevOps"**.

---

## Prerequisites

- **Windows 10/11**
- **Git** installed ([Download Git](https://git-scm.com/downloads))

---

## Setup Instructions (Step by Step)

### Step 1: Install Java JDK 17

Open **PowerShell** and run:

```powershell
winget install --id EclipseAdoptium.Temurin.17.JDK --accept-source-agreements --accept-package-agreements
```

> ⚠️ **After installation, close and reopen PowerShell** so that `JAVA_HOME` is picked up.

Verify the installation:

```powershell
java -version
```

You should see output like:
```
openjdk version "17.0.x" ...
```

---

### Step 2: Clone the Project

```powershell
git clone <REPOSITORY_URL>
cd demo
```

> Replace `<REPOSITORY_URL>` with the actual Git repo URL shared by your instructor.

If you received the project as a **ZIP file** instead, extract it and open PowerShell inside the `demo` folder (the one containing `pom.xml`).

---

### Step 3: Build the Project

```powershell
.\mvnw.cmd clean install -DskipTests
```

> This uses the Maven Wrapper (`mvnw.cmd`) included in the project — **no need to install Maven separately**.
> The first run will download dependencies and may take 2-3 minutes.

---

### Step 4: Run the Application

```powershell
.\mvnw.cmd spring-boot:run
```

You should see output like:

```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v4.1.0)

... Tomcat started on port 9090 ...
... Started DemoApplication ...
```

---

### Step 5: Open in Browser

Go to: **http://localhost:9090**

You should see:

> **Welcome to AWS DevOps**

---

### Step 6: Stop the Application

Press `Ctrl + C` in the PowerShell terminal to stop the server.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `java` is not recognized | Close and reopen PowerShell after installing JDK. If it still doesn't work, set `JAVA_HOME` manually (see below). |
| `JAVA_HOME` not set | Run: `[System.Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\Program Files\Eclipse Adoptium\jdk-17.0.19.10-hotspot", "User")` then restart PowerShell. |
| Port 9090 already in use | Change the port in `src/main/resources/application.properties` — edit `server.port=9090` to another port like `9091`. |
| `mvnw.cmd` not recognized | Make sure you are inside the correct `demo` folder (the one with `pom.xml`). Run `dir` to check. |
| Build fails with dependency errors | Make sure you have an internet connection. Maven needs to download dependencies on first run. |

---

## Project Structure

```
demo/
├── pom.xml                          # Maven config & dependencies
├── mvnw.cmd                         # Maven Wrapper (Windows)
├── mvnw                             # Maven Wrapper (Mac/Linux)
└── src/
    └── main/
        ├── java/com/devops/demo/
        │   ├── DemoApplication.java     # Main entry point
        │   └── HelloController.java     # REST controller (handles "/" route)
        └── resources/
            └── application.properties   # App config (port, etc.)
```

---

## Quick Commands Summary

| Action | Command |
|---|---|
| Install JDK 17 | `winget install --id EclipseAdoptium.Temurin.17.JDK --accept-source-agreements --accept-package-agreements` |
| Build the project | `.\mvnw.cmd clean install -DskipTests` |
| Run the app | `.\mvnw.cmd spring-boot:run` |
| Stop the app | `Ctrl + C` |
| Check Java version | `java -version` |
