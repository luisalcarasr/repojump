# repojump

Plugin de fish para abrir en el navegador la pagina del repositorio git del directorio actual.

Detecta el remote de git, construye la URL del repositorio y abre rutas comunes como pull requests, merge requests e issues.

## Instalacion

### Con Fisher

```fish
fisher install l.alcaras/repojump
```

### Instalacion manual

```fish
cp functions/rj.fish ~/.config/fish/functions/
cp completions/rj.fish ~/.config/fish/completions/
```

Despues de la instalacion manual, recarga fish o abre una nueva terminal.

## Uso

```fish
rj
```

Abre la pagina principal del repositorio.

```fish
rj pr
rj mr
```

Abren la pagina de pull requests en GitHub o merge requests en GitLab. `pr` y `mr` son equivalentes y actuan segun el proveedor detectado.

```fish
rj issues
```

Abre la pagina de issues.

## Comandos soportados

| Comando | GitHub | GitLab |
| --- | --- | --- |
| `rj` | Repo home | Repo home |
| `rj pr` | `/pulls` | `/-/merge_requests` |
| `rj mr` | `/pulls` | `/-/merge_requests` |
| `rj issues` | `/issues` | `/-/issues` |
| `rj ci` | `/actions` | `/-/pipelines` |
| `rj releases` | `/releases` | `/-/releases` |
| `rj tags` | `/tags` | `/-/tags` |
| `rj wiki` | `/wiki` | `/-/wikis` |
| `rj branches` | `/branches` | `/-/branches` |
| `rj commits` | `/commits` | `/-/commits` |
| `rj settings` | `/settings` | `/-/settings/general` |

Tambien puedes pasar cualquier ruta no soportada explicitamente:

```fish
rj milestones
```

Esto abre `<repo-url>/milestones`.

## Opciones

### Usar otro remote

Por defecto usa `origin`.

```fish
rj --remote upstream
rj -r upstream issues
```

### Forzar proveedor

Puedes forzar el proveedor cuando la deteccion automatica no sea suficiente, por ejemplo en instancias self-hosted.

```fish
rj --provider gitlab mr
rj -p github pr
```

Proveedores soportados:

- `github`
- `gitlab`

Tambien puedes configurar un proveedor por defecto para remotes no detectados:

```fish
set -U GTB_PROVIDER gitlab
```

## Formatos de remote soportados

- `git@github.com:owner/repo.git`
- `https://github.com/owner/repo.git`
- `ssh://git@gitlab.com/owner/repo.git`
- `git://github.com/owner/repo.git`

## Author

Luis Alcaras

## License

GPL-3.0
