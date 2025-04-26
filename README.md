[简体中文](./README_HANS.md)

<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/31800695/138593031-536f9b8c-714c-4c4f-8725-63ea105fcca0.png">
  <h3 align="center">github-lang-box</h3>
  <p align="center">💻📌 Update a pinned gist to show your most used programming languages</p>
</p>

# github-lang-box
[![npm](https://img.shields.io/npm/v/github-activity-box.svg?style=flat-square)](https://www.npmjs.com/package/github-lang-box)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/maxchang3/github-lang-box/ci.yml?style=flat-square&label=CI)](https://github.com/maxchang3/github-lang-box/actions)
[![License](https://img.shields.io/github/license/maxchang3/github-lang-box?style=flat-square)](LICENSE)

A fork of [lang-stats-box](https://github.com/Aveek-Saha/lang-stats-box) with enhanced features:

- 🔑 Uses `/user/repos` endpoint to fetch all repositories (including private ones)
- 🎨 Supports custom descriptions, language exclusions, and repository filtering
- 📦 Published to npm with binary support for easy use via `npx` or `pnpx`
- ✅ Updated dependencies and completely rewritten in TypeScript

> **Note**: Since this package uses the `/user/repos` endpoint, Fine-grained access tokens must have the `metadata:read` permission.

## Usage

### Use as a CLI

```bash
# Run directly with npx/pnpx
npx github-lang-box [options]

# Or install globally
npm install -g github-lang-box
github-lang-box [options]
```

**Options:**
- `--dry` - Preview the output without updating the gist

**Required Environment Variables:**
| Variable     | Description                                                                                               |
| ------------ | --------------------------------------------------------------------------------------------------------- |
| GH_TOKEN     | GitHub access token with `gist` and `metadata:read` scopes                                                |
| GIST_ID      | The ID from your gist URL: <br> `https://gist.github.com/username/`**`8335e85451541072dd25fda601129f7d`** |
| GH_USERNAME  | Your GitHub username                                                                                      |
| EXCLUDE      | (Optional) Comma-separated list of languages to exclude <br> Example: `Jupyter Notebook,CSS,TeX,PHP`      |
| EXCLUDE_REPO | (Optional) Comma-separated list of repositories to exclude <br> Example: `username/repo1,username/repo2`  |
| DESCRIPTION  | (Optional) Custom description for the gist                                                                |

### GitHub Action Setup

#### Prerequisites

1. Create a new public GitHub Gist at https://gist.github.com/
2. Generate an access token with `gist` and `metadata:read` scopes at https://github.com/settings/tokens?type=beta

#### Setup workflow

1. Copy [this workflow file](./action.yml) to your repository's `.github/workflows/` directory
2. Navigate to your repository's **Settings > Secrets**
3. Add the required secrets as listed in the environment variables table above
4. Commit and push your changes

## Credits

- Inspired by [@matchai's bird-box](https://github.com/matchai/bird-box)
- Forked from [@Aveek-Saha's lang-stats-box](https://github.com/Aveek-Saha/lang-stats-box)
