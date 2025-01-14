# Release process

Start by making a release issue using the template below. The issue checklist can be followed to
release a new version of the Helm chart and help everybody coordinate. Do some
copy pasting!

## Issue title: Release x.y.z

This issue will be used to coordinate the next release of the Helm
chart according to the instructions in [RELEASE.md](RELEASE.md).
Below is the checklist for this release.

## Pre-release iteration 1

- Make a changelog
  - [ ] Summarize points of interest.
  - [ ] List breaking changes and mention the [upgrade instructions](https://z2jh.jupyter.org/en/latest/upgrading.html).
    - [ ] Update the upgrade instructions.
  - [ ] List features with brief descriptions.

- Pre-release
  - [ ] Create and push a git tag

    ```bash
    git checkout master
    git pull <REMOTE> master
    git tag -a x.y.z-beta.1
    git push <REMOTE> --tags
    ```

- Update documentation
  - [ ] Update old version references to the new version

- Communicate
  - [ ] Write a discourse post

- Verify
  - [ ] Follow one set of instructions to deploy on z2jh.jupyter.org

## Final release

- Update changelog
  - [ ] Update the changelog
  - [ ] Generate and add a list of contributors

    ```bash
    # install dependencies for the script
    pip install pygithub requests-cache tqdm

    # NOTE: You may need to wait a long time for this to finish. You may even
    #       get errors because you used too much of your API quota. If that
    #       happens, you can re-run it again later and rely on the caching to
    #       ensure you make progress. You have 5000 requests per hour.

    # get a GITHUB_API_TOKEN for use with the script
     GITHUB_API_TOKEN="your-token" tools/contributors.py
    ```

- Release
  - [ ] Create and push a git tag

    ```bash
    git checkout master
    git pull <REMOTE> master
    git tag -a x.y.z
    git push <REMOTE> --tags
    ```

  - [ ] Create a GitHub release
    
    Visit the [release
    page](https://github.com/jupyterhub/zero-to-jupyterhub-k8s/releases) and
    create a new release referencing the recent tag. Add a brief text like the
    one below.

    ```Markdown
    # TODO: Figure out how to...
    - Warn about eventual breaking changes.
    - Reference upgrade instructions and the changelog.
    - NOTE: Also make the upgrade instructions contain a reference on what to do if they fail.
    ```

- Communicate
  - [ ] Write a discourse post
  - [ ] Write a blog post
  - [ ] Tweet about it
