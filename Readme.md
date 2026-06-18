# This is my squad files

#!/bin/bash
# install.sh in your dotfiles repository

 
  [ You Type: "@squad build a new user profile tab" ]
                         │
                         ▼
        [.github/agents/squad.agent.md] (Coordinator)
          Reads your prompt, assesses the workspace
                         │
        ┌────────────────┴────────────────┐
        ▼                                 ▼
 [.squad/agents/]                  [.copilot/skills/]
Consults sub-agent charters       Triggers targeted skills
to spin up specialized roles       (e.g., /generate-component)
(Frontend Dev, Tester, etc.)       to output styled React code
        │                                 │
        └────────────────┬────────────────┘
                         ▼
               [.copilot/mcp-config.json]
       Executes package scripts to test/verify build
