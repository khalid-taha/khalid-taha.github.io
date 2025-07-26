**Making a Stateless LLM Project‑Aware**

Large language models have goldfish memories—they don’t recall past calls unless you hand them that context every single time. Yet you *can* run a weeks‑long coding project with ChatGPT (or any other LLM) if you wrap a thin layer of “state management” around each request.  
Below you’ll find the key ideas in plain, practical language. They work no matter how you connect: web chat, REST API, CLI, whatever.

---

### 1  Persist state outside the conversation  

Treat the model like a freelance coder who clears their desk at the end of the day. Anything you don’t file away will vanish.  
Keep three small documents in your own storage—Git, S3, a database row, anything you control:

| File | What’s inside | Why it matters |
|------|---------------|----------------|
| **Blueprint / spec** | The lasting requirements and architecture notes. | Gives the model a north‑star every call. |
| **Journal / log** | A running human‑readable diary of what changed and why. | Lets you audit progress and decisions. |
| **State file** | Exactly one entry like `next_task: “build parser”` plus a `status`. | Tells the model what to do *right now*. |

The assistant only reads and edits these files; it never invents its own version of reality.

---

### 2  Embed a deterministic contract in every prompt  

Before you hit “send,” your wrapper code builds a prompt that repeats the ground rules:

1. Load the state file.  
2. If there’s one task marked **todo**, finish it in this turn.  
3. If nothing is todo, pull the next milestone from the spec and write it into the state file.  
4. Make sure there’s **never more than one open task**.

Because you restate the contract every time, the model can’t drift—even if the chat history is empty.

---

### 3  Return full files, not diffs  

Ask for the *entire* contents of each file it touched. Why? You can overwrite the old file without worrying about merge conflicts, and your test runner can prove everything still works. The transport doesn’t matter—fenced code blocks, JSON parts, multipart: just send the whole thing.

---

### 4  Keep each round bite‑sized and atomic  

* One todo → one model call → one test run.  
* Tests happen **after** files are written.  
* If tests fail, you feed the error log back; the same todo stays put.  
* If tests pass, mark the task **done** and queue the next one.

Small, clear steps mean bugs are easy to trace and roll back.

---

### 5  Park heavy data elsewhere  

Chat messages should stay text‑only. Big binaries (images, model weights, year‑long CSVs) live in cloud storage; the state file just holds a link or hash. That keeps prompts fast and avoids attachment headaches.

---

### 6  Automate the envelope, let the model do the thinking  

A lightweight driver script can:

1. Read the three docs from storage.  
2. Build the prompt with the contract above.  
3. Call the LLM.  
4. Parse the reply, save the files.  
5. Run your test suite; if green, commit and push; if red, send the errors back as the next prompt.

The script handles routine plumbing— the model focuses on writing code and updating the state doc.

---

**Take‑away**  
Long‑running work with an LLM isn’t magic; it’s a simple protocol. Persist a tiny control plane (spec, journal, state) and remind the model of the rules at every turn. Follow that rhythm and your AI teammate will pick up exactly where it left off—no matter how or when you call it.
