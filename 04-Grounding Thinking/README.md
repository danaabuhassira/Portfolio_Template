# U4 — GROUND ITS KNOWLEDGE
## Grounding Thinking

> Generating a convincing answer does not mean having the knowledge to answer correctly.

In this unit, I learned how to build AI assistants that answer from specific knowledge, how information travels from a source to an answer, and how to test where a system fails and improve it with evidence.

---

## 🎯 Capability

**Knowledge-Grounded AI Systems Engineering**

The ability to design an assistant that relies on defined knowledge, understand the path from source to answer (retrieval, context and generation), and evaluate and improve its quality.

---

## 🧠 What I Learned

* **Define the Assistant:** Setting purpose, scope, behavior, constraints and success criteria before building.
* **Engineer the Knowledge:** Choosing and judging sources, separating instructions from knowledge, and preparing documents for retrieval.
* **Understand Grounding & RAG:** Following a question through query, retrieval, context and generation, and knowing that RAG does not guarantee a correct answer.
* **Engineer Retrieval Quality:** Understanding search types, Top-K, thresholds and context quality.
* **Evaluate & Improve:** Testing with varied questions, telling correctness from groundedness, diagnosing whether a failure comes from knowledge, retrieval, context or generation, and comparing results against a baseline.

---

## 🛠️ Projects

### 01 — Guided Project

**Project:** TECHFIX — AI Computer Troubleshooting Assistant

An Arabic assistant built with Dify that answers computer troubleshooting questions using a dedicated knowledge base.

* **Problem:** Users facing everyday computer problems often cannot find clear, safe troubleshooting guidance in Arabic.
* **Solution:** A Dify chatflow (Start, Knowledge Retrieval, LLM, Answer) with a four-document knowledge base. The assistant asks for details when a description is vague, stays within its scope, and does not invent steps.
* **Tools:** Dify, Dify Knowledge Base, LLM, Markdown, GitHub

[Explore the Project](https://github.com/danaabuhassira/Portfolio_Template/tree/main/04-Grounding%20Thinking/Course-Project)

### 02 — Independent Project

**Project:** Freelance Compass (بوصلة الفريلانسر)

A knowledge-grounded assistant that answers new freelancers' questions from the official documentation of freelance platforms.

* **Problem:** Rules differ between platforms, and a wrong number or rule can cost a freelancer money or their account.
* **Solution:** A RAG assistant built on official sources for Upwork, Freelancer, Khamsat and Mostaql. It answers from retrieved passages, shows the source and copy date, and says it has no confirmed information when the sources do not cover a question.
* **Tools:** Dify, Dify Knowledge Base, Gemini, Markdown, GitHub

[Explore the Project](https://github.com/danaabuhassira/Portfolio_Template/tree/main/04-Grounding%20Thinking/Independent-Project)

---

## 🔍 Engineering Focus

In this unit, I focused on these questions:

1. What is the assistant for, and what is outside its scope?
2. Is the knowledge reliable, current and complete?
3. Was the right information retrieved, and was it enough?
4. Is the answer correct, and is it supported by the retrieved context?
5. When something fails, is the cause the knowledge, the retrieval, the context or the generation?
6. Did a change improve the system, and did it break something else?

---

## 📌 Key Takeaway

> **Understand the Knowledge. Engineer the Retrieval. Evaluate the System. Improve with Evidence.**

---

## 📈 Capability Progress

* Defining an assistant's purpose, scope and limits.
* Choosing and evaluating knowledge sources.
* Building a knowledge base and a retrieval workflow.
* Testing with varied question types.
* Diagnosing failures by stage.
* Documenting experiments and results.

---

## 🔗 Related Projects

* [Guided Project](https://github.com/danaabuhassira/Portfolio_Template/tree/main/04-Grounding%20Thinking/Course-Project)
* [Independent Project](https://github.com/danaabuhassira/Portfolio_Template/tree/main/04-Grounding%20Thinking/Independent-Project)

**Next: U5 — CONTROL ITS AGENCY**
