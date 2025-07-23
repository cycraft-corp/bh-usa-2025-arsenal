# All Talk, AI Action: Binary Analysis Toolkit MCP Server
Vibe reversing toolkits for local hosted LLMs presented in [BlackHat USA 2025 arsenal: All Talk, AI Action: Binary Analysis Toolkit MCP Server](https://www.blackhat.com/us-25/arsenal/schedule/index.html#all-talk-ai-action-binary-analysis-toolkit-mcp-server-45680).
## Requisites
* Hypervisior (VirtualBox/Vmware/HyperV ... etc)
    * **Two Windows** VM
    * One shall installed with IDA Pro + idalib
* IDA Pro 9.0 up
    * **idalib** required
* [Roo Code](https://github.com/RooCodeInc/Roo-Code) + VScode
    * Not required, but recommanded
    * Recommand version: `3.19.5`

## Project layout
```
├─BinAnalysisMCPs  # MCP collections
│  ├─ida-mcp
│  ├─speakeasy-mcp
│  └─x64dbg-mcp
└─docs
    ├─assets       # picture assets
    └─labs         # lab documents
```

## Architecture & Usage
![](/docs/assets/arch.png)

### VM setup
1. Install python + [uv](https://github.com/astral-sh/uv).
2. Disable Microsoft Defender or other antivirius.
    - [defendnot](https://github.com/es3n1n/defendnot)
       - ```irm https://dnot.sh/ | iex```
4. Disable Windows Security Mandatory ASLR option (for stablizing debugger output).
    <details>
    <summary>Click to View</summary>

    ```
    Set-Processmitigation -System -Disable ForceRelocateImages
   Set-Processmitigation -System -Disable BottomUp, HighEntropy
    ```
    ![alt text](/docs/assets/disable-aslr.png)
    </detail>
5. Copy MCPs into VM and install MCPs required packages via `uv`.
6. Copy samples **to same paths** in VMs.

#### x64dbg VM
1. Install [x64dbg](https://github.com/x64dbg/x64dbg) and [x64dbg-automate](https://github.com/dariushoule/x64dbg-automate).
2. **Take a snapshot** in case of malware **destroy whole enviroment**.

#### Speakeasy/IDA Pro VM
Install idalib


### MCP client(Roo Code) setup
1. Set API key & token limit
    <details>
    <summary>Click to View</summary>

    ![alt text](/docs/assets/set-api.png)
    </detail>
2. Enable **context condensing** with your preferred ratio, since it is very likely to reach the token limit of LLM (ex: [40962](https://huggingface.co/Qwen/Qwen3-32B) for `Qwen3-32B`)
    <details>
    <summary>Click to View</summary>

    ![alt text](/docs/assets/enable-condense.png)
    </detail>
3. Connnect MCP server, tweak your prompt, and start your advanture :D
    <details>
    <summary>Click to View</summary>

    ![alt text](/docs/assets/connect-mcp-server.png)
    ![alt text](/docs/assets/mode-selection.png)
    ![alt text](/docs/assets/mode-prompt.png)
    </details>

## Labs
To help you better understand how our toolkits work, we’ve provided several labs—ranging from CTF challenges to real-world malware—so you can become more familiar with them.

1. [Solve CTF challenge with MCP](/docs/labs/01.md)
2. [Examine C2 and behaviors of cobalt strike beacon](/docs/labs/02.md)
3. [Extract shellcode from loader process memory with debugger](/docs/labs/03.md)

## Difference with orignal MCP projects
Compared to previous projects, our work is more focused on supporting local hosted small language models(like `Qwen3-32B`). As a result, it features:

1. A more streamlined set of tools.
2. Simplified tool descriptions and workflows.
3. More LLM-friendly outputs.

For more details, please refer to each MCP project directory.

## Contributors and etc.
Please refer to [CREDITS.md](/docs/CREDITS.md).
