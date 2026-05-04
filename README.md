# repojump

Fish plugin to open the current git repository in your browser.

It detects the git remote, builds the repository URL, and opens common pages like pull requests, merge requests, and issues.

## Installation

### With Fisher

```fish
fisher install luisalcarasr/repojump
```

### Manual Installation

Clone the repository:

```fish
git clone git@github.com:luisalcarasr/repojump.git
cd repojump
```

Copy the function and completions into your fish config:

```fish
cp functions/rj.fish ~/.config/fish/functions/
cp completions/rj.fish ~/.config/fish/completions/
```

Reload fish or open a new terminal.

```fish
exec fish
```

## Usage

```fish
rj
```

Opens the repository home page.

```fish
rj pr
rj mr
```

Opens the pull requests page on GitHub or the merge requests page on GitLab. `pr` and `mr` are equivalent and behave according to the detected provider.

```fish
rj issues
```

Opens the issues page.

## Supported Commands

| Command | GitHub | GitLab |
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

You can also pass any path that is not explicitly supported:

```fish
rj milestones
```

This opens `<repo-url>/milestones`.

## Options

### Use Another Remote

By default, it uses `origin`.

```fish
rj --remote upstream
rj -r upstream issues
```

### Force Provider

You can force the provider when automatic detection is not enough, for example on self-hosted instances.

```fish
rj --provider gitlab mr
rj -p github pr
```

Supported providers:

- `github`
- `gitlab`

## Supported Remote Formats

- `git@github.com:owner/repo.git`
- `https://github.com/owner/repo.git`
- `ssh://git@gitlab.com/owner/repo.git`
- `git://github.com/owner/repo.git`

## Author

Luis Alcaras

## License

GPL-3.0
