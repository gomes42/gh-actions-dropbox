# 📦 Collection of GitHub Actions for Dropbox (`gh-actions-dropbox`)

Easily integrate Dropbox into your CI/CD pipelines with GitHub Actions for Dropbox. This tool simplifies interactions with the [Dropbox API](https://www.dropbox.com/developers/documentation/http/documentation), enabling file management within your automated workflows. By incorporating Dropbox functionalities into your pipeline, you can streamline tasks such as backups, file transfers, and data synchronization, enhancing the efficiency and reliability of your development processes.

# 🚀 Available Actions<br>

- `File Upload`
- `Download file`
- `Download folder as .zip`
- `Move file/folder`

See [Examples Usage](https://github.com/gomes42/gh-actions-dropbox?tab=readme-ov-file#-examples-usage)

# ⚙️ Configuration

1. Create your app on [Dropbox Developers](https://www.dropbox.com/developers/apps?_tk=pilot_lp&_ad=topbar4&_camp=myapps).

2. Set Required Permissions:

   | Action 🚀          | Permissions 🚦        |
   | ------------------ | --------------------- |
   | files/upload       | `files.content.write` |
   | files/download     | `files.content.read`  |
   | files/download_zip | `files.content.read`  |
   | files/move         | `files.content.write` |

3. Generate an **Access Token** and **Refresh Token**: <br/> Follow [This Guide](https://preventdirectaccess.com/docs/create-app-key-access-token-for-dropbox-account/#access-token).

4. **Create secrets to your repository**: <br/>
   `Settings > Secrets and variables > Actions > Secrets > New repository secret`

```bash
DROPBOX_APP_KEY = ##################
DROPBOX_APP_SECRET = ##################
DROPBOX_REFRESH_TOKEN = ##################
```

# 📝 Examples Usage

<details>
<summary>Upload a file to Dropbox 📤</summary>
<br>

```yaml
jobs:
  my-example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🔔
        uses: actions/checkout@v4

      - name: Dropbox Upload 📦
        uses: gomes42/gh-actions-dropbox/files/upload@2
        with:
          DROPBOX_APP_KEY: ${{ secrets.DROPBOX_APP_KEY }}
          DROPBOX_APP_SECRET: ${{ secrets.DROPBOX_APP_SECRET }}
          DROPBOX_REFRESH_TOKEN: ${{ secrets.DROPBOX_REFRESH_TOKEN }}
          SOURCE_PATH: OriginalFile.txt
          DEST_PATH: /MyFiles/File.txt

          # SOURCE_PATH:
          #   Path to file to upload
          #   (in container)

          # DEST_PATH:
          #   Destination file path
          #   (relative to root of Dropbox account)
```

</details>

<details>
<summary>Download a file from Dropbox 📩</summary>
<br>

```yaml
jobs:
  my-example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🔔
        uses: actions/checkout@v4

      - name: Dropbox Download file 📦
        uses: gomes42/gh-actions-dropbox/files/download@2
        with:
          DROPBOX_APP_KEY: ${{ secrets.DROPBOX_APP_KEY }}
          DROPBOX_APP_SECRET: ${{ secrets.DROPBOX_APP_SECRET }}
          DROPBOX_REFRESH_TOKEN: ${{ secrets.DROPBOX_REFRESH_TOKEN }}
          SOURCE_PATH: /MyFiles/MyFolder/MyFile.txt
          DEST_PATH: MyFile.txt

          # SOURCE_PATH:
          #   Path to a file to download
          #   (relative to root of Dropbox account)

          # DEST_PATH:
          #   Destination file path
          #   (in container)
```

</details>

<details>
<summary>Download a folder as <code>.zip</code> from Dropbox 📁</summary>
<br>

```yaml
jobs:
  my-example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🔔
        uses: actions/checkout@v4

      - name: Dropbox Download (.zip) 📦
        uses: gomes42/gh-actions-dropbox/files/download_zip@2
        with:
          DROPBOX_APP_KEY: ${{ secrets.DROPBOX_APP_KEY }}
          DROPBOX_APP_SECRET: ${{ secrets.DROPBOX_APP_SECRET }}
          DROPBOX_REFRESH_TOKEN: ${{ secrets.DROPBOX_REFRESH_TOKEN }}
          SOURCE_PATH: /MyFiles/MyFolder
          DEST_PATH: MyFolder.zip

          # SOURCE_PATH:
          #   Path to a folder to download as .zip
          #   (relative to root of Dropbox account)

          # DEST_PATH:
          #   Destination .zip file path
          #   (in container)
```

</details>

<details>
<summary>Move a file or folder on Dropbox 🔀</summary>
<br>

```yaml
jobs:
  my-example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🔔
        uses: actions/checkout@v4

      - name: Dropbox Move 📦
        uses: gomes42/gh-actions-dropbox/files/move@2
        with:
          DROPBOX_APP_KEY: ${{ secrets.DROPBOX_APP_KEY }}
          DROPBOX_APP_SECRET: ${{ secrets.DROPBOX_APP_SECRET }}
          DROPBOX_REFRESH_TOKEN: ${{ secrets.DROPBOX_REFRESH_TOKEN }}
          SOURCE_PATH: /MyFiles/File.txt
          DEST_PATH: /MyFiles/MoveInHere/File.txt

          # SOURCE_PATH:
          #   Path to a file or folder
          #   (relative to root of Dropbox account)

          # DEST_PATH:
          #   Path to the new location
          #   (relative to root of Dropbox account)
```

</details>

# 🤝 Contributing

Contributions are welcome! Please feel free to submit a [Pull Request](https://github.com/gomes42/gh-actions-dropbox/pulls) or [open an issue](https://github.com/gomes42/gh-actions-dropbox/issues).

<a href = "https://github.com/gomes42/gh-actions-dropbox/graphs/contributors">
  <img src = "https://contrib.rocks/image?repo=gomes42/gh-actions-dropbox"/>
</a>

# 📜 License

The scripts and documentation in this project are released under the [MIT License](./LICENSE).
