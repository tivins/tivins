# tivins

**A fully local AI stack on a single 16 GB GPU** — LLM, memory, images, video, music, voice —
built as small reusable bricks in TypeScript on [Bun](https://bun.sh).<br>
Software architect & developer · TypeScript, PHP, C++, Rust, Python ·
[YouTube][yt] · [Stack Overflow][so] (750+ answers)

```mermaid
flowchart LR
  subgraph Bricks
    stack[llm-stack-ts<br><i>services + shared GPU lease</i>]
    lib[llm-lib-ts<br><i>LLM client, agents, tools</i>]
    mem[llm-memory-ts<br><i>semantic memory</i>]
    comfy[comfyui-client-ts<br><i>image · video · music</i>]
    ui[ts-ui<br><i>terminal UI</i>]
  end
  subgraph Local services
    llama[llama.cpp]
    comfyui[ComfyUI]
    pg[(Postgres + pgvector)]
  end
  subgraph Apps
    studio[Studio<br><i>images, videos, songs</i>]
    chat[Chat<br><i>multi-bot, memory</i>]
    more[forums, quizzes,<br>widgets, …]
  end
  stack --> llama & comfyui
  lib --> llama
  comfy --> comfyui
  mem --> pg
  Bricks --> Apps
```

## Bricks

| Brick | What it does |
| :--- | :--- |
| [llm-lib-ts][lib] | OpenAI-compatible client (llama.cpp, OpenRouter): chat, streaming, JSON Schema output, `Agent` + `ToolRegistry`, embeddings, rerank |
| [llm-stack-ts][stack] | Starts and stops local services (llama.cpp, ComfyUI, embeddings, STT…) from one `stack.toml`; GPU lease shared between processes |
| [llm-memory-ts][memory] | Long-term semantic memory: Postgres + pgvector, recall (ANN then rerank), deduplication |
| [comfyui-client-ts][comfy] | ComfyUI client: Qwen Image, Krea 2, FLUX 3 Klein, MiniMax H3 (image & video), Wan 2.2, MiniMax Music 3, upscale, interpolation |
| [ts-ui][tsui] | Terminal primitives for Bun CLIs: spinner, steps, colors, timing |

## See it run

Everything below is generated on one home PC, no cloud.

[![One GPU, six eras](https://img.youtube.com/vi/ff9biMHGTgM/mqdefault.jpg)](https://youtu.be/ff9biMHGTgM)
[![A photo becomes a song](https://img.youtube.com/vi/K3y11J4hhV4/mqdefault.jpg)](https://youtu.be/K3y11J4hhV4)
[![A grandmother who doesn't exist](https://img.youtube.com/vi/Xk1vc9smSKA/mqdefault.jpg)](https://youtu.be/Xk1vc9smSKA)

*How my programs learned to share one GPU · A photo becomes a song · A grandmother who doesn't exist comes to life* (in French)

<details>
<summary><b>Earlier work</b></summary>

### NLVM

* [nlvm-specs](https://github.com/nlvm-lang/nlvm-specs) — language specifications *(Markdown)*
* [nlvm](https://github.com/nlvm-lang/nlvm) — implementation *(Rust)*
* [vvm](https://github.com/tivins/vvm) — first version, archived *(C++)*

### PHP & tools

* [PHP Solid](https://github.com/tivins/php-solid) — detects LSP and ISP violations in PHP code
* [Inferred Dependency Injection](https://github.com/tivins/poc-di-inferred) — automatic DI by reflection (PoC)
* [API Interface and DTO](https://github.com/tivins/poc-api-interface) — request/response DTOs, typed handler and OpenAPI from one definition (PoC)
* [taskman](https://github.com/tivins/taskman) — project management for AI pipelines (MCP, CLI, web, SQLite)
* [Deven](https://github.com/tivins/deven) — dockerized PHP environment with GPU support
* [comprendre](https://github.com/tivins/comprendre) — documentation in French (patterns, concepts, frameworks, tests)

</details>

[yt]: https://www.youtube.com/@tivinsStuff
[so]: https://stackoverflow.com/users/9193372/syscall
[lib]: https://github.com/tivins/llm-lib-ts
[stack]: https://github.com/tivins/llm-stack-ts
[memory]: https://github.com/tivins/llm-memory-ts
[comfy]: https://github.com/tivins/comfyui-client-ts
[tsui]: https://github.com/tivins/ts-ui
