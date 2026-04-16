---
layout: simple
title: FGV
---

# FGV - FaceTendance

## Tables

| Name   | Description       | Download 📥 | Upload 📤 |
| :----- | :---------------- | :---------: | :-------: |
| `cotw` | Estate            |     ✅      |    ❌     |
| `htsm` | Supervisor        |     ✅      |    ❌     |
| `htsd` | Worker            |     ✅      |    ❌     |
| `htam` | Attendance Header |     ✅      |    ❌     |
| `htad` | Attendance Detail |     ✅      |    ✅     |
| `padj` | Overtime          |     ❌      |    ❌     |

### cotw (Estate)

Estate table has:

- work start/end
- rest1 start/end
- rest2 start/end
- overtime start/end

This we will download and upload back with each attendance record.

### htam (Attendance Header)

Record in `htam` is only created for a\
supervisor + month + year.\
`htam`.`htam_reference_no` = `htad`.`htad_reference_no`

01403226202602\
`01403226` + `2026` + `02`\
`htam_supervisor_id` + `htam_year` + `zero_padd_2(htam_period)`\
htam_period varchar(2) is month

### htad (Attendance Detail)

This is the main attendance table that we:\

- download data from
- and upload data to.

### padj (over-time)

## Links

- [Daily Flow](./daily-flow.md)
- [OpenAPI](./openapi)
