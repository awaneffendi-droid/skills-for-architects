# Output Formatting

These conventions govern how skill outputs are structured and presented.

## Tables

- Use tables for **all comparative data**: product comparisons, scenario analysis, code requirements, area breakdowns
- Include units in column headers, not in every cell: `Area (SF)` with values `1,250` — not `1,250 SF` in each row
- Right-align numeric columns; left-align text columns
- Always include a totals or summary row where applicable

## Headings

- Structure outputs with clear, hierarchical headings that match professional deliverable conventions
- Use descriptive headings, not generic ones: "Egress Requirements — Level 2" not "Section 3"
- Number headings only when the output is a specification or report with cross-references

## Source Attribution

- Cite the source for every data point that comes from an external database or API:
  - Statistics: "Sumber: BPS, Kecamatan [nama] Dalam Angka [tahun]"
  - Hazard data: "Sumber: BNPB, InaRISK, diakses [tanggal]"
  - Climate: "Sumber: BMKG, Stasiun [nama], data [periode]"
  - Zoning: "Sumber: Perda/Perkada [kabupaten/kota] Nomor [x] Tahun [y] tentang RDTR [kawasan], Lampiran [n]"
- Place sources at the end of each section or in a footnote — not inline in every sentence

## File Output

- When a skill writes a file, use descriptive filenames: `888-brannan-zoning-envelope.html` not `output.html`
- Default to markdown (`.md`) for text reports
- Use HTML only for interactive or visual outputs (3D viewers, slide decks, dashboards)
- Include a YAML front matter block in markdown reports with: title, date, address/subject, skill name

## Lists

- Use bulleted lists for unordered items (materials, features, observations)
- Use numbered lists only for sequential steps or ranked items
- Keep list items parallel in grammar: all start with a verb, or all start with a noun
