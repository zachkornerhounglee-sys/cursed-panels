# CURSED PANELS — JJK boss rush

An arcade-styled, single-file browser boss rush with solo mode and up to four-player, host-authoritative co-op. The cabinet-style visuals use a deep purple backdrop, gold trim, pink bloom, and hand-drawn anime curse sprites. The game is bundled in `index.html`; no install is needed to play solo.

## Play

Open `index.html`. Choose **SOLO RUN** or **HOST CO-OP**. The host shares the lobby link with friends, who open it and join. Select a fighter and ready up.

- **WASD / arrow keys:** move
- **Left / right Shift:** dash through attacks (brief invulnerability, about a 1-second cooldown)
- **Mouse:** aim
- **Left-click / J:** basic attack
- **Q / right-click:** skill
- **E / Space:** Domain (100 CE)
- **Escape:** settings

The settings menu includes auto-strike, Performance / Balanced / High graphics, bloom and soft glow, lens flares, motion trails, screen shake, hit flashes, damage numbers, particles, background detail, and master volume. Preferences save locally in the browser. Auto-strike repeats the basic attack; Black Flash still depends on the timing ring.

## Bosses and dialogue

Jogo uses meteor marks, flame fans and eruptions; Hanami creates root lattices, seed bursts and bloom zones; Mahito uses soul fans, transfiguration marks and pinwheel bursts; Sukuna uses rapid Dismantle volleys, cross-cleaves, Shrine slash zones, World-Cut lanes and an execution grid. Jogo, Hanami and Mahito also gain new signature patterns. Every boss enters a 30-second, invulnerable Last Stand when reduced to 20% HP. During this phase, player attacks cannot damage the boss and its attack patterns become faster and more aggressive; survive the timer, then finish the fight. Each boss has unique Last Stand dialogue. Each boss has intro dialogue, health-threshold taunts, and domain dialogue.

Between bosses, each player chooses one of three perks. Clear all four bosses to win.

## Multiplayer and performance

The host remains authoritative. Clients send inputs at about 30 Hz; the host broadcasts snapshots at about 20 Hz. To reduce lag on congested connections, the host drops stale snapshots when a data channel's send queue grows instead of letting old states pile up. Active projectiles, warning zones and transient effects are capped, and snapshots use compact arrays for projectile and zone data. Graphics controls are client-local, so lowering effects does not change the shared simulation. Dash input and dash direction are host-authoritative and included in snapshots.

Signalling uses the free PeerJS cloud broker and gameplay uses WebRTC data channels. Strict school/corporate Wi-Fi or NAT rules can still block peer connections; the game cannot bypass those network restrictions without a reachable TURN relay.

## Deploy on GitHub Pages

Push `index.html` to a repository, then enable GitHub Pages from the repository settings. Share the page URL; the host can use **COPY LINK** in the lobby.

## Developer build and smoke test

```sh
cd dev
npm install
npm run build
npm test
```

The editable source is `dev/src/game.html`; `build.js` inserts the PeerJS browser bundle into `pkg/index.html`.
