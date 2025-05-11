# go-project-script


# Go Project Scaffolder with TUI, Cobra & Markdown

This script automates the creation of a new Go project, pre-configured with a Terminal User Interface (TUI) using Bubble Tea, Command Line Interface (CLI) argument parsing with Cobra, and Markdown rendering capabilities via Glamour.

It's designed to give you a quick start for building modern CLI applications in Go.

## Features of the Scaffolding Script

* **Interactive Setup**: Prompts for a project name.
* **Directory Structure**: Creates a standard Go project layout (`cmd/`, `internal/`).
* **Go Modules**: Initializes a Go module for your project.
* **Dependency Management**: Automatically fetches necessary Go packages:
    * `github.com/spf13/cobra` (for CLI structure)
    * `github.com/charmbracelet/bubbletea` (for TUI components)
    * `github.com/charmbracelet/lipgloss` (for TUI styling)
    * `github.com/charmbracelet/glamour` (for Markdown rendering)
* **Boilerplate Code**: Generates starter code for:
    * `main.go`
    * A root Cobra command (`cmd/root.go`)
    * A sample TUI command (`cmd/tuiCmd.go`)
    * A Bubble Tea model (`internal/tui/model.go`)
    * A sample Markdown rendering command (`cmd/renderCmd.go`)
* **.gitignore**: Creates a basic `.gitignore` file suitable for Go projects.
* **Build & Run Instructions**: Provides clear next steps after project generation.

## Prerequisites

* **Go**: You must have Go installed and configured on your system. The script will check for its presence. If not installed, visit [https://golang.org/doc/install](https://golang.org/doc/install).
* **Bash Shell**: The script is a Bash script and should be run in a Bash-compatible environment (common on Linux and macOS; available on Windows via WSL or Git Bash).

## How to Use

1.  **Save the Script**:
    Save the content of the `go_project_script.sh` (provided in the accompanying document) to a file on your local system. For example, name it `create_go_tui_project.sh`.

2.  **Make it Executable**:
    Open your terminal and navigate to the directory where you saved the script. Run the following command to make it executable:
    ```bash
    chmod +x create_go_tui_project.sh
    ```

3.  **Run the Script**:
    Execute the script from your terminal:
    ```bash
    ./create_go_tui_project.sh
    ```

4.  **Follow Prompts**:
    * The script will first check if Go is installed.
    * It will then ask you to enter a name for your new project. This name will be used for the directory and the Go module (e.g., `my-cool-app`).

5.  **Project Generation**:
    The script will create a new directory with your project's name, set up the Go module, download dependencies, and generate all the boilerplate files.

6.  **Navigate and Explore**:
    Once the script finishes, it will print instructions. You will already be inside the newly created project directory.

## Generated Project Structure

If you named your project `my-app`, the structure will look like this:

my-app/├── cmd/│   ├── root.go       # Cobra root command│   ├── tuiCmd.go     # Cobra command to launch the TUI│   └── renderCmd.go  # Cobra command to render Markdown├── internal/│   └── tui/│       └── model.go  # Bubble Tea model for the TUI├── go.mod            # Go module definition├── go.sum            # Go module checksums├── main.go           # Main application entry point└── .gitignore        # Git ignore file
## After Generation

The script will output instructions on how to build and run your new application. Typically:

1.  **Run commands directly (development)**:
    * `go run main.go --help` (to see all available commands)
    * `go run main.go tui` (to launch the sample TUI)
    * `go run main.go render-md` (to render sample Markdown)

2.  **Build a binary**:
    * `go build -o <your_project_name> main.go`
    * For example: `go build -o my-app main.go`

3.  **Run the compiled binary**:
    * `./<your_project_name> --help`
    * `./<your_project_name> tui`
    * `./<your_project_name> render-md`

## Customization

* **Module Path**: By default, the Go module path is the same as the project name. For public projects intended for services like GitHub, you'll want to re-initialize your module with a full path (e.g., `github.com/yourusername/yourprojectname`) and update the import paths in the `.go` files accordingly. The script provides a tip about this.
* **TUI Logic**: The `internal/tui/model.go` file contains a basic Bubble Tea model. You can expand this with more complex logic, views, and updates.
* **Cobra Commands**: Add more subcommands to `cmd/` and register them in `cmd/root.go` or other parent commands.
* **Markdown Styling**: The `cmd/renderCmd.go` uses `glamour.WithAutoStyle()`. You can explore other Glamour options for different Markdown rendering styles (e.g., `glamour.DarkStyle`, `glamour.LightStyle`, or custom stylesheets).

## Contributing to the Scaffolding Script

If you have suggestions or improvements for the `go_project_script.sh` itself, please feel free to propose them!
