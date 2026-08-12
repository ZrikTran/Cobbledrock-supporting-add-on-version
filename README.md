| Pack | Role |
|---|---|
| `CobbleDrock-Core-1.2.2.mcaddon` | Core gameplay (required) |
| `CobbleDrock-Content-1.2.2.mcaddon` | Pokemon content (required) |
| `CobbleDrock-Legendary-Spawns-1.0.0.mcaddon` | Special Legendaries (rare, 20–30 min) |
| `CobbleDrock-Wild-Legendary-Spawns-1.0.0.mcaddon` | Popular Legendaries (12–18 min) |
| `CobbleDrock-Spawn-Alerts-1.0.0.mcaddon` | CSA-style server alerts (recommended) |

---

## 1. What's new / updated

**`CobbleDrock-Legendary-Spawns-1.0.0` (rebuilt)**
- Dependency bumped from Core **1.2.1 → 1.2.2** (the old build would not load with the current Core).
- Now honors the shared **"only one Legendary in the world at a time"** rule: before spawning it scans all 3 dimensions for any entity tagged `lota:legendary_spawn` (from any pack) and refuses if one is out.
- Removed 6 dead table entries (`uxie`, `mesprit`, `azelf`, `dialga`, `palkia`, `giratina`) that have **no entity in Core 1.2.2** — those spawn attempts used to fail silently and waste spawn slots. Effective table: **31 species**.

**`CobbleDrock-Wild-Legendary-Spawns-1.0.0` (new)**
- Spawns **21 popular/common Legendaries** out in the wild, ~**12–18 minutes** apart.
- The ultra-rares / Mythicals (Mew, Celebi, Jirachi, Deoxys, Phione, Manaphy, Darkrai, Shaymin, Arceus, Victini, Keldeo, Meloetta, Genesect, Diancie, Hoopa, Volcanion, Regigigas, Xerneas, Yveltal, Zygarde…) are **deliberately excluded — reserved for a future update**.
- Does **not** announce anything itself — it only tags spawns (`lota:legendary_spawn` + `lota:spawn_cap_exempt`) so **Spawn Alerts** broadcasts the full CSA-style alert (including capture / defeat / despawn).
- Declares a hard dependency on Core 1.2.2 **and** Legendary Spawns 1.0.0.

**`CobbleDrock-Spawn-Alerts-1.0.0` (new)**
- Bedrock port of the Java *Cobblemon Spawn Alerts 1.13.2* mod: server-wide notifications for Legendary / Mythical / Ultra Beast / Paradox / Rare / Shiny spawns with name, dex #, level, IVs, nature, ability, coordinates, biome and nearest player, plus a sound.
- Also announces when a tracked Pokemon is captured ("was captured by X"), defeated, or despawns.
- Configurable in-game (see `lota:alerts_config` below).

---

## 2. Where Pokemon spawn

### 2a. Regular wild Pokemon (Core)
Wild Pokemon spawn naturally via the Core's Cobblemon-derived spawn data, in the biomes and conditions defined per species, **16–64 blocks from players**, with rarity buckets:

| Bucket | Weight (≈ %) |
|---|---|
| Common | 88.5 |
| Uncommon | 10 |
| Rare | 1.2 |
| Ultra-rare | 0.3 |

Plus `pokemonPerChunk: 1`, despawn at 32–96 blocks, shiny rate **1/4096**.

### 2b. Popular Legendaries — `Wild Legendary Spawns` (21 species, ~12–18 min)

Placement: **ground** = on solid terrain · **surface** = on top of water/terrain · **sky** = high in the air.

