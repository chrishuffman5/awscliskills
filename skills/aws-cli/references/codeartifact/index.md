# AWS CLI v2 -- CodeArtifact Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/codeartifact/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-domain` | Domain | Create a new CodeArtifact domain |
| `delete-domain` | Domain | Delete a domain |
| `describe-domain` | Domain | Describe a domain |
| `list-domains` | Domain | List all domains in the account |
| `get-domain-permissions-policy` | Domain | Get the resource policy for a domain |
| `put-domain-permissions-policy` | Domain | Set or update the resource policy for a domain |
| `delete-domain-permissions-policy` | Domain | Delete the resource policy for a domain |
| `create-repository` | Repository | Create a new repository |
| `delete-repository` | Repository | Delete a repository |
| `describe-repository` | Repository | Describe a repository |
| `list-repositories` | Repository | List all repositories in the account |
| `list-repositories-in-domain` | Repository | List repositories in a domain |
| `update-repository` | Repository | Update repository description or upstreams |
| `get-repository-endpoint` | Repository | Get the endpoint URL for a repository |
| `get-repository-permissions-policy` | Repository | Get the resource policy for a repository |
| `put-repository-permissions-policy` | Repository | Set or update the resource policy for a repository |
| `delete-repository-permissions-policy` | Repository | Delete the resource policy for a repository |
| `associate-external-connection` | Repository | Associate an external connection with a repository |
| `disassociate-external-connection` | Repository | Remove an external connection from a repository |
| `login` | Repository | Configure a package manager to use a CodeArtifact repository |
| `describe-package` | Package | Describe a package |
| `list-packages` | Package | List packages in a repository |
| `delete-package` | Package | Delete a package and all its versions |
| `get-associated-package-group` | Package | Get the package group associated with a package |
| `put-package-origin-configuration` | Package | Set the origin configuration for a package |
| `describe-package-version` | Package Version | Describe a package version |
| `list-package-versions` | Package Version | List versions of a package |
| `list-package-version-assets` | Package Version | List assets of a package version |
| `list-package-version-dependencies` | Package Version | List dependencies of a package version |
| `get-package-version-readme` | Package Version | Get the readme of a package version |
| `get-package-version-asset` | Package Version | Get a specific asset of a package version |
| `copy-package-versions` | Package Version | Copy package versions between repositories |
| `delete-package-versions` | Package Version | Delete specific package versions |
| `dispose-package-versions` | Package Version | Dispose of package versions (remove from upstream) |
| `update-package-versions-status` | Package Version | Update the status of package versions |
| `publish-package-version` | Package Version | Publish a generic package version |
| `get-authorization-token` | Auth | Get a temporary authorization token |
| `create-package-group` | Package Group | Create a package group |
| `delete-package-group` | Package Group | Delete a package group |
| `describe-package-group` | Package Group | Describe a package group |
| `list-package-groups` | Package Group | List package groups in a domain |
| `update-package-group` | Package Group | Update a package group |
| `update-package-group-origin-configuration` | Package Group | Update origin configuration for a package group |
| `list-allowed-repositories-for-group` | Package Group | List repositories allowed for a package group origin restriction |
| `list-associated-packages` | Package Group | List packages associated with a package group |
| `list-sub-package-groups` | Package Group | List sub-package-groups of a package group |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws codeartifact` commands.

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
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
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

### Package Formats
| Format | Description |
|--------|-------------|
| `npm` | npm packages |
| `pypi` | Python packages |
| `maven` | Maven/Java packages |
| `nuget` | NuGet/.NET packages |
| `generic` | Generic packages |
| `swift` | Swift packages |
| `cargo` | Rust/Cargo packages |
| `ruby` | Ruby gems |

### External Connections
| Connection | Description |
|------------|-------------|
| `public:npmjs` | npm public registry |
| `public:pypi` | Python Package Index |
| `public:maven-central` | Maven Central |
| `public:maven-googleandroid` | Google Android Maven |
| `public:maven-gradleplugins` | Gradle Plugins |
| `public:maven-commonsware` | CommonsWare Maven |
| `public:nuget-org` | NuGet Gallery |
| `public:ruby-gems-org` | RubyGems.org |
| `public:crates-io` | crates.io |

### Package Version Statuses
| Status | Description |
|--------|-------------|
| `Published` | Version is available for download |
| `Unfinished` | Version upload is incomplete |
| `Unlisted` | Version is not visible in listings but can be fetched directly |
| `Archived` | Version is archived and cannot be downloaded |
| `Disposed` | Version has been disposed |
| `Deleted` | Version has been deleted |

### Origin Restriction Modes
| Mode | Description |
|------|-------------|
| `ALLOW` | Allow publishing/upstream fetching |
| `BLOCK` | Block publishing/upstream fetching |
| `ALLOW_SPECIFIC_REPOSITORIES` | Allow from specific repositories only |
| `INHERIT` | Inherit from parent package group |
