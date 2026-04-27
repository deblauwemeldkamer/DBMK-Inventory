# DBMK-Inventory v1.0.0
### NL + EN GitHub Readme

---

## Nederlands

DBMK-Inventory is een modern, veilig inventory systeem voor FiveM ESX Legacy.  
Deze versie (`v1.0.0`) is gebouwd als server-authoritative core met focus op stabiliteit, anti-duplication en gebruiksvriendelijke NUI.

![Police Armory Preview](https://i.imgur.com/Bl210ZP.png)

### Features

- Server-side gevalideerde inventory acties (move/use/drop)
- Drag & drop NUI met hotbar (1-4)
- World drops (item op grond leggen en oppakken)
- Gewicht + slot limieten
- MySQL persistent storage (`oxmysql`)
- ESX bridge met write-through parity
- 3 themes: `emerald`, `graphite`, `gold`
- 10 talen: `en, nl, de, fr, es, it, pt, pl, tr, ro`
- Notify adapters (incl. `DBMK-NotifySystem`)
- Rich Discord webhook logs (avatar, banner, colors, metadata)

### Hoe werkt het systeem?

1. Client stuurt alleen intentie (bijv. “move item van slot A naar B”).
2. Server valideert alles (item, stack, weight, versie).
3. Server slaat op in database en stuurt nieuwe state terug.
4. NUI rendert de nieuwe state met theme + locale.

### Wat moet jij zelf doen in config?

In `shared/config.lua` minimaal:

```lua
Config.OpenKey = 'I'
Config.Theme = 'emerald' -- emerald | graphite | gold
Config.Locale = 'en' -- en, nl, de, fr, es, it, pt, pl, tr, ro
```

Voor stabiele ESX sync:

```lua
Config.EsxBridge.ImportOnFirstSeen = false
Config.EsxBridge.WriteThrough = true
Config.EsxBridge.WriteThroughAdd = true
Config.EsxBridge.WriteThroughRemove = true
```

Voor DBMK notify:

```lua
Config.Notify.Provider = 'dbmk'
```

Voor webhooks:

```lua
Config.Webhooks.Enabled = true
Config.Webhooks.Url = 'https://discord.com/api/webhooks/...'
```

### Installatie (kort)

1. SQL importeren: `sql/dbmk_inventory.sql`
2. Resources starten in juiste volgorde:
   - `oxmysql`, `es_extended`, `ox_lib`
   - optioneel `DBMK-NotifySystem`
   - `DBMK-Inventory`

---

## English

DBMK-Inventory is a modern and secure inventory system for FiveM ESX Legacy.  
This release (`v1.0.0`) is designed as a server-authoritative core focused on anti-duplication, reliability, and clean NUI UX.

### Features

- Server-validated inventory actions (move/use/drop)
- Drag & drop NUI with hotbar (1-4)
- World drops (drop item on ground and pick up)
- Weight + slot limits
- MySQL persistence (`oxmysql`)
- ESX bridge with write-through parity
- 3 themes: `emerald`, `graphite`, `gold`
- 10 languages: `en, nl, de, fr, es, it, pt, pl, tr, ro`
- Notify adapters (including `DBMK-NotifySystem`)
- Rich Discord webhook logs (avatar, banner, colors, metadata)

### How the system works

1. Client sends intent only (for example: move item from slot A to B).
2. Server validates everything (item, stack rules, weight, version).
3. Server persists state and returns updated payload.
4. NUI renders updated state using selected theme + locale.

### What users must configure

In `shared/config.lua` (minimum):

```lua
Config.OpenKey = 'I'
Config.Theme = 'emerald' -- emerald | graphite | gold
Config.Locale = 'en' -- en, nl, de, fr, es, it, pt, pl, tr, ro
```

For restart-safe ESX sync:

```lua
Config.EsxBridge.ImportOnFirstSeen = false
Config.EsxBridge.WriteThrough = true
Config.EsxBridge.WriteThroughAdd = true
Config.EsxBridge.WriteThroughRemove = true
```

For DBMK notifications:

```lua
Config.Notify.Provider = 'dbmk'
```

For webhooks:

```lua
Config.Webhooks.Enabled = true
Config.Webhooks.Url = 'https://discord.com/api/webhooks/...'
```

### Quick install

1. Import SQL: `sql/dbmk_inventory.sql`
2. Start resources in correct order:
   - `oxmysql`, `es_extended`, `ox_lib`
   - optional `DBMK-NotifySystem`
   - `DBMK-Inventory`

---

## Version

- Project: **DBMK-Inventory v1.0.0**
- UI watermark version: configurable with `Config.UiVersion`
