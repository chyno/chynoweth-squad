# This is my squad files

#!/bin/bash
# install.sh in your dotfiles repository

# Define your desired path
TARGET_DIR="/home/node/workspaces/apps"
SQUAD_DIR="/home/node/workspaces/chynoweth-squad"
WORKSPACE_ROOT="/home/node/workspaces"

# 1. Create the parent directory
mkdir -p "$WORKSPACE_ROOT"

# 2. Move the repository from the default location to your subfolder
# Only move if the target doesn't exist and the source DOES exist
if [ -d "/home/node/workspace" ] && [ ! -d "$TARGET_DIR" ]; then
    echo "Relocating repository to $TARGET_DIR..."
    mv /home/node/workspace "$TARGET_DIR"
fi

# 3. Clone your second repository (SQUAD)
if [ ! -d "$SQUAD_DIR" ]; then
    git clone https://github.com/chyno/chynoweth-squad.git "$SQUAD_DIR"
fi

# 4. Create the symlink for your MCP skills
ln -sf "$SQUAD_DIR/.squad" "$TARGET_DIR/.squad"

# 5. Generate the .code-workspace file
cat <<EOF > "$WORKSPACE_ROOT/project.code-workspace"
{
  "folders": [
    { "name": "Apps", "path": "apps" },
    { "name": "Squad Skills", "path": "chynoweth-squad" }
  ],
  "settings": {
    "terminal.integrated.cwd": "/home/node/workspaces/apps"
  }
}
EOF


How to handle RebuildsPersistent Storage: Everything inside /home/node/ is typically tied to the container's lifecycle. To ensure persistence across full rebuilds, you should ideally perform these actions within /workspaces/ (the standard persistent mount in GitHub Codespaces) instead of /home/node/workspace/.Automatic Setup: Because this script is in your dotfiles, it runs every time you create or rebuild a codespace.The "One-Click" Step after RebuildBecause the devcontainer.json still points VS Code to /home/node/workspace/, when you first open the codespace, you might see an empty folder (since you moved the files).Press Ctrl+Shift+P (or Cmd+Shift+P).Run File: Open Workspace from File....Select /home/node/workspaces/project.code-workspace.VS Code will reload with both repositories visible in the sidebar, and your symlinks will be active.Would you like to know how to add repository-specific permissions to your GitHub account so that your dotfiles can clone your private chynoweth-squad repo without asking for a password?
