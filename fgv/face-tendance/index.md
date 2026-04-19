# FGV - FaceTendance

## 🧭 Overview

Below is the data I've collected regarding the project so far.

## Borrowed Workers

To handle the case of borrowed workers.
The device shall download workers from a new table called

### estate_workers_master_data

| Column Name          | Data Type | Notes                                           |
| :------------------- | :-------- | :---------------------------------------------- |
| `original_estate_id` | String    | Original estate ID for attendance submission.   |
| `working_estate_id`  | String    | Current estate ID where the worker is assigned. |
| `worker_id`          | String    | Unique identifier for the worker.               |
| `worker_name`        | String    | Full name of the worker.                        |
| `supervisor_id`      | String    | Identifier for the worker's supervisor.         |

This way the device can download based on `working_estate_id`, so it will get all the workers present.\
`original_estate_id` is still needed because that's the id that will be used for attendance.

## 📸 Worker Biometrics

A new table `worker_biometrics` will be created

| Column Name              | Data Type   | Notes                                        |
| :----------------------- | :---------- | :------------------------------------------- |
| `worker_id`              | String      | Identifier for the worker.                   |
| `image`                  | Binary/Blob | Stores the worker's image.                   |
| `image_updated`          | Timestamp   | Timestamp of the last image update.          |
| `embedding_int8`         | Binary/Blob | Stores the face embedding in INT8 format.    |
| `embedding_int8_updated` | Timestamp   | Timestamp of the last INT8 embedding update. |
| `embedding_fp8`          | Binary/Blob | Stores the face embedding in FP8 format.     |
| `embedding_fp8_updated`  | Timestamp   | Timestamp of the last FP8 embedding update.  |

## 🗄️ Other Tables

| Name   | Description               | Download 📥 | Upload 📤 |
| :----- | :------------------------ | :---------: | :-------: |
| `cotw` | Estate                    |     ✅      |    ❌     |
| `htsm` | Supervisor                |     ✅      |    ❌     |
| `htsd` | Supervisor-Worker Mapping |     ❌      |    ❌     |
| `htam` | Attendance Header         |     ❌      |    ❌     |
| `htad` | Attendance Detail         |     ❌      |    ✅     |
| `padj` | Overtime                  |     ❌      |    ❌     |

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
`htam_supervisor_id` + `htam_year` + zero_padd_2(`htam_period`)\
`htam_period` varchar(2) is month

### htad (Attendance Detail)

This is the main attendance table that we:\

- download data from
- and upload data to.

## ⚙️ Database Naming Convention

Currently each estate has their own database named as `ermlprod*r530_est*[####]` ending with a 4 digit estate code in the end.

## 🔗 Links

- [Daily Flow](./daily-flow.md)
- [OpenAPI](./openapi)
