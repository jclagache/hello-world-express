# Hello World Express

Express.js application demonstrating the use of devfiles and ODO for development on OpenShift.
The use of the Visual Studio Code [OpenShift plugin](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-openshift-connector) is presented there as well as the use of [odo](https://odo.dev/) in command line.

## Prerequisites

1. **ODO CLI**
   ```bash
   # Install ODO on Windows
   curl -L https://developers.redhat.com/content-gateway/file/pub/openshift-v4/clients/odo/v3.16.1/odo-windows-amd64.exe -o odo.exe
   ```

3. **OpenShift Access**
   - Cluster URL
   - Authentication token
   - Project/namespace permissions

2. **VS Code + OpenShift Toolkit (Optional)**
   - Install the [OpenShift Toolkit](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-openshift-connector) extension
   - The extension integrates ODO and provides a graphical interface for development

## Inner-Loop Development

### Option 1: Command Line (ODO CLI)

1. **Cluster Login**
   ```bash
   odo login --token=<token> --server=<server-url>
   ```

2. **Initialization (not necessary in this case)**
   ```bash
   odo init
   ```

3. **Development Mode**
   ```bash
   odo dev
   ```

### Option 2: VS Code with OpenShift Toolkit

1. **Cluster Login**
   - Open OpenShift view
   - Click "Log in to cluster"
   - Paste connection token

2. **Component Creation**
   - In the "Components" view
   - Click "Create Component"
   - Follow the creation wizard

3. **Development**
   - Right-click on component
   - Select "Start Dev"
   - Development environment starts automatically

4. **Debug**
   - Right-click on component
   - Select "Debug"
   - VS Code debugger connects automatically

## VS Code Extension Features

- OpenShift components and resources view
- Guided component creation
- Development lifecycle management
- Integrated debugging
- Real-time logs
- Automatic port forwarding

## Project Structure

```
hello-world-express/
├── .devfile.yaml       # Environment configuration
├── app.js             # Application entry point
├── test/             # Tests
│   └── test.js
└── package.json      # Dependencies and scripts
```

## Devfile Configuration

```yaml
commands:
  - id: install
    exec:
      component: runtime
      commandLine: npm install
      workingDir: ${PROJECT_SOURCE}

  - id: run
    exec:
      component: runtime
      commandLine: npm start
      workingDir: ${PROJECT_SOURCE}

  - id: debug
    exec:
      component: runtime
      commandLine: npm run debug
      workingDir: ${PROJECT_SOURCE}

  - id: test
    exec:
      component: runtime
      commandLine: npm test
      workingDir: ${PROJECT_SOURCE}
```

## Development Workflow

1. **Startup**
   - Via CLI: `odo dev`
   - Via VS Code: Right-click > Start Dev

2. **Development**
   - Modify code
   - Automatic synchronization
   - Hot reload active

3. **Testing**
   - Via CLI: `odo dev`
              `odo run test`
   - Via VS Code: Right-click > Run Test

4. **Debugging**
   - Via CLI: `odo dev --debug`
   - Via VS Code: Right-click > Debug

## Resources

- [ODO Documentation](https://odo.dev/docs)
- [OpenShift Toolkit Documentation](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-openshift-connector)
- [OpenShift Guide](https://docs.openshift.com)

## License

MIT

## Author

jcl
