# Instructions for agents

- `plugins/<name>/` holds one plugin, listed in `.agents/plugins/marketplace.json`.
- `templates/<name>/` holds one repository template, listed in `.gitbook/templates.json`. The app copies the folder into each new repo, minus what the answers to its `template.yaml` leave out, so everything in it is for the people and agents using that repo.
- `templates/base/` is the skeleton a new template starts from, and `templates/blank/` is base filled in for a general-purpose repo. Neither is listed.
- Work on a branch and open a pull request. Never push to `main`.
