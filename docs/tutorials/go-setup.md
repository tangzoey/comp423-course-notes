# Setting up a dev container for Go

* Primary author: [tangzoey](https://github.com/tangzoey)
* Reviewer: [Zixin Wei](https://github.com/starkersawz666)

## Prerequisites

Before starting, ensure you have the following installed on your system:

- **Docker**  Docker is containerization platform. If Docker has not been installed, please go to [Docker Desktop](https://www.docker.com/products/docker-desktop/) to downlaod and install.
- **Visual Studio Code**  [VSCode](https://code.visualstudio.com/) is the Integrated Development Environment (IDE) recommended here. 
- **Dev Containers Extension**  installed inside Visual Studio Code.

---

## Step-by-Step Instructions

### 1. Create a Blank Directory

Start by creating a new blank directory for your project:

```bash
mkdir go-dev-container
cd go-dev-container
```

Initialize a new Git repository:

```bash
git init
```

---

### 2. Add Dev Container Configuration

Create a `.devcontainer` folder in your project directory and add a `devcontainer.json` file:

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

- ```"image"``` Uses the official Microsoft Go Dev Container base image.
- ```"extensions": ["golang.Go"]``` Ensures the Go VS Code plugin is installed.
- ```"go.useLanguageServer": true``` Configures Go tools to use the language server.
- ```"postCreateCommand": "go version"``` Verifies the installed Go version after the container is built.

---

### 3. Open the Project in a Dev Container

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

This creates a `go.mod` file, which tracks dependencies for your project.

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

## Result Following the Tutorial

An expected result of the go project is given at [Github](https://github.com/tangzoey/comp423-go-container).

## Congratulations!

You have successfully run your first go program!