# IBM Bob IDE Custom Configurations & Modes

This repository serves as a centralized hub for custom modes, automated rules, and workflow extensions for the IBM Bob AI Assistant inside your IDE. 

By utilizing these configurations, you can extend Bob's core capabilities, introduce role-specific developer personas, and automate workspace actions like file auditing, documentation generation, and task history exports.

---

## 📂 Repository Architecture

* `.bob/` - The project-level directory containing custom mode definitions and modular instruction rules.
  * `custom_modes.yaml` - The main configuration index where all custom developer personas are defined.
  * `rules-{mode-slug}/` - Dedicated folders containing specific behavioral instructions linked to individual modes.
* `*.yaml` (Root Files) - Unified standalone configuration payloads designed for global IDE installation.

---

## 🛠 Setup & Installation Workflows

You can implement the configurations found in this repository using either a localized workspace approach or a universal global approach.

### Method 1: Workspace Project Setup (Recommended)
Use this workflow to activate custom modes automatically for anyone working inside a specific project repository.

#### Step 1: Clone and Link the Configurations
1. Clone this configuration repository to your local computer:
   ```bash
   git clone [repository-link]
   ```
2. Copy the entire hidden `.bob/` folder from this repository and paste it directly into the root directory of your active project workspace. Your target project layout should look like this:
   ```text
   your-active-project/
   ├── .bob/
   │   ├── custom_modes.yaml
   │   └── rules-[custom-mode-slug]/
   │       └── instructions.md
   └── src/
   ```
   *(Note: Folders starting with a dot are hidden by default on macOS. Press `Cmd + Shift + .` inside Finder to toggle hidden file visibility).*

#### Step 2: Configure Workspace Bounds (If Applicable)
If any of the custom modes in this repository generate background log assets or hidden build targets (such as `.bob/BobLogs/`), ensure you append those paths to your active project's `.gitignore` file so they are never tracked or committed back to your team's remote source control.

---

### Method 2: Global IDE Configuration (Universal Setup)
Use this workflow if you want custom modes universally available across all project directories you open inside your IDE, without pasting a `.bob` folder into every separate project layout.

1. Clone this configuration repository to your local computer:
   ```bash
   git clone [repository-link]
   ```
2. Open your development environment window.
3. Click on the **BOB Settings (Gear Icon)** located at the bottom of the Bob chat UI panel view.
4. Navigate to the **Modes** configuration tab menu options.
5. Click on the **Imports** button asset.
6. Navigate into the cloned repository, open the **`import-global-custom-mode/`** folder, and select the specific configuration `.yaml` file for the mode you wish to install (e.g., `session-logger.yaml`).


## 🚀 Activating and Executing Your Custom Modes

After deploying your files using either Method 1 or Method 2, initialize the new environment configurations using these steps:

1. **Reload Bob:** Open your IDE Command Palette (`Ctrl + Shift + P` on Windows/Linux or `Cmd + Shift + P` on macOS), type `Reload Window`, and press **Enter**.
2. **Switch Active Persona:** Click the **Modes Dropdown** menu wrapper located at the top header of Bob's chat panel layout window.
3. Select your newly imported custom mode from the populated selections.

### Workspace Operation & Automation
Once a custom mode is active, Bob dynamically pulls the corresponding markdown rules from the workspace to guide his processing boundaries. 
* If a mode requires background directories to run execution commands, **Bob will automatically generate those folders inside the workspace** the first time the relevant trigger conditions or slash commands are executed.

---

## 📋 Available Custom Modes

The following custom personas are configured and ready to use in this repository:

### 1. 📝 Session Logger (`session-logger`)
* **Description:** A meticulous engineering assistant designed to automate your development documentation. When you finish a task and issue a closing phrase (like *"All done"* or *"Goodbye"*), Bob captures the entire conversation history, code changes, and project milestones. He then compiles them into an isolated, standalone, timestamped Markdown file saved cleanly inside the `.bob/BobLogs/` directory.

