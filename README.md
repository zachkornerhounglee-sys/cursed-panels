# CURSED PANELS - JJK boss rush (Manga-In-Motion / Kinetic Ink)

`index.html` is the whole game (HTML+CSS+JS+PeerJS inlined; only Google Fonts is external).

## Play
Open `index.html`. HOST GAME gives a link; friends open it and join. SOLO needs no network.
WASD move, mouse aim, click = strike, Q / right-click = skill, E / Space = Domain (100 CE).
A ring closes on your character every 1.1s. Strike as it lands for a BLACK FLASH (x2.5+ damage, streaks stack, +25 CE).
During a DOMAIN CLASH, mash E / Space.

## Deploy on GitHub Pages
Push `index.html` to a repo, then Settings > Pages > deploy from branch. Share `https://<you>.github.io/<repo>/`. The host's lobby link is that URL plus `#<code>`.
Signalling uses the free PeerJS cloud broker; gameplay runs peer-to-peer over WebRTC. Strict corporate/school NATs may need a TURN server (pass `config` to `new Peer`).

## Netcode
Host-authoritative. Clients send inputs at 30Hz; host simulates at 60Hz and broadcasts snapshots at 20Hz. Clients predict their own movement and extrapolate projectiles. Max 4 players.

## Tuning
Black Flash window: `CH[n].bf` (seconds either side of the ring; 0.001s is below one frame, so the defaults are 0.05 to 0.10s). Boss data: `BOSSES`. Perks: `PERKS`.
Dev: `cd dev && npm i && npm run build && npm test` (jsdom smoke test drives the sim through all 4 bosses).
