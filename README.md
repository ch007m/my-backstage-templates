# My backstage templates

This is what you should do to use the templates of this project in your backstage application:

Create (or use an existing) backstage application (>= 1.25):
```bash
npx @backstage/create-app
Need to install the following packages:
@backstage/create-app@0.5.14
Ok to proceed? (y) y
? Enter a name for the app [required] my-backstage
...
cd my-backstage
```

Add to your `app-config.local.yaml` file (or create it) the url pointing to this repo using the `catalog.locations` field:

```bash
cat <<EOF > app-config.local.yaml
# my-backstage local config
catalog:
  import:
    entityFilename: catalog-info.yaml
  rules:
    - allow: [Component,System,API,Resource,Location,Template,Group,User]
  locations:
    # My backstage templates
    - type: url
      target: https://github.com/ch007m/my-backstage-templates/blob/main/all.yaml
EOF
```
Launch backstage: `yarn dev`

## Gitea template

**Description**: To create a gitea repository (public or private) on a local `gitea.localtest.me:3333` server.

[**Template file**](./gitea/template.yaml)

**Instructions**:

- Have the gitea plugin `@backstage/plugin-scaffolder-backend-module-gitea` registered within your `packages/backend`. See the plugin page for more information [README.md](https://github.com/backstage/backstage/blob/master/plugins/scaffolder-backend-module-gitea/README.md)
- Install and run a [local](https://github.com/ch007m/my-gitea/tree/main) gitea server.
- Add the following `integrations` to the `app-config.local.yaml` file
```yaml
integrations:
  gitea:
  - host: gitea.localtest.me:3333
    username: "gitea_admin"
    password: "gitea_admin"
```

## Dummy template

**Description**: Simple template to test field and debug using the action `debug:log`

[**Template file**](./dummy/template.yaml)



```yaml
  steps:
    - id: debug
      name: debug
      action: debug:log
      input:
        message: ${{ parameters.myInput | base64 }}
```

## Template filter template

**Description**: Template to play with a `TemplateFilter` able to `base64` a template's field. 

**Remark**: This template will validate the doc that we will develop according to this ticket [24002](https://github.com/backstage/backstage/issues/24002) using such instructions: https://github.com/ch007m/backstage-backend-module?tab=readme-ov-file#howto-guide-backend-module-and-template-filter

[**Template file**](./templatefilter/template.yaml)

```yaml
  steps:
    - id: debug
      name: debug
      action: debug:log
      input:
        message: ${{ parameters.myInput | base64 }}
```
