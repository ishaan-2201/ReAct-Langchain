# 🧠 Custom ReAct Agent Implementation with LangChain

This is a minimal yet powerful demonstration of how to **implement the ReAct (Reasoning + Acting)** pattern using **LangChain** and **OpenAI's LLMs**, with custom tools and prompt chaining logic.

---

## 💡 Motivation

The **ReAct (Reasoning and Acting)** paradigm empowers language models to **both think and act** — allowing them to solve complex tasks using external tools. While high-level agent frameworks abstract this for convenience, this project is a **from-scratch implementation** for educational and experimental purposes.

The goal was to:

- Understand and implement the ReAct loop manually.
- Learn how agents decide between actions and final answers.
- Gain finer control over prompt logic, scratchpads, and response handling.

---

<img width="929" alt="" src="https://github.com/ishaan-2201/ReAct-Langchain/blob/main/ReAct_Agent_Image.jpg?raw=true">

## 🧠 What is the ReAct Algorithm?

**ReAct** combines:

- **Reasoning** (thoughts about what to do next) and
- **Acting** (invoking tools to gather more information)

**_In a feedback loop that looks like this:_**

**_Question:_** What is the length of "Ishaan"?<br/>
**_Thought:_** I should check the character length of the text<br/>
**_Action:_** get*text_length
\*\*\_Action Input:*** "Ishaan"<br/>
**_Observation:_** 6<br/>
**_Thought:_** I now know the final answer<br/>
**_Final Answer:_\*\* 6

LangChain supports this via `ReActSingleInputOutputParser`, but this project builds the loop manually to show how it all works under the hood.

---

## 🔧 Features

- Uses **OpenAI** (via LangChain's `ChatOpenAI`) as the LLM.
- Employs a **custom prompt** based on Harrison Chase’s ReAct template.
- Registers and formats a dummy tool (`get_text_length`) using LangChain's tool abstraction.
- Parses outputs using `ReActSingleInputOutputParser` to distinguish between `AgentAction` and `AgentFinish`.
- Dynamically **invokes tools** and **feeds observations** back into the scratchpad.
- Repeats until a final answer is found.

---
