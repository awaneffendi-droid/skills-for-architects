# /as:zoning-analysis-id

Analisis tata ruang untuk lahan di Indonesia: status kegiatan dalam RDTR/peraturan zonasi (matriks ITBX), KDB, KLB, KDH, KTB, GSB dan ketinggian, berdasarkan perda/perkada kabupaten/kota yang berlaku dan KRK untuk persil tersebut. The [source manifest](../../corpus/sources/catalog.json) guides retrieval; the repository carries no zoning rulebook or numerical control tables.

## Install

```bash
claude plugin marketplace add AlpacaLabsLLC/skills-for-architects
claude plugin install as@skills-for-architects
```

## Use

Invoke `/as:zoning-analysis-id` with an address (kelurahan, kecamatan, kabupaten/kota), coordinates or a supplied plot survey, plus the requested analysis. The skill resolves date/use/scope, retrieves the original perda/perkada and maps, verifies applicability and calculates only from established rules and plot inputs, in metres and square metres. Missing access, version evidence or geometry is reported explicitly, and unverified regulation references are marked *perlu verifikasi*.
