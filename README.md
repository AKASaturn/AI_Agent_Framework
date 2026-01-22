```markdown
# AI NPC Framework — Minimal Agent for Virtual Characters

A lightweight, privacy-first framework for building AI NPCs (Non-Player Characters) with tool calling, memory, and voice capabilities.

> **v0.1 MVP**: Core execution engine only. No memory, no TTS, no clients — just the essential loop.

---

## 🚀 Quick Start

1. **Install**
   ```bash
   git clone https://github.com/AKASaturn/ai-npc-framework.git
   cd ai-npc-framework
   pip install -e .
   ```

2. **Run Example**
   ```bash
   python examples/basic.py
   ```
   You should see:
   ```
   🤖 Agent responded: 
   ✅ File written successfully: workspace/hello.txt
   📄 Content: Hello from AI NPC!
   ```

---

## 🧩 How to Use

### 1. Implement Your LLM Client
Your LLM client must have a `generate(messages, tools)` method that returns:
```python
{
  "content": str,
  "tool_calls": [{"id": "...", "function": {"name": "...", "arguments": {...}}}],
  "usage": {"total_tokens": int}  # optional
}
```

### 2. Implement Your Tools
Each tool must have:
- A `name` class attribute (string)
- An `async execute(**kwargs)` method that returns:
  ```python
  {"success": bool, "content": str, "error": str}
  ```

### 3. Launch Agent
```python
agent = Agent(llm_client=my_llm, tools=[my_tool], system_prompt="You are Sarah.")
agent.add_user_message("Do something useful.")
result = await agent.run_step()
```

---

## 📦 Dependencies

- **Core**: None (pure Python 3.9+)
- **Optional**: `tiktoken` (for future token counting)

---

## 🔮 What's Next?

This MVP is the foundation for:
- Persistent memory (SQLite + RAG)
- Local TTS integration (Tacotron2 + HiFi-GAN)
- Multi-user isolation
- Live2D / Unity frontends

See our roadmap in the full documentation (coming soon).
```

---
