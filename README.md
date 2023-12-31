# Trienpont Bucket

Trienpont bucket for [Scoop](https://scoop.sh), the Windows command-line installer.

## List of Avaliable Apps a.k.a Manifests
- dbeaver
- filezilla
- git
- github desktop
- nodejs16
- nuget
- sql server management studio (smss)
- visual studion 2019 (visualstudio19)
- visual studio 2022 (visualstudio22)

**special**
- cptools => Installs all required applications to develop on the Capital Platforms project

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

1. Create new manifests by copying `bucket/app-name.json.template` to
   `bucket/<app-name>.json`.
2. See this resource on how to create manifests:

    `To make a new manifest contribution, please read the [Contributing
    Guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md)
    and [App Manifests](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)
    wiki page.`

3. Once read and understood either create your own or navigate to scoop.sh/apps and retrofit premade casks to your use case


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
