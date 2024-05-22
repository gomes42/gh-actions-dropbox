# 📦 Collection of GitHub Actions for Dropbox (`gh-actions-dropbox`)

Easily integrate Dropbox into your CI/CD pipelines with GitHub Actions for Dropbox. This tool simplifies interactions with the [Dropbox API](https://www.dropbox.com/developers/documentation/http/documentation), enabling file management within your automated workflows. By incorporating Dropbox functionalities into your pipeline, you can streamline tasks such as backups, file transfers, and data synchronization, enhancing the efficiency and reliability of your development processes.

# 🚀 Available Actions<br>

`File Upload`<br>
`Download folder as .zip`<br>

# ⚙️ Configuration

1. Create your app on [Dropbox Developers](https://www.dropbox.com/developers/apps?_tk=pilot_lp&_ad=topbar4&_camp=myapps).

2. Set Required Permissions:

   | Action 🚀          | Permissions 🚦        |
   | ------------------ | --------------------- |
   | files/upload       | `files.content.write` |
   | files/download_zip | `files.content.read`  |

3. Generate an **Access Token** and **Refresh Token**: <br/> Follow [This Guide](https://preventdirectaccess.com/docs/create-app-key-access-token-for-dropbox-account/#access-token).

4. **Create secrets to your repository**: <br/>
   `Settings > Secrets and variables > Actions > Secrets > New repository secret`

```bash
DROPBOX_APP_KEY = ##################
DROPBOX_APP_SECRET = ##################
DROPBOX_REFRESH_TOKEN = ##################
```

# 📝 Examples Usage

<details open>
<summary>Upload file to Dropbox 📤</summary>
<br>

```yaml
jobs:
  my-example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🔔
        uses: actions/checkout@v4

      - name: Dropbox Upload 📦
        uses: lgxm3z/gh-actions-dropbox/files/upload@2
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

<details open>
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
        uses: lgxm3z/gh-actions-dropbox/files/download_zip@2
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

# 🤝 Contributing

Contributions are welcome! Please feel free to submit a [Pull Request](https://github.com/lgxm3z/gh-actions-dropbox/pulls) or [open an issue](https://github.com/lgxm3z/gh-actions-dropbox/issues).

# 📜 License

The scripts and documentation in this project are released under the [MIT License](./LICENSE).
