# Sync ChainGuard Registry to GHCR

This is an example action to synchronize a Chainguard registry to GHCR. This is currently set to run on push, but you would most likely configure this to [run on a schedule](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule)

## Instructions

You need to populate the following secrets:

```CGIDENTITY```

This is generated using the [chainctl](https://edu.chainguard.dev/chainguard/administration/how-to-install-chainctl/#:~:text=You%20can%20install%20chainctl%20for,chainctl%20on%20your%20macOS%20device) utility.

Run the following command in your terminal to generate this value:

```
chainctl iam identity create github[GITHUB-IDENTITY] \
  --github-repo=${GITHUB_ORG}/${GITHUB_REPO} \
  --github-ref=refs/heads/main \
  --role=registry.pull
```

```GHTOKEN```

Create a Github token that has permissions to push images to GHCR

```ORG_NAME```

The Chainguard Org that you are going to be synchronizing from.

```TARGET_NAME```

The name of the registry you are going to be pushing the containers to.
