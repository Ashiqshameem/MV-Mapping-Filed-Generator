# GDM–MV Mapping Field Generator

A small web page that creates new mapping rows (like OPEN, HIGH, LOW) for a symbol, using a row the symbol already has (usually CLOSE).

## When to use it

Use it when a client asks for a field that a symbol doesn't have in the mapping file yet.

**Example:** The client wants OPEN, HIGH and LOW for a symbol, but the file only has CLOSE for it. Instead of copying the CLOSE row by hand and editing it three times, paste the CLOSE row here and the tool creates the three new rows for you.

## What it changes

Only two things change in each new row:

| Column | CLOSE row | New HIGH row |
|---|---|---|
| FIELD | `CLOSE` | `HIGH` |
| MODEL URI | `.../EU.EL.BE.ICE.FIN.B.FUT.Y00/SETTLE` | `.../EU.EL.BE.ICE.FIN.B.FUT.Y00/HIGH` |

Everything else (ENI, BKW, symbol, NAME, DESCRIPTION, calendars, unit, currency and so on) is copied exactly.

## How to use it

1. **Paste the rows.** Copy the full row for the symbol from Excel (all columns, from ENI to the last one) and paste it in. The header row is optional. You can paste several symbols at once. Then click **Read rows**.
2. **Pick the fields.** Click the fields you need, for example OPEN, HIGH and LOW. Use **Select all** if you want every field.
3. **Check the URI endings.** The tool fills in the right ending for each field. You can change it if needed. If you see a yellow warning, check with the GDM team that the column exists before sending the rows to the client.
4. **Export.** Click **Copy for Excel** and paste into the mapping file, or click **Download CSV**.

## Good to know

- **The CLOSE row is used as the base.** If a symbol has no CLOSE row in your paste, the first row is used instead.
- **Fields the symbol already has are skipped,** so you don't create duplicates.
- **Some templates use different endings.** For example, the HE_ assessment templates use ASK for HIGH and BID for LOW. The tool handles this automatically.
- **A yellow warning means "check first".** It shows when no symbol of that template has the field in the current mapping files, so the column may not exist in GDM.
- **Your data stays on your computer.** The page runs fully in your browser and does not send it anywhere.

