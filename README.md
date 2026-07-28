<!-- jr-brand:start -->
<div align="center">
  <a href="https://jannikreinhard.com/">
    <img src="https://raw.githubusercontent.com/JayRHa/.github/main/assets/readme/tool.svg" alt="Jannik Reinhard — Driving AI with passion" width="100%">
  </a>
  <h1>Intune Agent</h1>
  <p><strong>Python-based agent for Microsoft Intune device management automation and monitoring.</strong></p>
  <p>
  <a href="https://jannikreinhard.com/"><img src="https://img.shields.io/badge/Website-146CDD?style=flat-square&amp;logo=wordpress&amp;logoColor=white" alt="Website"></a>
  <a href="https://github.com/JayRHa"><img src="https://img.shields.io/badge/GitHub-081427?style=flat-square&amp;logo=github&amp;logoColor=white" alt="GitHub"></a>
  <a href="https://www.linkedin.com/in/jannik-r/"><img src="https://img.shields.io/badge/LinkedIn-0795FF?style=flat-square&amp;logo=linkedin&amp;logoColor=white" alt="LinkedIn"></a>
  <a href="https://x.com/jannik_reinhard"><img src="https://img.shields.io/badge/X-081427?style=flat-square&amp;logo=x&amp;logoColor=white" alt="X"></a>
  <a href="https://www.youtube.com/@jannikreinhard"><img src="https://img.shields.io/badge/YouTube-146CDD?style=flat-square&amp;logo=youtube&amp;logoColor=white" alt="YouTube"></a>
  </p>
  <p><sub>Driving AI with passion · Microsoft Foundry · Intune · Azure</sub></p>
</div>
<!-- jr-brand:end -->

## Two Implementation Approaches

This project provides two implementation approaches:

| Approach | File | Description |
|----------|------|-------------|
| **Direct OpenAI SDK** | `main.py` | Uses Azure OpenAI SDK directly with manual tool definitions |
| **Microsoft Agent Framework** | `main_agent_framework.py` | Uses the new unified Agent Framework (successor to Semantic Kernel + AutoGen) |

### Microsoft Agent Framework Benefits
- Built-in `@ai_function` decorator for cleaner tool definitions
- Native support for approval workflows on destructive actions
- Graph-based workflows for multi-agent orchestration
- Built-in OpenTelemetry integration for observability
- Middleware support for intercepting agent actions

## Prerequisites

- Azure subscription with an active Intune license
- Azure AI Foundry resource with a deployed model (GPT-4o or GPT-4)
- An app registration in Entra ID with Graph API permissions
- Python 3.10+ (3.10+ required for Microsoft Agent Framework)

## Required Graph API Permissions

Your app registration needs these Microsoft Graph API permissions (Application permissions). The `setup.sh` script configures these automatically:

- `DeviceManagementManagedDevices.Read.All`
- `DeviceManagementManagedDevices.ReadWrite.All`
- `DeviceManagementManagedDevices.PrivilegedOperations.All`
- `DeviceManagementConfiguration.Read.All`
- `DeviceManagementConfiguration.ReadWrite.All`
- `DeviceManagementApps.Read.All`
- `DeviceManagementApps.ReadWrite.All`
- `DeviceManagementRBAC.Read.All`
- `DeviceManagementServiceConfig.Read.All`

## Setup

1. Clone the repository

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Copy `.env.example` to `.env` and configure:
   ```bash
   cp .env.example .env
   ```

5. Edit `.env` with your settings:
   - `AZURE_OPENAI_API_KEY`: Your Azure OpenAI API key
   - `AZURE_OPENAI_ENDPOINT`: Your Azure OpenAI endpoint URL
   - `MODEL_DEPLOYMENT_NAME`: The deployed model name (e.g., `gpt-4o`)
   - `AZURE_TENANT_ID`: Your Entra ID tenant ID
   - `AZURE_CLIENT_ID`: Your app registration client ID
   - `AZURE_CLIENT_SECRET`: Your app registration client secret

## Usage

### Option 1: Direct OpenAI SDK (Classic)
```bash
python main.py
```

### Option 2: Microsoft Agent Framework (Recommended)
```bash
python main_agent_framework.py
```

### Example Queries

- "Show me all non-compliant devices"
- "Which Windows devices haven't synced in 48 hours?"
- "Break down our fleet by OS"
- "Find devices without disk encryption"
- "How many devices do we have?"
- "Show me all compliance policies"

## Available Tools

| Tool | Description |
|------|-------------|
| `get_device_count` | Get total count of managed devices |
| `get_noncompliant_devices` | List all non-compliant devices |
| `get_devices_by_os` | Filter devices by operating system |
| `get_stale_devices` | Find devices that haven't synced recently |
| `get_device_breakdown_by_os` | Get device counts grouped by OS |
| `get_compliance_policies` | List all compliance policies |
| `sync_device` | Trigger a device sync |
| `get_devices_without_encryption` | Find unencrypted devices |

## Project Structure

```
intune-agent-foundry/
├── main.py                    # Classic agent (direct OpenAI SDK)
├── main_agent_framework.py    # Agent using Microsoft Agent Framework
├── graph_helper.py            # Microsoft Graph API client
├── intune_tools.py            # Function tools (classic approach)
├── requirements.txt           # Python dependencies
├── setup.sh                   # Azure app registration setup script
├── .env.example               # Environment variable template
└── README.md
```

## Learn More

- [Microsoft Agent Framework Overview](https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview)
- [Agent Framework GitHub Repository](https://github.com/microsoft/agent-framework)
- [Microsoft Graph API for Intune](https://learn.microsoft.com/en-us/graph/api/resources/intune-graph-overview)

## License

This project is available under the terms in [LICENSE](LICENSE).

<!-- jr-brand-footer:start -->

---

<div align="center">
  <p><sub>Built and maintained by <a href="https://jannikreinhard.com/">Jannik Reinhard</a> · Microsoft MVP for Security and AI Platform.</sub></p>
  <p><a href="https://www.buymeacoffee.com/jannikreinf">Support the open-source work</a></p>
  <p><strong>Stay healthy, Cheers Jannik</strong></p>
</div>

<!-- jr-brand-footer:end -->
