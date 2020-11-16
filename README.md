# Ansible Role: mssql

https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server?view=sql-server-ver15
https://docs.ansible.com/ansible/latest/collections/community/general/mssql_db_module.html

can't build image with molecule requires prebuild image

---

# Generelle Guidelines

## Branches

In den `master ` Branch wird nicht manuell gepusht. Der Master Branch soll stehts in einem deploybaren zustand sein (stable master). Im `develop` Branch oder in dezidierten feature Branches findet Entwicklung statt.

## Tests

Gitlab Pipelines werden zum Testen verwendet. D.h. getestet wird, was in `.gitlab-ci.yml` definiert ist.

## Release

Um neue Features in den `master` Branch zu mergen, kann folgender git alias angelegt werden.

```
git config --global alias.release "push -o merge_request.create -o merge_request.target=master -o merge_request.merge
_when_pipeline_succeeds"
```

Dieser Alias kann anschließend wie folgt verwendet werden um einen Branch in `master` zu mergen, sofern die Gitlab Pipeline erfolgreich durchläuft.

```
git release origin <local-branch-name>
```

Weiter Informationen hierzu auf: https://docs.gitlab.com/ee/user/project/push_options.html