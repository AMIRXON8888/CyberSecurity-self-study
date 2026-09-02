# Bandit Level 19 — SUID and SGID

## What I learned

### SUID

Normally, when a user executes a program, the program runs with that user's privileges.

However, a program with the **SUID (Set User ID)** permission can run with the privileges of the program's owner.

In this level, the `bandit20-do` program had the SUID permission and was owned by `bandit20`. This allowed me to execute a command with `bandit20`'s privileges.

### `id`

I used the `id` command to check information about my current user, including my **user ID (UID)** and **group ID (GID)**.

In this level, running `id` showed information about my identity as `bandit19`.

### Real UID and Effective UID

A process can have different user identities:

* **Real UID** — the user who started the process.
* **Effective UID** — the user identity whose permissions the process is currently using.

SUID allows a program to use the effective privileges of the executable's owner.

### SGID

**SGID (Set Group ID)** works similarly to SUID, but with groups instead of users.

* **SUID** → affects the effective user identity.
* **SGID** → affects the effective group identity.

### Main takeaway

A program does not always run with the same privileges as the user who started it. Special permissions such as **SUID** and **SGID** can allow a program to run with a different effective user or group identity.

This is important for Linux security because programs with special permissions can access resources that the user running them would not normally be able to access.
