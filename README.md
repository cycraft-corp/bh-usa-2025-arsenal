# All Talk, AI Action: Binary Analysis Toolkit MCP Server

This repository contains the lab materials for our presentation [BlackHat USA 2025 Arsenal: All Talk, AI Action: Binary Analysis Toolkit MCP Server](https://www.blackhat.com/us-25/arsenal/schedule/index.html#all-talk-ai-action-binary-analysis-toolkit-mcp-server-45680).

You can find the source code of our tool in: [BinaryAnalysisMCPs](https://github.com/cycraft-corp/BinaryAnalysisMCPs)

## Labs

These hands-on labs are designed to walk you through the core features of our MCP Server. The scenarios range from solving a CTF challenge to analyzing real-world malware samples.

1. [Lab 01: Solve CTF challenge with MCP](/labs/01.md)
2. [Lab 02: Examine C2 and behaviors of Cobalt Strike beacon](/labs/02.md)
3. [Lab 03: Extract shellcode from loader process memory with debugger](/labs/03.md)

## Setting Up Your Lab Environment

### Prerequisites

* Hypervisor (VirtualBox/Vmware/HyperV ... etc)
    * **Two Windows** VM
    * One should have IDA Pro + idalib installed
* IDA Pro (version 9.0 or newer)
    * **idalib** required
* [Roo Code](https://github.com/RooCodeInc/Roo-Code) + VScode
    * Not required, but recommended
    * Recommended version: `3.19.5`

### Architecture

![](/assets/arch.png)

### VM setup

1. Install python + [uv](https://github.com/astral-sh/uv).
2. Disable Microsoft Defender or other antivirus.
    - [defendnot](https://github.com/es3n1n/defendnot)
       - ```irm https://dnot.sh/ | iex```
3. Disable the Windows Security Mandatory ASLR option (to stabilize debugger output).
    <details>
    <summary>Click to View</summary>

    ```
    Set-Processmitigation -System -Disable ForceRelocateImages
   Set-Processmitigation -System -Disable BottomUp, HighEntropy
    ```
    ![alt text](/assets/disable-aslr.png)
    </detail>
4. Copy MCPs into VM and install MCPs required packages via `uv`.
5. Copy samples **to same paths** in VMs.

#### x64dbg VM

1. Install [x64dbg](https://github.com/x64dbg/x64dbg) and [x64dbg-automate](https://github.com/dariushoule/x64dbg-automate).
2. **Take a snapshot** in case of malware **destroy the whole environment**.

#### Speakeasy/IDA Pro VM

Install idalib

### MCP client (Roo Code) setup

1. Set API key & token limit
    <details>
    <summary>Click to View</summary>

    ![alt text](/assets/set-api.png)
    </detail>
2. Enable **context condensing** with your preferred ratio, since it is very likely to reach the token limit of LLM (ex: [40962](https://huggingface.co/Qwen/Qwen3-32B) for `Qwen3-32B`)
    <details>
    <summary>Click to View</summary>

    ![alt text](/assets/enable-condense.png)
    </detail>
3. Connect to MCP server, tweak your prompt, and start your adventure :D
    <details>
    <summary>Click to View</summary>

    ![alt text](/assets/connect-mcp-server.png)
    ![alt text](/assets/mode-selection.png)
    ![alt text](/assets/mode-prompt.png)
    </details>

## Differences with original MCP projects

Compared to previous projects, our work is more focused on supporting local hosted small language models(like `Qwen3-32B`). As a result, it features:

1. A more streamlined set of tools.
2. Simplified tool descriptions and workflows.
3. More LLM-friendly outputs.

For more details, please refer to each MCP project directory.

## Contributors
* [asef18766](https://github.com/asef18766)
* [oalieno](https://github.com/oalieno)
* [dange0](https://github.com/dange0)
* [AuTooong](https://github.com/AuTooong)