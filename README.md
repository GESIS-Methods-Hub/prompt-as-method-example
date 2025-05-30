# Prompt-as-Method Example

A simple example to showcase using a [prompt](prompt.json) as a method on some [data](data.csv).

If you have an [Ollama](https://ollama.com/download) running on the default port on your local machine:

```shell
# ensure LLM is downloaded
ollama pull llama3.1

# initialize virtual environemnt
python3 -m venv .venv && source .venv/bin/activate

# install prompt-as-method
pip install prompt-as-method

# run the prompt
python -m prompt_as_method --prompt prompt.json --data data.csv
```
