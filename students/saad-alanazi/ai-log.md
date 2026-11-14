# AI log — complete with your actual prompts

## AI-assisted work so far
- User request: "Help me doing this assignment step by step" (November 14, 2026)
- User provided a revised Open-Meteo CSV for the Minneapolis area.

## Error caught and how it was checked
- The CSV contains two separate tables (hourly weather followed by daily summaries). Treating the entire file as one hourly table would incorrectly mix daily-summary numbers into the weather fields.
- Checked the raw CSV headers and dates; extracted exactly 360 hourly records from October 29 through November 12, 2026 and excluded the daily-summary table from the working CSV.
- The first uploaded weather export was for Berlin; the replacement uses coordinates near Minneapolis. Verified from the metadata in the uploaded CSV.

## Prompts used subsequently
Add each exact prompt you send to any LLM, and record responses that needed correction. Do not claim you checked something you did not actually check.
