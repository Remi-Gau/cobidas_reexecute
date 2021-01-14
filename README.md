# Template repository to create an app based on repro schema + UI

This repository provides the basic environment and automation to set up an app
running the
[Reproschema user interface](https://github.com/ReproNim/reproschema-ui) and
with questionnaires encoded as a
[Reproschema](https://github.com/ReproNim/reproschema).

## Changes to make to get your app running

- [ ] Click `Use this template` to [create a new repository on your account](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template).

- [ ] Clone the newly created repository.

- [ ] Change the name of the `github` repository to `.github` to make sure that
      Github will recognize it as folder to look into and run some its Github
      actions (the continuous integration service runby Github).
- [ ] Add your `protocol_schema` file in the protocols folder.

- [ ] Make sure to modify `.github/workflows/build_deploy.yml`, so that the
      reproschema python package will run on the right protocol_schema. Look for
      something like the snippet of code below:

```yml
# IMPORTANT
# Modify the following line so that to replace
# protocols/FOLDER_NAME/SCHEMA_FILE_NAME
# with the actual path to your protocol schema
# Once you are done, remove these comment lines.
reproschema -l DEBUG validate protocols/FOLDER_NAME/SCHEMA_FILE_NAME
```

- [ ] You also need to modify `ui-changes/src/config.js` so that:
  - [ ] `assetsPublicPath` is the actual name of the repository you gave to
        repository when you use the template repository.
  - [ ] `githubSrc` points to the right protocol schema, otherwise the UI will
        not know where to look for the content. To do that, you should only to
        change this bit
        `user_name/repo_name/branch_name/protocols/schema_file_name.jsonld` in
        the following code.

```
  githubSrc: 'https://raw.githubusercontent.com/user_name/repo_name/branch_name/protocols/schema_file_name.jsonld',
  assetsPublicPath: '/reproschema_template/',
```

- [ ] copy the activity and items schema into the `activities` folder (if you
      want to host them into this repository).
