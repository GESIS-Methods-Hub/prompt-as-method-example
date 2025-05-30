# Prompt-as-Method Example

A simple example to showcase using a prompt as a method.

The prompt is defined in the [`prompt.json`](prompt.json).

```json
{
    "task": "https://raw.githubusercontent.com/GESIS-Methods-Hub/prompt-as-method/refs/heads/main/examples/sentiment/task.json",
    "model": "llama3.1",
    "messages": [
        {
            "content": "Judge whether the following text has 'positive', 'neutral' or 'negative' sentiment. Answer with a JSON object with the sentiment and your confidence (between 0 and 1).\n\n{{{text}}}",
            "role": "user"
        }
    ]
}
```

In the prompt, `{{{text}}}` is replaced by the values in the `text`-column of [`data.csv`](data.csv):

```csv
text,sentiment
The food was terrible,negative
This phone is awesome!,positive
```

To run it, make sure you have an [Ollama](https://ollama.com/download) (or another LLM server) running on the default port on your local machine:

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

Output (indentation added, confidence might chance):

```json
{
    "input":{"text":"The food was terrible","sentiment":"negative"},
    "output":{"sentiment":"negative","confidence":0.9}
}
{
    "input":{"text":"This phone is awesome!","sentiment":"positive"},
    "output":{"sentiment":"positive","confidence":1}
}
```
