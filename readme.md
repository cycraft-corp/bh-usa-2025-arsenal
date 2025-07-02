# All Talk, AI Action: Binary Analysis Toolkit MCP Server
Vibe reversing toolkits for local hosted LLMs presented in [BlackHat USA 2025 arsenal: All Talk, AI Action: Binary Analysis Toolkit MCP Server](https://www.blackhat.com/us-25/arsenal/schedule/index.html#all-talk-ai-action-binary-analysis-toolkit-mcp-server-45680).

## Project layout
```

```

## Architecture & Usage
![](/docs/assets/arch.png)


## Labs
To help you better understand how our toolkits work, we’ve provided several labs—ranging from CTF challenges to real-world malware—so you can become more familiar with them.

1. [Solve CTF challenge with MCP](/docs/labs/01.md)
2. [Examine C2 and behaviour of cobalt strike beacon](/docs/labs/02.md)
3. [Extract shellcode from loader itself](/docs/labs/03.md)

## Difference with orignal MCP projects
Compared to previous projects, our work is more focused on supporting local hosted small language models(like `qwen3-32b`). As a result, it features:

1. A more streamlined set of tools.
2. Simplified tool descriptions and workflows.
3. More LLM-friendly outputs.

For more details, please refer to each MCP project directory.

## Lab sample links
* [Flare-On9 4th challenge: darn_mice](https://flare-on.com/files/Flare-On9_Challenges.zip)
* Realworld cobalt strike beacon
    * [loader](https://www.virustotal.com/gui/file/05ebd7a4983c7ae919935a69590cb3e88e0dcdbac243f40eb9aeb4892970cb7e/)
    * [shellcode](https://www.virustotal.com/gui/file/eb4006cc1a78239e63e9276de278609ede8a79c4d51382ee64747e7384fd9ec4)