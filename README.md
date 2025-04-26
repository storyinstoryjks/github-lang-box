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


Fork of [lang-stats-box](https://github.com/Aveek-Saha/lang-stats-box) with some customizations:

- Updated dependencies, Rewritten in TypeScript
- Published to npm, Added binary for use with `npx` or `pnpx`
- Use `/user/repos` endpoint to fetch all repos of the user (including private repos)
- Custom `description`, exclude languages and _repositories_!

> **Note**: Due to the use of `/user/repos` endpoint, the Fine-grained access tokens must have the `metadata:read` permission.

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
- `--dry` - Preview output without updating the gist

**Required Environment Variables:**
| Variable     | Description                                                                                                          |
| ------------ | -------------------------------------------------------------------------------------------------------------------- |
| GH_TOKEN     | GitHub access token with `gist` and `metadata:read` scopes                                                           |
| GIST_ID      | The ID portion from your gist url: <br> `https://gist.github.com/Aveek-Saha/` **`8335e85451541072dd25fda601129f7d`** |
| GH_USERNAME  | Your GitHub account username                                                                                         |
| EXCLUDE      | A comma-separated list of languages you want to exclude from the gist. <br> Eg: _Jupyter Notebook, CSS, TeX, PHP_    |
| EXCLUDE_REPO | A comma-separated list of repositories you want to exclude from the gist. <br> Eg: _username/repo1, username/repo2_  |
| DESCRIPTION  | A custom description for the gist.                                                                                   |
|              |


#### Options

- `--dry`: Dry run, only fetch the data and print the output.


### Setup a GitHub Action

#### Prep work

1. Create a new public GitHub Gist (https://gist.github.com/)
2. Create an access token with the `gist` and `metadata:read` scopes and copy it.(https://github.com/settings/tokens?type=beta)

#### Project setup

1. Copy [this workflow file](./action.yml) to your repo's `.github/workflows` directory.
2. Go to the repo **Settings > Secrets**
3. Add the secrets according to the environment variables listed above. **Make sure to add the `GH_TOKEN` secret.** 
4. Commit and push the changes to your repo.

## Credits

This code was inspired by [@matchai's bird-box](https://github.com/matchai/bird-box).

This is a fork of [@Aveek-Saha's lang-stats-box](https://github.com/Aveek-Saha/lang-stats-box).
