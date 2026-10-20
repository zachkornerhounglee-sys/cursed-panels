# Design sheet

**Loop:** title screen > lobby and character selection > four boss fights > perk draft between bosses > victory / wipe > lobby.

**Presentation:** dark cursed arena with a restrained violet grid, character-coloured silhouettes, neon edge lighting, a lower-third dialogue plate, and reduced default flashes. Settings include Performance / Balanced / High graphics, auto-strike, screen shake, hit flash, floating damage numbers, particles, background detail and master volume.

**Boss identities:**
- **Jogo:** meteor marks, sweeping Ember Fan volleys and staggered eruptions.
- **Hanami:** Root Lattice hazard rows, Seed Burst patterns and Bloom zones.
- **Mahito:** Soul Fan projectiles, delayed Transfigure markers and Mirror Soul pinwheels.
- **Sukuna:** twin Dismantle volleys, Cross Cleave lanes and Shrine slash zones.

All bosses have unique intro dialogue and two health-threshold taunts; Mahito and Sukuna also announce their domains. Dialogue is part of the host snapshot, so co-op players see the same line at roughly the same time.

**Netcode:** host-authoritative WebRTC star; clients send inputs at about 30 Hz and snapshots are broadcast at about 20 Hz. Snapshot backpressure, projectile / warning-zone caps and bounded effect queues reduce bandwidth and stale-update buildup during congestion. Host authority means the shared game state remains consistent, but restrictive Wi-Fi/NAT settings can still prevent WebRTC connections.

**Domains:** one at a time. Casting into an active boss domain (or the boss casting into yours) starts a 4-second Domain Clash mash; the winner's domain takes over, the loser takes damage / stun.

| Character | LMB (primary) | Q (secondary) | E (Domain) |
|---|---|---|---|
| Itadori, Brawler | Black Flash Fist: dash strike, rhythm crits | Divergent Fist: dash + delayed second hit | Malevolent Vessel: sure-hit cleaves |
| Fushiguro, Summoner | Divine Dog: homing shikigami | Toad Decoy: boss aggro bait that bites | Chimera Shadow Garden: slows boss, sure-hit |
| Ieiri, Support | Ofuda Needle: fast seal | Reverse Technique: heal + revive nearby | Sanctum of Mending: boss stop, slow and regen field |
| Gojo, Glass Cannon | Blue: drags boss in | Hollow Purple: charged piercing blast | Unlimited Void: boss frozen, sure-hit; Infinity can auto-block shots |


## Neon domains and Last Stand
Domains render with layered neon barriers, rotating sigils, lens flares, and character-specific motifs. Every boss enters a 30-second invulnerable Last Stand at 20% HP; all players see the same timer and must dodge that boss’s accelerated, signature attack patterns. The boss becomes vulnerable again when the timer ends.
