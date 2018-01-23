# Docker for local development
- This repo is for creating a development environment for working on the http://rhythmofrussian.lib.virginia.edu website (which is a clone of http://prosody.lib.virginia.edu)

## Create Environment and Files
- Make a directory for the local project
  - `mkdir project-folder`
  - `cd project-folder`
- Clone the rhythm-of-russian repository
  - This will download a copy of the docker-compose.yml and the database file.
- Clone plugins and theme
  - Clone the plugin folder
    - `git clone https://github.com/scholarslab/prosody_plugin.git prosody_plugin`
  - Clone the theme folder
    - `git clone https://github.com/scholarslab/prosody_theme.git prosody_theme`
  - Seravo wp-custom-bulk-actions
    - `git clone https://github.com/Seravo/wp-custom-bulk-actions.git custom-bulk-actions`


# Workflow for working on plugin and theme.
- Based off of the github-flow workflow, see http://scottchacon.com/2011/08/31/github-flow.html
- Github Flow
  - **master branch:** The main stable branch. All feature and work branches should be off of this branch, and merged back into this branch.
  - **production branch:** When a good stable release is achieved, merge from the main to production with a tag. Once pushed to GitHub, Travis CI will automatically push tagged branches to npm.js.
  - **working/feature branch:** When making changes or adding a feature, or fixing a bug, create a branch with a descriptive name off of the master branch. This is also pushed to GitHub and pushed to constantly. Any branch not master or production is something being worked on. When changes are done, submit a pull request. Others can add to a conversation about the changes, and any subsequent changes can be made before merging into master.


# Notes for initial setup
## Create the database.sql file
- Changes to the SQL dump from the production site.
  - Use a dump from the production when it only had two users, one poem, nothing else.
    - Delete all the SQL comments from the begining of the file, up to the create table (definitely the create database lines)
    - Delete all the SQLcomments from the end of the file
  - Take out all but one user from all tables
  - Change remaining user to 'adminuser'
  - Reset the password to 'admin pass' using http://www.passwordtool.hu/wordpress-password-hash-generator-v3-v4
  - Replace all the URLs with 'localhost'
  - Change the email address for 'adminuser' to 'adminuser@example.com' (2 places)
  - Change all default date stamps to be a valid date, from '0000-00-00 00:00:00' to '2001-01-01 01:01:01'
## Changes to docker-compose.yml from regular prosody to rhythm.
  - Change the volume names in the 'db:' service to 'rhythm'
    - and the corresponding line in the 'volumes:' section
  - Make sure the table prefix matches the table names from the SQL file
