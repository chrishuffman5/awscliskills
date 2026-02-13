# AWS CLI v2 -- Device Farm Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/devicefarm/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-project` | Project | Create a new Device Farm project |
| `delete-project` | Project | Delete a project |
| `get-project` | Project | Get details of a project |
| `list-projects` | Project | List all projects |
| `update-project` | Project | Update a project |
| `get-account-settings` | Project | Get account-level settings |
| `create-device-pool` | Device Pool | Create a device pool |
| `delete-device-pool` | Device Pool | Delete a device pool |
| `get-device-pool` | Device Pool | Get details of a device pool |
| `list-device-pools` | Device Pool | List device pools in a project |
| `update-device-pool` | Device Pool | Update a device pool |
| `get-device-pool-compatibility` | Device Pool | Check device pool compatibility with a run |
| `get-device` | Device | Get details of a specific device |
| `list-devices` | Device | List available devices |
| `schedule-run` | Run | Schedule a test run |
| `stop-run` | Run | Stop a running test run |
| `delete-run` | Run | Delete a test run |
| `get-run` | Run | Get details of a test run |
| `list-runs` | Run | List test runs in a project |
| `list-unique-problems` | Run | List unique problems found in a run |
| `get-job` | Job | Get details of a job |
| `list-jobs` | Job | List jobs in a run |
| `stop-job` | Job | Stop a running job |
| `get-suite` | Suite | Get details of a test suite |
| `list-suites` | Suite | List suites in a job |
| `get-test` | Test | Get details of a test |
| `list-tests` | Test | List tests in a suite |
| `list-samples` | Sample | List samples in a job |
| `list-artifacts` | Artifact | List artifacts for a run/job/suite/test |
| `create-upload` | Upload | Create an upload |
| `delete-upload` | Upload | Delete an upload |
| `get-upload` | Upload | Get details of an upload |
| `list-uploads` | Upload | List uploads in a project |
| `update-upload` | Upload | Update an upload |
| `install-to-remote-access-session` | Upload | Install an app to a remote access session |
| `create-remote-access-session` | Remote Access | Create a remote access session |
| `delete-remote-access-session` | Remote Access | Delete a remote access session |
| `get-remote-access-session` | Remote Access | Get details of a remote access session |
| `list-remote-access-sessions` | Remote Access | List remote access sessions |
| `stop-remote-access-session` | Remote Access | Stop a remote access session |
| `create-network-profile` | Network Profile | Create a network profile |
| `delete-network-profile` | Network Profile | Delete a network profile |
| `get-network-profile` | Network Profile | Get details of a network profile |
| `list-network-profiles` | Network Profile | List network profiles |
| `update-network-profile` | Network Profile | Update a network profile |
| `create-instance-profile` | Instance Profile | Create an instance profile |
| `delete-instance-profile` | Instance Profile | Delete an instance profile |
| `get-instance-profile` | Instance Profile | Get details of an instance profile |
| `list-instance-profiles` | Instance Profile | List instance profiles |
| `update-instance-profile` | Instance Profile | Update an instance profile |
| `create-vpce-configuration` | VPCE Config | Create a VPCE configuration |
| `delete-vpce-configuration` | VPCE Config | Delete a VPCE configuration |
| `get-vpce-configuration` | VPCE Config | Get details of a VPCE configuration |
| `list-vpce-configurations` | VPCE Config | List VPCE configurations |
| `update-vpce-configuration` | VPCE Config | Update a VPCE configuration |
| `create-test-grid-project` | Test Grid | Create a test grid (Selenium) project |
| `delete-test-grid-project` | Test Grid | Delete a test grid project |
| `get-test-grid-project` | Test Grid | Get details of a test grid project |
| `list-test-grid-projects` | Test Grid | List test grid projects |
| `update-test-grid-project` | Test Grid | Update a test grid project |
| `create-test-grid-url` | Test Grid | Create a URL for a test grid session |
| `get-test-grid-session` | Test Grid | Get details of a test grid session |
| `list-test-grid-sessions` | Test Grid | List test grid sessions |
| `list-test-grid-session-actions` | Test Grid | List actions in a test grid session |
| `list-test-grid-session-artifacts` | Test Grid | List artifacts for a test grid session |
| `list-offerings` | Offering | List available device offerings |
| `list-offering-promotions` | Offering | List offering promotions |
| `list-offering-transactions` | Offering | List offering transactions |
| `get-offering-status` | Offering | Get current offering status |
| `purchase-offering` | Offering | Purchase a device offering |
| `renew-offering` | Offering | Renew a device offering |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws devicefarm` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
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

### Region Availability
Device Farm is only available in `us-west-2`. All commands must target this region.

### Run Result Values
| Result | Description |
|--------|-------------|
| `PENDING` | Run is pending |
| `PASSED` | Run passed |
| `WARNED` | Run passed with warnings |
| `FAILED` | Run failed |
| `SKIPPED` | Run was skipped |
| `ERRORED` | Run errored |
| `STOPPED` | Run was stopped |

### Upload Types
| Type | Description |
|------|-------------|
| `ANDROID_APP` | Android application package (.apk) |
| `IOS_APP` | iOS application package (.ipa) |
| `WEB_APP` | Web application |
| `EXTERNAL_DATA` | External test data |
| `APPIUM_JAVA_JUNIT_TEST_PACKAGE` | Appium Java JUnit test package |
| `APPIUM_JAVA_TESTNG_TEST_PACKAGE` | Appium Java TestNG test package |
| `APPIUM_PYTHON_TEST_PACKAGE` | Appium Python test package |
| `APPIUM_NODE_TEST_PACKAGE` | Appium Node.js test package |
| `APPIUM_RUBY_TEST_PACKAGE` | Appium Ruby test package |
| `CALABASH_TEST_PACKAGE` | Calabash test package |
| `INSTRUMENTATION_TEST_PACKAGE` | Instrumentation test package |
| `UIAUTOMATION_TEST_PACKAGE` | UI Automation test package |
| `UIAUTOMATOR_TEST_PACKAGE` | UI Automator test package |
| `XCTEST_TEST_PACKAGE` | XCTest test package |
| `XCTEST_UI_TEST_PACKAGE` | XCTest UI test package |

### Upload Status Values
| Status | Description |
|--------|-------------|
| `INITIALIZED` | Upload created but file not yet uploaded |
| `PROCESSING` | Upload is being processed |
| `SUCCEEDED` | Upload processed successfully |
| `FAILED` | Upload processing failed |

### Device Platform Values
| Platform | Description |
|----------|-------------|
| `ANDROID` | Android devices |
| `IOS` | iOS devices |
