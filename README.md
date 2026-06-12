# sperre-marketplace

Internt Claude Code-marketplace for Sperre Air Power AS.

Inneholder kun **offentlige, eksterne** plugins som er gjennomgått og godkjent for
intern bruk. Ingenting Sperre-spesifikt ligger her.

## Plugins

| Plugin | Versjon | Kilde | Lisens |
|--------|---------|-------|--------|
| superpowers | 5.1.0 | https://github.com/obra/superpowers | MIT |

## Pinning

Hver plugin er en **frosset, vendored kopi** under `plugins/`. Marketplace peker
til lokal sti (`source`), ikke til GitHub. Godkjenning gjelder den versjonen som
ligger her — oppgradering krever ny gjennomgang og at versjonen bumpes i
`.claude-plugin/marketplace.json`.

## Avvik fra upstream superpowers

Følgende ble bevisst utelatt fra den vendrede kopien:

- `skills/brainstorming/` — krever Node.js (lokal webserver). Utelatt pga.
  Sperre-policy «kun Python».
- `skills/writing-skills/render-graphs.js` — Node.js-hjelper. Utelatt (samme grunn).
- `scripts/`, `tests/`, `docs/` — vedlikeholder-/utviklertooling, ikke brukervendt.
- Plattform-manifester for andre verktøy (`.opencode/`, `.codex-plugin/`,
  `.cursor-plugin/`, `gemini-extension.json` m.fl.).
- Upstream sin egen `marketplace.json` (ville gitt en marketplace inni en marketplace).

> Merk: `hooks/` er beholdt. Plugin-en kjører en `SessionStart`-hook automatisk
> ved hver oppstart (leser skill-innhold og injiserer kontekst). Den endres ikke
> uten ny gjennomgang.
