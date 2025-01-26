# Setting up a dev container for Go

* Primary author: [tangzoey](https://github.com/tangzoey)
* Reviewer: [Zixin Wei](https://github.com/starkersawz666)

## Prerequisites

To begin, ensure your system is equipped with the following:

1. **Docker**  
   Docker is essential for containerization. If you haven’t installed it yet, download it from [Docker Desktop](https://www.docker.com/products/docker-desktop/).

2. **Visual Studio Code (VSCode)**  
   Use VSCode as the recommended Integrated Development Environment (IDE). It can be downloaded from [Visual Studio Code](https://code.visualstudio.com/).

3. **Dev Containers Extension**  
   Install the Dev Containers extension in Visual Studio Code to enable container-based development.


---

## Step-by-Step Instructions

### 1. Set Up an Empty Project Directory

Begin by setting up a new empty directory for your project, and initialize a Git repository in this directory:

```bash
mkdir go-dev-container
cd go-dev-container
git init
```

---

### 2. Configure the Dev Container

Set up a `.devcontainer` directory and create a `devcontainer.json` file within your project:

```bash
mkdir .devcontainer
cd .devcontainer
touch devcontainer.json
```

Edit `devcontainer.json` with the following content:

```json
{
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/vscode/devcontainers/go:0-1.20",
    "customizations": {
        "vscode": {
            "extensions": [
                "golang.Go"
            ],
            "settings": {
                "go.useLanguageServer": true
            }
        }
    },
    "postCreateCommand": "go version"
}

```

**Explanation:**

- ```"image"``` Specifies Microsoft's official Go development container image.
- ```"extensions": ["golang.Go"]``` Ensures the Go extension for VSCode is automatically installed.
- ```"go.useLanguageServer": true``` Configures Go tools to use the language server.
- ```"postCreateCommand": "go version"``` Verifies the installed Go version after the container is built.

---

### 3. Launch the Project in a Dev Container

1. Open the project directory in VS Code.
2. Use the Command Palette (`Ctrl+Shift+P`) and select `Dev Containers: Reopen in Container`.
3. Wait for the container to build and launch.

---

### 4. Verify the Go Installation

Run the following command in the integrated terminal:

```bash
go version
```

You should see output confirming a recent version of Go (e.g., `go version go1.20 linux/amd64`).

---

### 5. Initialize a Go Project

Run the following command to initialize a new Go module:

```bash
go mod init hello-comp423
```

This command generates a `go.mod` file, which tracks dependencies for your project.

---

### 6. Write the "Hello COMP423" Program

Create a new file named `main.go`:

```bash
touch main.go
```

Edit `main.go` with the following content:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

---

### 7. Run the Program

To run the program directly:

```bash
go run main.go
```

Output:

```
Hello COMP423
```

**Note:** The `go run` command compiles and runs the program in one step without creating a binary file.

---

### 8. Build and Run the Binary

To compile the program into a binary:

```bash
go build -o hello
```

This creates a binary named `hello`. Run the binary:

```bash
./hello
```

Output:

```
Hello COMP423
```

**Discussion:**

- The `go build` command is similar to the `gcc` command in COMP211, which compiles source code into an executable.
- Unlike `go run`, `go build` creates a reusable binary that can be executed without Go installed.

---

### 9. Commit Your Changes

To save your work, commit your changes to Git:

```bash
git add .
git commit -m "Initial setup with Hello COMP423"
```

---

## Tutorial Outcome

To see an example of the completed Go project, visit the following [GitHub repository](https://github.com/tangzoey/comp423-go-container).