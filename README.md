# Welcome to your new dataform project

## Are you the first person to deploy the code? Run these commands. If someone already initialized all the dataform repositories, then ignore this part

### [0] Initialize git

```shell
git init
```

### [1] Add files in your new local repository

```shell
git add .
```

### [2] Commit the files that were staged in your local repository

```shell
git commit -m "First commit of all dataform files"
```

### [3] Create a new repository on [GitHub](https://github.com/). Choose a repository name and ignore the intitialization of the README, license, or gitignore files to avoid errors. They can be added once the project is set up in GitHub. Copy the remote repository URL at the top of the Quick Setup page.

Go back to your terminal and replace `REMOTE-URL` with the copied remote repository's URL.
This `REMOTE-URL` looks like git@github.com:Rik-devoteam/data-foundation-factory-test.git for ssh authentication

```shell
git remote add origin REMOTE-URL
```

### [4] Verify the setup

```shell
git remote -v
```

### [5] Push the changes in your local repository to GitHub.com. If you want to rename your default branch, then replace "main" with that name

```shell
git push -u origin main
```

### [6] Make two new branches for development and acceptance

```shell
git branch dev
git branch uat
```

### [7] Push the other two local repository branches to GitHub.com

```shell
git checkout dev
git push -u origin dev
git checkout uat
git push -u origin uat
```

## Is your dataform project already set up? Here you can find more information on dataform

### Versioning of the secret in secret manager

It is crucial to regularly change the acces token of the remote dataform git repository. Follow the steps in [Dataform third-party Git repository](https://cloud.google.com/dataform/docs/connect-repository), to generate a private and public key. Once on the Google Cloud console, go to your project containing the secret. Go to the Secret Manager (Security) page, select the secret and add the new private key using the New Version option. Dataform will always use the latest version of the secret.


### A dataform repository contains the following types of files

Config files

- These files configure your Dataform project and contain Javascript dependences. The dataform.json, contains general information that Dataform uses to create new tables and views. Such as which schema should be used.
- In the package.json all the Javascript dependencies are found.

Definitions

- Definitions are SQLX and JavaScript files that define new tables, views, and additional SQL operations to run in BigQuery. These filesare organized according to their data stage.
- An SQLX file consists of a block and body. The body contains the SQL specific information. The block specifies the output of the script. Additionally it contains documentation and data quality tests.

Includes

- It contains JavaScript files where you can define variables and functions.

### The inital dataform files are configured using the "dev" branch. However at runtime, compilation overrides makes sure that each stage contains the branch specific parameters

### Developers can create workspaces within the 'dev' repository in Dataform, allowing them to experiment with and test new features. For each developer a different schema will be used to store created tables and views, within the same dataset in BigQuery
