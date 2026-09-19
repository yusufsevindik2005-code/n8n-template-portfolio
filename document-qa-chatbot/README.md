# Company Document Q&A Chatbot (n8n + Claude RAG)

An n8n chat agent that answers questions grounded in your own company documents, not general knowledge. Two connected workflows: an ingestion pipeline that watches a Google Drive folder and indexes every newly uploaded file into a vector store, and a chat agent that retrieves the relevant passages for each question before Claude answers, naming the document it used.

**Tested end to end** with real documents: it caught two files that contradicted each other (3 remote days vs 2 remote days for different teams) and named both source files, returned exact figures and names correctly, and said so instead of guessing when the answer was not in any document.

**Highlights**
- Retrieval-as-tool design: the agent searches your documents before answering and can rephrase the query itself
- Source-named answers: every indexed chunk carries its file name and link, so the agent can say which document an answer came from and flag it when two documents disagree
- Per-conversation memory keyed on the chat session, not one shared thread, so several people can ask questions at the same time
- Ingestion is separate from chat: index new files without touching the chat agent

**What you need (all have free tiers, no card required to start)**
- n8n (cloud or self-hosted)
- Google Drive (the folder you want indexed)
- Anthropic API key (Claude answers the questions; pay per use, roughly 1.7 US cents per question in our measured test)
- Mistral API key (embeddings, free experiment plan)
- Qdrant (free cloud cluster or self-hosted)

**Good to know**
- Ingestion picks up newly uploaded files. Editing an existing file does not re-index it, upload the new version as a new file.
- A free Qdrant cloud cluster pauses after a week without use, so an idle test setup needs a quick wake-up.
- Setup takes some patience: five credentials to connect. The workflow files use placeholders for all of them.

**Stack**: n8n + Claude (answering) + Mistral embeddings + Qdrant.

*(Full template files are delivered on purchase. This repo is a portfolio showcase, not the download.)*
