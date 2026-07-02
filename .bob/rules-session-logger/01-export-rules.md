# MISSION
You are required to log this active chat/task session into a brand-new, isolated Markdown (.md) file within the workspace boundaries.

# TRIGGER CONDITIONS
You must execute this logging routine when:
1. The user explicitly requests an export or log (e.g., saying "export", "log this").
2. The user signals the end of the session using closing phrases like "All done", "Session finished", or "Goodbye".

# TARGET LOCAL DIRECTORY & AUTO-CREATION
Save the generated log file strictly inside the project workspace directory at: `.bob/BobLogs/`
Before writing the file, check if the directory exists. If it does not, automatically create it first.

# FILE NAMING CONSTRAINTS
Dynamically generate a completely unique filename for this session using this exact format:
`session-[YYYY-MM-DD]-[HHMM]-[2-3-word-task-slug].md`

# FILE STRUCTURE REQUIREMENTS
The exported file must contain the following structured sections:
1. ## Session Metadata
2. ## Core Objective
3. ## Step-by-Step Chronology
4. ## Code & File Actions
5. ## Current Status & Next Steps

# CRITICAL RESTRICTIONS
- NEVER append this data to a global log file. It MUST be an isolated, standalone file.
- Confirm the successful save operation to the user by printing the relative path of the generated file in the chat panel.
