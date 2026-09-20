# HARDBURN

**You launch a missile. Then you have to fly it.**

A physics time-attack in a single HTML file. Hold the motor and it burns; let go and
you're a dart with gravity attached. The mouse sets your aim, WASD swings the airframe
off that line so you can burn sideways out of a corner, and a nose-fired grapple carves
the turns you can't. Score is style — threaded gates, shaved walls, G-load, swings — and
only beating your own best banks anything. Spend it on crates. Rare airframes change the
geometry you fly; the rarest carry a sixth system all their own.

## Running it

Double-click `hardburn.html`. That's it — no build, no server, no install. Progress saves
to `localStorage`, so it persists per browser.

The only thing it fetches is the two typefaces from Google Fonts. Offline it falls back to
Arial Narrow / Consolas and looks noticeably cheaper, but plays identically.

## Controls

| Key | Action |
| --- | --- |
| `SPACE` | Launch off the rail — then **hold** for thrust. The motor only runs while you do. |
| `MOUSE` | Aim. Screen-relative, no roll to untangle. This is also your grapple line. |
| `WASD` | Rotate the airframe relative to your aim. It stays where you put it. |
| `CTRL` *(or `X`)* | Snap the airframe back to the aim line. Tap to align, hold to pin. |
| `SHIFT` / `RMB` | Hard burn. Burns fuel. |
| `E` / `LMB` | Grapple — fires from the nose down the aim line. Hold to swing. |
| `C` | Drag chute. |
| `F` | Time dilation. Costs you real clock. |
| `Q` | Skin ability (Epic airframes and up). |
| `R` / `ESC` | Restart run / abort. |

> **Heads up:** `CTRL`+`W` closes the browser tab and no page can block it. If you catch
> yourself doing that while aligning, use `X` instead — it's bound to the same action.

## Three directions, and the gaps between them

This is the whole game:

- **Aim** — where the mouse points. The white bracket.
- **Airframe** — where the nose points, which is where thrust goes. WASD moves it.
- **Flight path** — where you're *actually* going. The cyan circle, which turns amber
  when it stops agreeing with your aim.

Swing the nose 90° off your flight path and you can thrust sideways out of a corner.
Swing it all the way round and you retro-burn while still looking where you're going.

## Scoring

| | |
| --- | --- |
| **THREAD** | Pass a gate near its centre. Dead centre at speed pays double. |
| **SKIM** | Fly within 8 m of a surface. The multiplier climbs while you hold it. |
| **G-LOAD** | Hard turns load the airframe and pay while loaded. |
| **SWING** | Hook a surface and carve round it. Pays on release, scaled by arc. |
| **KILL** | Hit the target. Remaining time converts to points. |

**Banking:** only the *improvement over your personal best* on that course banks at full
rate. Re-flying a course you've already beaten pays a fraction. Grinding isn't a strategy;
flying better is.

## Courses

Seeded and generated — type any word and you get that course, forever, identically. The
same seed builds the same course on any machine, so seeds are shareable.

Routes are built from named features rather than random drift, so the tools actually get
asked for: **hairpins** turn harder than the airframe manages at speed (that's what the
grapple masts are for), **chicanes** flick back the other way and punish anyone still at
300, **fields** are slaloms, **straights** are where the burn pays.

Four difficulties — `MILK RUN` (9 gates, wide) through `STANDARD`, `TIGHT`, and
`SUICIDAL` (18 gates, 22 m apertures, triple structure density and a 2.6× payout).

## Airframes

23 of them across six rarities, pulled from crates with credits.

| Rarity | Odds | What actually changes |
| --- | --- | --- |
| Common | 52% | Paint and stencils |
| Uncommon | 27% | Livery, small handling bias |
| Rare | 13% | **Real geometry** — length, calibre, nose, fins, canards, pods — plus emissive trim |
| Epic | 6% | Geometry + VFX + **a sixth system on `Q`** |
| Legendary | 1.8% | Rewind, Singularity, Nova Lance |
| Mythic | 0.2% | Event Horizon, Ascension |

From Rare up the airframe is genuinely rebuilt, not recoloured — HALOGEN is a 9 m dart
that turns badly, KINGFISHER has oversized surfaces and turns 24% harder, IRONCLAD carries
strap-on boosters and an extra hull. The hangar preview is the mesh that launches.

Crates cost 100 CR (900 for a ten-pack). Duplicates render down to scrap, and 600 scrap
forges a guaranteed Epic or better. Pity guarantees Epic+ at 40 pulls and Legendary+ at 150.

Abilities are free and pre-equipped — the crates are what you spend on.

## Design note

The world is bone-on-ink monochrome and saturated colour belongs only to your missile, its
exhaust and its VFX. Rarity is literally how much colour is on your screen, so a Mythic
airframe is unmistakable from across the room.

Rendered with a hand-rolled software 3D pipeline on Canvas2D — painter-sorted filled
polygons with inked edges, because the direction is technical plates, not lit surfaces.
Exhaust and VFX use real additive compositing on a separate pass.

## Credit

The concept is lifted from **[Dumbfire](https://store.steampowered.com/app/4944600/Dumbfire/)**
by TitanGameDev — an unguided missile, style scoring, and a control scheme where the mouse
aims and the body rotates independently. This is an independent single-file take on that
idea, with seeded generation in place of a level editor and a collection layer on top.
