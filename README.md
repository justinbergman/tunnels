# SSH Tunnel Simulator

An interactive, single-page simulator for learning SSH port forwarding with `-L` (local) and `-R` (remote) tunnels.

Students type real `ssh` commands into a simulated terminal, then send packets through the tunnel and watch (or step through) each stage: the connection to the listening port, the trip through the encrypted SSH connection, and the onward connection from the tunnel exit to the destination.

## What it covers

- A four-host network in a line: `coworker — laptop — bastion — intranet`. Each host can reach only its neighbours.
- `-L` and `-R` forwards, including bind addresses (`127.0.0.1`, `0.0.0.0`, a specific interface), `-g`, `sudo` for ports below 1024, and `-o ExitOnForwardFailure=yes`.
- The bastion's `sshd_config` settings `GatewayPorts` and `AllowTcpForwarding`, and how they change what students' commands actually do.
- A Sandbox with ready-made examples, and nine Challenges with hints and solutions.

Command format used throughout:

```
ssh alex@203.0.113.10 -L 8080:10.0.0.20:80
ssh alex@203.0.113.10 -R 8000:127.0.0.1:3000
```

## Hosting with GitHub Pages

The whole app is `index.html`; there is no build step.

1. In this repository, open **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Choose branch **main** and folder **/ (root)**, then **Save**.
4. After a minute or two the site is live at `https://justinbergman.github.io/tunnels/`.

`.nojekyll` tells GitHub Pages to serve the files as they are, without running Jekyll.

GitHub Pages on a private repository needs a paid GitHub plan; on a free plan the repository must be public.

## Running locally

Open `index.html` in any modern browser. An internet connection is only needed for the web fonts; without it the page falls back to system fonts.

## Notes

- Challenge progress is saved in each student's browser (local storage). It isn't shared between devices, and you can't see it centrally.
