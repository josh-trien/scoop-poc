# Trienpont Bucket

Template bucket for [Scoop](https://scoop.sh), the Windows command-line installer.

## How to install Scoop

Please run the following commands:

```pwsh
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script the first time
>irm get.scoop.sh | iex
```

## How do I install these manifests?

After manifests have been committed and pushed, run the following:

```pwsh
scoop bucket add scoop-poc https://github.com/josh-trien/scoop-poc
scoop install scoop-poc/<manifest name>
```

## How do I contribute to this bucket?

1. Document the bucket in `README.md`.
2. Replace the placeholder repository string in `bin/auto-pr.ps1`.
3. Create new manifests by copying `bucket/app-name.json.template` to
   `bucket/<app-name>.json`.
4. Commit and push changes.
5. If you'd like your bucket to be indexed on `https://scoop.sh`, add the
   topic `scoop-bucket` to your repository.

## How do I contribute new manifests?

To make a new manifest contribution, please read the [Contributing
Guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md)
and [App Manifests](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)
wiki page.

## Hash doesn't match error?

To fix this the hash needs to updated with the new artifact hash that has been uploaed to the manifests url
steps:
1. Grab the url from the manifest of the tool that failed to download under bucket
2. Access that url to download the file.+/zipped folder
3. Run the following command in Powershell
    `Get-FileHash <Path to downloaded File> SHA256`
4. Take that hash output and replace the hash value within the manifest with said hash
5. Push these changes to master
6. Update your local bucket by running `scoop update` and rerun the install
