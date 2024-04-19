# My backstage templates

This is what you should do to use the templates of this project in your backstage application

Add to your `app-config.local.yaml` file the url pointing to this repo using the `catalog.locations` field:

```yaml
catalog:
  import:
    entityFilename: catalog-info.yaml
  rules:
    - allow: [Component,System,API,Resource,Location,Template,Group,User]
  locations:
    # My backstage templates
    - type: url
      target: https://github.com/ch007m/my-backstage-templates/blob/main/all.yaml
```

## Gitea template

Description: To create a gitea repository (public or private) on a [local](https://github.com/ch007m/my-gitea/tree/main) "gitea.localtest.me:3333" server.

Instructions:

- Have the gitea plugin `@backstage/plugin-scaffolder-backend-module-gitea` installed within the backend. See [README.md](https://github.com/backstage/backstage/blob/master/plugins/scaffolder-backend-module-gitea/README.md)
- Add the following integration to the `app-config.local.yaml` file
```yaml
integrations:
  gitea:
  - host: gitea.localtest.me:3333
    username: "gitea_admin"
    password: "gitea_admin"
```

## Dummy template

Description: Simple template to test fields and debug them using the action `debug:log`

```yaml
  steps:
    - id: debug
      name: debug
      action: debug:log
      input:
        message: ${{ parameters.myInput | base64 }}
```
