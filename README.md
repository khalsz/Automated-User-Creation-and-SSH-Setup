# Automated User Creation and SSH Setup

This script automates the creation of new users from a CSV file, adds them to a specified group, sets their passwords, and configures their SSH access by setting up their `.ssh` directories and authorized keys. This can be particularly useful for managing user access in a server environment.

## Features

- Automatically checks for the existence of a group and creates it if it doesn't exist.
- Adds new users from a CSV file and sets their passwords.
- Configures SSH access for the new users by copying a pre-defined authorized keys file.
- Sets appropriate permissions and ownership for the `.ssh` directories and files.

## Requirements

- Bash shell
- `sudo` privileges

## Usage

1. **Prepare the CSV file**

   Create a CSV file (e.g., `name.csv`) with the usernames of the users you want to create, one username per line.

2. **Prepare the authorized keys file**

   Create an `authorized_key` file containing the public SSH keys that should be authorized for all new users.

3. **Set the script variables**

   Ensure the following variables are set correctly in the script:

   - `file_name`: Path to your CSV file containing the usernames.
   - `group`: Name of the group to which the users will be added.
   - `SSH_SKEL`: Path to the SSH skeleton directory.
   - `AUTH`: Path to the file containing the public SSH keys.
   - `PASSWORD`: Default password to be set for the new users.

4. **Run the script**

   Execute the script with `sudo` to ensure it has the necessary permissions:

   ```bash
   sudo ./your_script.sh