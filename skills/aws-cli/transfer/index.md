# AWS CLI v2 -- Transfer Family Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/transfer/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-server` | Server | Create a Transfer Family server |
| `delete-server` | Server | Delete a server |
| `describe-server` | Server | Get server details |
| `list-servers` | Server | List all servers |
| `update-server` | Server | Update server configuration |
| `start-server` | Server | Start a stopped server |
| `stop-server` | Server | Stop a running server |
| `describe-security-policy` | Server | Get security policy details |
| `list-security-policies` | Server | List available security policies |
| `test-identity-provider` | Server | Test identity provider settings |
| `create-user` | User | Create a user on a server |
| `delete-user` | User | Delete a user |
| `describe-user` | User | Get user details |
| `list-users` | User | List users for a server |
| `update-user` | User | Update user settings |
| `import-ssh-public-key` | User | Import an SSH public key for a user |
| `delete-ssh-public-key` | User | Delete an SSH public key |
| `create-access` | Access | Create directory-service-based access |
| `delete-access` | Access | Delete an access entry |
| `describe-access` | Access | Get access details |
| `list-accesses` | Access | List access entries for a server |
| `update-access` | Access | Update access settings |
| `create-connector` | Connector | Create an SFTP or AS2 connector |
| `delete-connector` | Connector | Delete a connector |
| `describe-connector` | Connector | Get connector details |
| `list-connectors` | Connector | List all connectors |
| `update-connector` | Connector | Update connector settings |
| `start-file-transfer` | Connector | Start a file transfer via connector |
| `start-directory-listing` | Connector | List remote directory contents |
| `start-remote-delete` | Connector | Delete remote files |
| `start-remote-move` | Connector | Move remote files |
| `test-connection` | Connector | Test connector connectivity |
| `list-file-transfer-results` | Connector | List file transfer results |
| `create-agreement` | Agreement | Create an AS2 agreement |
| `delete-agreement` | Agreement | Delete an agreement |
| `describe-agreement` | Agreement | Get agreement details |
| `list-agreements` | Agreement | List agreements for a server |
| `update-agreement` | Agreement | Update agreement settings |
| `create-profile` | Profile | Create an AS2 profile |
| `delete-profile` | Profile | Delete a profile |
| `describe-profile` | Profile | Get profile details |
| `list-profiles` | Profile | List profiles |
| `update-profile` | Profile | Update profile settings |
| `create-workflow` | Workflow | Create a post-upload workflow |
| `delete-workflow` | Workflow | Delete a workflow |
| `describe-workflow` | Workflow | Get workflow details |
| `list-workflows` | Workflow | List all workflows |
| `describe-execution` | Workflow | Get workflow execution details |
| `list-executions` | Workflow | List workflow executions |
| `send-workflow-step-state` | Workflow | Send custom step state |
| `import-host-key` | Host Key | Import a host key |
| `delete-host-key` | Host Key | Delete a host key |
| `describe-host-key` | Host Key | Get host key details |
| `list-host-keys` | Host Key | List host keys for a server |
| `update-host-key` | Host Key | Update host key description |
| `import-certificate` | Certificate | Import an AS2 certificate |
| `delete-certificate` | Certificate | Delete a certificate |
| `describe-certificate` | Certificate | Get certificate details |
| `list-certificates` | Certificate | List certificates |
| `update-certificate` | Certificate | Update certificate dates/description |
| `create-web-app` | Web App | Create a web app portal |
| `delete-web-app` | Web App | Delete a web app |
| `describe-web-app` | Web App | Get web app details |
| `list-web-apps` | Web App | List web apps |
| `update-web-app` | Web App | Update web app settings |
| `describe-web-app-customization` | Web App | Get web app branding |
| `update-web-app-customization` | Web App | Update web app branding |
| `delete-web-app-customization` | Web App | Delete web app branding |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait server-online` | Wait | Wait until server is online |
| `wait server-offline` | Wait | Wait until server is offline |

---

## Global Options

These options are available on ALL `aws transfer` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Server States
| State | Description |
|-------|-------------|
| `ONLINE` | Server is accepting connections |
| `OFFLINE` | Server is stopped |
| `STARTING` | Server is starting up |
| `STOPPING` | Server is shutting down |
| `START_FAILED` | Server failed to start |
| `STOP_FAILED` | Server failed to stop |

### Identity Provider Types
| Type | Description |
|------|-------------|
| `SERVICE_MANAGED` | Managed by Transfer Family (SSH keys) |
| `AWS_DIRECTORY_SERVICE` | AWS Managed Microsoft AD |
| `API_GATEWAY` | Custom via API Gateway |
| `AWS_LAMBDA` | Custom via Lambda function |

### Supported Protocols
| Protocol | Description |
|----------|-------------|
| `SFTP` | SSH File Transfer Protocol |
| `FTPS` | File Transfer Protocol over SSL |
| `FTP` | File Transfer Protocol (unencrypted) |
| `AS2` | Applicability Statement 2 (B2B) |

### ID Patterns
| Resource | Pattern | Example |
|----------|---------|---------|
| Server | `s-[0-9a-f]{17}` | `s-0123456789abcdef0` |
| User | 3-100 chars | `myuser` |
| Connector | `c-[0-9a-f]{17}` | `c-0123456789abcdef0` |
| Agreement | `a-[0-9a-f]{17}` | `a-0123456789abcdef0` |
| Profile | `p-[0-9a-f]{17}` | `p-0123456789abcdef0` |
| Workflow | `w-[0-9a-f]{17}` | `w-0123456789abcdef0` |
| Host Key | `hostkey-[0-9a-f]{17}` | `hostkey-0123456789abcdef0` |
| Certificate | `cert-[0-9a-f]{17}` | `cert-0123456789abcdef0` |
| Web App | `webapp-[0-9a-f]{17}` | `webapp-0123456789abcdef0` |
