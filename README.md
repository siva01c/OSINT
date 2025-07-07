# OSINT Tools
Before running the project, copy .env.default to .env, then update your LinkedIn and OpenAI credentials and API keys in the .env file.

## LinkedIn Posts Analyser
This is a Jupyter Notebook project. The file linkedin.ipynb is a concept for a LinkedIn user post scraper and GenAI analyzer.
This tool is useful for OSINT purposes or for managing your digital footprint. It can retrieve LinkedIn posts from several years back and export them to a JSON file.

## Chat with GenAI
For the GenAI features, an OpenAI API key is required. In this part, the JSON file is imported into ChromaDB. Then, using the Gradio chat interface, an OpenAI chatbot is loaded with knowledge about the gathered LinkedIn posts.

