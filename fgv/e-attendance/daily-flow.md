# Daily Flow

## Day Start

### Data Download

User downloads data as follows:

#### Login based on Supervisor Credentials

**Download**

#### Estate

- id
- name
- rest1
- rest2
- overtime

#### Based on Estate

- Supervisors
- Workers

#### Based on Worker (Need to create a new table to store these, or store on file system?)

- Photos
- Attendance Records
- Face Embeddings

### Recording Attendance

- Supervisor takes photo.
- Based on matched worker id, clock-in is stored for that day.

### Sync

User can manually sync data by selecting an option in the app.
? Is the additional data added before sync ?

#### Have to add (When to sync this information?)

1. Clock In & Clock Out for Rest 1
2. ⁠clock In & Clock Out for Rest 2
3. Also OT column

htsm_supervisor_id
htsm_supervisor_name

htsd_worker_id,
htsd_worker_name
htsd_worker_type
htsd_supervisor_id
