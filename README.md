# Tango MCP Server Setup Instructions

Connect Tango's Context Engineering for AI Development Teams to your favorite development tools.

## 🚀 Quick Start

The Tango MCP Server is available at: `https://mcp.liketango.dev/mcp`

You'll need a JWT token for authentication. Get yours creating a FREE account at `https://app.liketango.dev/`

## 📱 Setup by Platform

### Team, Enterprise (Claude.ai)

1. Navigate to **Settings** in the sidebar on web or desktop
2. Scroll to **Integrations** at the bottom and click **Add more**
3. In the prompt enter:
   - **Integration name**: Tango
   - **Integration URL**: `https://mcp.liketango.dev/mcp`
4. Add your JWT token when prompted
5. Make sure to enable the tools in any new chats

### Free, Pro (Claude for Desktop)

1. Open the file `~/Library/Application Support/Claude/claude_desktop_config.json`
2. Add the following configuration:

```json
{
  "mcpServers": {
    "tango": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.liketango.dev/mcp",
        "--header",
        "Authorization:${TANGO_AUTH_TOKEN}"
      ],
      "env": {
        "TANGO_AUTH_TOKEN": "Bearer YOUR_JWT_TOKEN_HERE"
      }
    }
  }
}
```

3. Replace `YOUR_JWT_TOKEN_HERE` with your actual JWT token
4. Restart the Claude desktop app

### Cursor

**Option 1: Quick Setup**
1. Press `CTRL/CMD+P` and search for **MCP: Add Server**
2. Select **Command (stdio)**
3. Enter: `npx -y mcp-remote https://mcp.liketango.dev/mcp --header "Authorization:Bearer YOUR_JWT_TOKEN"`
4. Enter the name **Tango** and hit enter
5. Activate using **MCP: List Servers**, select **Tango**, then **Start Server**

**Option 2: Manual Configuration**
1. Open Cursor settings with `CMD+,` (Mac) or `CTRL+,` (Windows/Linux)
2. Search for "MCP" or "Model Context Protocol"
3. Edit your `mcp.json` file and add:

```json
{
  "mcpServers": {
    "tango": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.liketango.dev/mcp",
        "--header",
        "Authorization:${TANGO_AUTH_TOKEN}"
      ],
      "env": {
        "TANGO_AUTH_TOKEN": "Bearer YOUR_JWT_TOKEN_HERE"
      }
    }
  }
}
```

### Windsurf

1. Press `CTRL/CMD + ,` to open Windsurf settings
2. Scroll to **Cascade -> MCP servers**
3. Select **Add Server -> Add custom server**
4. Add the following:

```json
{
  "mcpServers": {
    "tango": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.liketango.dev/mcp",
        "--header",
        "Authorization:${TANGO_AUTH_TOKEN}"
      ],
      "env": {
        "TANGO_AUTH_TOKEN": "Bearer YOUR_JWT_TOKEN_HERE"
      }
    }
  }
}
```

### Zed

1. Press `CMD+,` to open Zed settings
2. Add the following to your settings:

```json
{
  "context_servers": {
    "tango": {
      "command": {
        "path": "npx",
        "args": [
          "-y",
          "mcp-remote",
          "https://mcp.liketango.dev/mcp",
          "--header",
          "Authorization:${TANGO_AUTH_TOKEN}"
        ],
        "env": {
          "TANGO_AUTH_TOKEN": "Bearer YOUR_JWT_TOKEN_HERE"
        }
      },
      "settings": {}
    }
  }
}
```

## 🔑 Getting Your JWT Token

1. Log in to [Tango](https://app.liketango.dev)
2. Navigate to your Account Settings
3. Find the "Security" tag
4. Generate and copy your JWT token
5. Keep it secure - this token provides access to all your project data!

## 🛠️ Available MCP Tools

Once connected, you'll have access to these powerful tools:

### `tango_start`
Initialize a development session by loading all memory bank files for your project. This gives the AI complete context about your project's history, decisions, and current state.

```
@tango_start
```

### `tango_tasks`
Fetch active context and individual task files from the memory bank. Perfect for understanding what needs to be done next.

```
@tango_tasks
```

### `tango_plan`
Review and creates a sequential thinking implementation for your task. Helps maintain consistency with project decisions.

```
@tango_plan
```

### `tango_update`
Update the memory bank with development progress, bug fixes, feature additions, and other important project or individual updates.

```
@tango_update "development_progress - Implemented user authentication"
```

## 🔧 Troubleshooting

### "401 Unauthorized" Error
- Check that your JWT token is valid and not expired
- Ensure you've included "Bearer " before the token
- Verify you have access to the project

### Connection Failed
- Verify the server URL is correct: `https://mcp.liketango.dev/mcp`
- Check your internet connection
- Try updating mcp-remote: `npm update -g mcp-remote`

### Tools Not Available
- Ensure the MCP server is properly configured
- Restart your editor after configuration changes
- Check that the server shows as "connected" in your editor

### Cursor Space-Escaping Issue
If you're having issues with Cursor on Windows, make sure to use the environment variable approach shown above, which avoids spaces in the header argument.

## 🚨 Security Notes

- **Never share your JWT token publicly**
- Tokens are project-specific and grant access to your memory bank
- Store tokens securely in environment variables when possible
- Rotate tokens regularly for better security

## 📚 Additional Resources

- [Tango Documentation](https://docs.liketango.dev)
- [MCP Protocol Specification](https://modelcontextprotocol.io)
- [mcp-remote GitHub](https://github.com/geelen/mcp-remote)

## 💬 Support

Having issues? Contact us:
- Email: contact@liketango.dev
- Discord: [Join our community](https://discord.gg/tango)
