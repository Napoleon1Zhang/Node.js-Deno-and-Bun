## Node.js Deno and Bun Tutorial

### Setup
#### Node.js
Open your web browser and go to the official Node.js website: https://nodejs.org.

On the website's homepage, you will see two download options: LTS (Long Term Support) and Current version. If you want the most stable version, it's recommended to choose the LTS version. Click the download link under "LTS" and "Recommended for Most Users."

Choose the appropriate installer for your operating system. Node.js supports Windows, macOS, and various Linux distributions. Click the download link for your OS.

After the download is complete, double-click the installer and follow the installation wizard's instructions. On Windows, you may need to select some installation options, but most users can accept the default settings.

![picture 1](images/1.png)

Once the installation is complete, open a terminal (command prompt) and run the following command to check if Node.js is successfully installed:

```code
node -v
```
This will display the installed Node.js version. Then, run:

```code
npm -v
```

This will show the installed npm (Node Package Manager) version.

Now, you have successfully installed Node.js and npm, and you can start using Node.js to run JavaScript code and manage project dependencies.

If you need to install the Current version of Node.js, you can choose "Current" on the Node.js official website and follow the same installation steps.

Please note that Node.js versions are continuously updated, so you can upgrade to new versions at any time, but for production environments, it's recommended to use the LTS version for stability and long-term support.

#### Bun

Make sure that your WSL (Windows Subsystem for Linux) system, which is Ubuntu in your case, has unzip installed. Otherwise, you may encounter an error when installing Bun.

```code
error: unzip is required to install Bun (see: https://github.com/Jarred-Sumner/bun#unzip-is-required
```
Open WSL using the Terminal and install `unzip` on your Ubuntu system with the following command.
```code
sudo apt-get install unzip
curl https://bun.sh/install | bash
```
The following prompt indicates a successful installation.
```code
Bun was installed successfully to /root/.bun/bin/bun

Manually add the directory to your $HOME/.bashrc (or similar)

   BUN_INSTALL="/root/.bun"
   PATH="$BUN_INSTALL/bin:$PATH"
```


Let's create a new "http.js" file and write some code.
```code
// http.js
export default {
  port: 3000,
  fetch(request) {
    return new Response("Welcome to Bun!");
  },
};
```
Start the HTTP service.
```code
bun run http.js
```
To access http://localhost:3000, you should see the message "Welcome to Bun!" which indicates that it's running successfully.

#### Deno
install code:
```code
brew install deno
```

In Visual Studio Code, you can add a launch.json file to configure your debugging settings. 
```code
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceFolder}/your-app.js",
      "preLaunchTask": "npm: start",
      "outFiles": [],
      "runtimeArgs": [
        "--inspect-brk=0"
      ],
      "env": {
        "NODE_ENV": "development"
      },
      "sourceMaps": false,
      "protocol": "inspector",
      "skipFiles": [
        "<node_internals>/**"
      ]
    }
  ]
}
```

With the configuration set up, you can now start writing your source code. First, you can add dependencies for Oak and MySQL in your deps.ts file.
