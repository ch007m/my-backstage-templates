# My backstage templates

- Gitea: To create a gitea repository (public or private) on "gitea.localtest.me:3333"
- Dummy: simple template to test fields and debug

## How to use them

Add to your `addp-config.local.yaml` file the location pointing to this repo

```yaml
integrations:
  gitea:
    - host: gitea.localtest.me:3333
      username: "gitea_admin"
      password: "gitea_admin"

catalog:
  import:
    entityFilename: catalog-info.yaml
  rules:
    - allow: [Component,System,API,Resource,Location,Template,Group,User]
  locations:
    # Gitea scaffold template example
    - type: url
      target: ../../qshift/all.yaml
```