# Contributing

Thanks for taking a look at this project. Contributions are welcome.

## Reporting issues

If you find a bug or have a suggestion, please open an issue on GitHub.
It helps a lot if you include:
- what you expected to happen,
- what actually happened,
- the command you ran and the output you saw.

## Making changes

1. Fork the repository and create a new branch for your change.
2. Keep the script simple and readable. The whole point of `ask` is that
   it stays small and easy to understand.
3. Test your changes locally before opening a pull request. At a minimum
   try these cases:
   - a plain prompt passed as arguments,
   - a prompt piped in through stdin,
   - a prompt that mixes both.
4. Open a pull request and describe what you changed and why.

## Style

- Stick to plain Bash. The only external tools should be `curl` and `jq`.
- Try to keep lines reasonably short and use comments where things might
  not be obvious.
- Commit messages should briefly describe what the commit does.

## Questions

If something is unclear, just open an issue and ask. 
