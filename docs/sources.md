# Source notes

Primary references checked **2026-10-11**. These are documentation observations, not live compatibility tests. All controller requirements elsewhere in this repository are this project's proposals. IBM's cited changelog identifies versions but does not show release dates, so the date here records this review rather than a vendor release date.

| IBM reference | Documented capability relevant to the design |
| --- | --- |
| [Starting a non-interactive session](https://bob.ibm.com/docs/shell/getting-started/start-bobshell-non-interactive) | `bob run` accepts prompt arguments or stdin and provides `json` / `stream-json` output. Authentication requires `BOB_API_KEY`; interactive login is not reused. `--max-cost` is expressed in Bobcoins, and `--max-turns` limits agentic turns. Tool calls are pre-approved. Options include workspace selection, capability restrictions, and task resume. General API keys require a team context. |
| [Tool groups](https://bob.ibm.com/docs/shell/core-concepts/tools) | Named tool groups can be disabled. The documented table includes editing in Plan and Ask modes; a mode label therefore cannot establish this project's restriction profile. |
| [Approval settings](https://bob.ibm.com/docs/shell/configuration/approval-settings) | Documents group approvals and command-prefix approval/denial settings. This preview does not edit them or assume that interactive prompting applies to a noninteractive run. |
| [Lifecycle hooks](https://bob.ibm.com/docs/shell/configuration/lifecycle-hooks) | `PostToolUse` and `Stop` cannot block and ignore stdout. Hooks run without sandbox isolation. A stop hook is not a verification-and-repair controller. |
| [Shell changelog](https://bob.ibm.com/docs/shell/changelog#205) | The current 2.0.5 section documents task sharing between Bob Shell running as an ACP agent and connected editors. This is a native cross-editor continuity candidate, not evidence of an external shared board, a controller-owned contract, or current verification. Earlier entries record a correction to `--disable-mcp` behavior and support for background processes. Client-version qualification and descendant cleanup still need explicit evidence. |

## Interpretation limits

Structured session output reports session events and outcomes; the controller must independently decide whether repository acceptance conditions have been met. The docs' cost limit is not evidence of an exact invoice ceiling, and this project has not measured overshoot or accounting behavior.

The proposed contract is not an IBM workflow language, public plugin schema, or promise that Bob supports external stage enforcement. This repository supplies no SDK, REST endpoint, credential setup, provider adapter, or executable example.

Future implementation should fail closed when its required capability profile cannot be established for the installed client. Any additional source claim should link its primary reference and distinguish documentation from observed behavior.
