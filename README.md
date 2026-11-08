# Cowrie SSH Honeypot Lab

I deployed a Cowrie SSH honeypot in Ubuntu on WSL and reconstructed a controlled SSH session from its JSON logs.

## Setup

I configured Cowrie to listen on `127.0.0.1:2222` and verified the listener with `ss`. When Cowrie initially failed to start, I traced the error to duplicate configuration settings, backed up the file, and applied a minimal local listener configuration.

## Results

Using the shared session ID `ea31146690de`, I correlated these events in `cowrie.json`:

1. `cowrie.session.connect` — The local SSH client connected to the honeypot.
2. `cowrie.login.success` — Cowrie accepted the `labtest` login.
3. `cowrie.command.input` — Cowrie recorded `whoami`, `pwd`, and `exit`.
4. `cowrie.session.closed` — The connection closed after about 159 seconds.

The lab used one controlled session from localhost. The attempted password is omitted from the published timeline.

## Lab Report

[Read the full lab report (PDF)](./Cowrie%20SSH%20Honeypot%20Lab.pdf)
