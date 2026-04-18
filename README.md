
A small command-line tool that sends prompts to an OpenAI-compatible chat
completions API and prints the reply.

Written in Bash. Only `curl` and `jq` are required.

## Requirements

- `bash`
- `curl`
- `jq`
- An API key for any OpenAI-compatible provider (Groq, OpenAI, Together,
  OpenRouter, a local server that speaks the same format, etc.)

## Setup

Set these three environment variables before using the tool:

```bash
export ASK_API_URL="https://api.groq.com/openai/v1/chat/completions"
export ASK_MODEL="llama-3.3-70b-versatile"
export ASK_API_KEY="your_api_key_here"
```

You can put these in your `~/.bashrc` so they are set automatically in
every new shell.

Make the script executable:

```bash
chmod +x ask
```

Optionally move it somewhere on your `PATH`, for example:

```bash
sudo mv ask /usr/local/bin/
```

## Usage

Pass the prompt as arguments:

```bash
ask "What year was the Eiffel Tower built?"
```

All arguments are joined into a single prompt:

```bash
ask "Establishment dates of" "Turkey" "Azerbaijan" "Japan"
```

Pipe text into `ask` through stdin:

```bash
cat script.sh | ask "Explain what this Bash script does:"
```

Combine arguments and stdin:

```bash
echo "ls -la" | ask "What does this command do?"
```

Use it inside command substitution:

```bash
ask "Explain this output:" "$(uname -a)"
```

## Alias example

A handy grammar-fixing alias:

```bash
alias ask-fix="ask 'Correct any grammatical, spelling, or punctuation errors in the input text. Input text:'"
```

Then:

```bash
ask-fix "their going too the store"
```

## Known limitations

- The tool only supports the chat completions endpoint. Streaming,
  function calling, and vision inputs are not implemented.
- There is no conversation history. Every call is a fresh request, so
  the model does not remember earlier questions.
- Errors from the API are printed as raw JSON. The script does not try
  to pretty-print or interpret them.
- The system prompt is hard-coded. If you want a different one you need
  to edit the script.
- No retry logic. A temporary network failure will simply fail the call.

## License

MIT. See the `LICENSE` file.