| Pokemon | Dimension | Biomes | Placement |
|---|---|---|---|
| Articuno | Overworld | Icy (ice plains, snow taiga, frozen peaks, snowy slopes…) | ground |
| Zapdos | Overworld | Peaks (jagged/frozen/stony peaks, extreme hills) | ground |
| Moltres | Nether | Hell / basalt deltas / crimson forest | ground |
| Mewtwo | Overworld | Caves (lush/dripstone/deep dark) | ground |
| Entei | Overworld | Badlands + savannas | ground |
| Lugia | Overworld | Deep oceans | surface |
| Ho-Oh | Overworld | Peaks | sky |
| Regirock | Overworld | Deserts + badlands + stone beach | ground |
| Regice | Overworld | Icy | ground |
| Registeel | Overworld | Dripstone caves / deep dark / extreme hills | ground |
| Latias | Overworld | Flower forest / forest / birch forest | ground |
| Latios | Overworld | Flower forest / forest / birch forest | ground |
| Kyogre | Overworld | Deep oceans | surface |
| Groudon | Overworld | Deserts + badlands | ground |
| Rayquaza | Overworld | Peaks | sky |
| Reshiram | Overworld | Badlands + deserts | ground |
| Zekrom | Overworld | Peaks + roofed forest | ground |
| Kyurem | Overworld | Icy | ground |
| Tornadus | Overworld | Plains + savannas + hills | sky |
| Thundurus | Overworld | Plains + savannas + jagged peaks | sky |
| Landorus | Overworld | Plains + savannas + deserts | ground |

### 2c. Special Legendaries — `Legendary Spawns` (31 species, ~20–30 min)

| Pokemon | Dimension | Biomes | Placement |
|---|---|---|---|
| Articuno | Overworld | Icy | ground |
| Zapdos | Overworld | Peaks | ground |
| Moltres | Nether | Hot nether | ground |
| Mewtwo | Overworld | Caves | ground |
| Mew | Overworld | Jungles | ground |
| Entei | Overworld | Badlands + savannas | ground |
| Lugia | Overworld | Deep oceans | surface |
| Ho-Oh | Overworld | Peaks | sky |
| Regirock | Overworld | Deserts + badlands + stone beach | ground |
| Regice | Overworld | Icy | ground |
| Registeel | Overworld | Dripstone / deep dark / extreme hills | ground |
| Regigigas | Overworld | Ice spikes / ice mountains / snowy slopes | ground |
| Latias / Latios | Overworld | Flower forest / forest / birch forest | ground |
| Kyogre | Overworld | Deep oceans | surface |
| Groudon | Overworld | Deserts + badlands | ground |
| Rayquaza | Overworld | Peaks | sky |
| Deoxys | The End | The End | ground |
| Darkrai | Overworld | Dark woods (roofed forest, deep dark…) | ground · **night only** |
| Arceus | The End | The End | sky |
| Reshiram | Overworld | Badlands + deserts | ground |
| Zekrom | Overworld | Peaks + roofed forest | ground |
| Kyurem | Overworld | Icy | ground |
| Victini | Overworld | Plains | ground |
| Tornadus / Thundurus | Overworld | Plains + savannas (+ peaks) | sky |
| Landorus | Overworld | Plains + savannas + deserts | ground |
| Keldeo | Overworld | River / swamp / mangrove / beach | ground |
| Meloetta | Overworld | Flower forest / birch forest | ground |
| Genesect | Overworld | Caves | ground |
| Shaymin | Overworld | Flower forest / meadow / cherry grove | ground |

> **One at a time:** only **one** Legendary (from either pack) exists in the whole world at any moment — the shared `lota:legendary_spawn` check enforces it. If a Legendary is already out, the other pack waits and retries.

---

## 3. Spawn rates & how to check

### Rate settings

| Setting | Wild Legendary Spawns | Legendary Spawns |
|---|---|---|
| Spawn interval | 15 min ± 3 min (12–18) | 25 min ± 5 min (20–30) |
| Lifetime before leaving | 15 min | 20 min |
| Retry when no spot found | 30 s | 60 s |
| Distance from player | 40–80 blocks | 48–96 blocks |
| Level range | 50–65 | 55–70 |
| Guaranteed perfect IVs | 2 | 3 |

### In-game rate checks (operator commands)

| Command | Shows |
|---|---|
| `/scriptevent lota:wild_status` | Popular Legendary status + ETA of next roll + how many Legendaries are currently in the world |
| `/scriptevent lota:legendary_status` | Special Legendary status + ETA |
| `/scriptevent lota:alerts_status` | Alerts config summary (enabled tiers, sound, cooldowns) |
| `/scriptevent lota:wild_spawn` / `lota:legendary_spawn` | Force an immediate spawn attempt (must be in a matching biome) |
| `/scriptevent lota:alerts_test` | Send a test alert to every player |


*** : Addons Cobblebrock by Lota882
