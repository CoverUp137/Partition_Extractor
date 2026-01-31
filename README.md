# Android Firmware Partition Extractor & KernelSU Auto-Patcher

This is a GitHub Actions-based automation tool designed to help users extract specific partitions from Android firmware (`payload.bin`) and optionally apply KernelSU LKM-mode Root patches.

## 🛠️ Usage Instructions

1. **Obtain GitHub Token**: Click your profile picture in the top right corner -> **Settings** -> **Developer Settings** -> **Personal access tokens** -> Create a new token.
2. **Fork this Repository**: Fork this project to your own GitHub account.
3. **Configure Secrets**: Go to your repository's **Settings** -> **Secrets and variables** -> **Actions** -> **New repository secret**. Set the name to `TOKEN` and paste your personal access token.
4. **Access Actions**: Navigate to the **Actions** tab in your repository.
5. **Select Workflow**: Choose the **"Firmware Partition Extraction & KernelSU Patch"** workflow from the left sidebar.
6. **Run Workflow**: Click **"Run workflow"** on the right and fill in the following parameters:
   - **Firmware ZIP URL**: Direct download link for the firmware.
   - **Partitions to extract**: Default is `boot,init_boot`, modify as needed (comma-separated).
   - **Patch with KernelSU**: Check this box to enable the patching feature.
   - **Magisk Version**: Used to extract the `magiskboot` tool (e.g., `30.6`).
   - **KernelSU Version**: Specify the KSU version (e.g., `3.0.0`).
   - **KMI Version**: Specify the kernel version (e.g., `android15-6.6`). This must match the `.ko` filename in the official KernelSU Release.
   - **Target Partition to Patch**: Usually `init_boot` or `boot`.
   - **Upload Options**: Choose whether to upload to Releases or Workflow Artifacts.

## 📂 File Descriptions

- `.github/workflows/extract-partitions-Kernelsu.yml`: The core workflow configuration file.
- `README.md`: This documentation file.

## ⚠️ Important Notes

- **KMI Version Matching**: KernelSU patching is highly dependent on the accuracy of the KMI version. Please ensure your kernel version is correct.
- **Storage Space**: GitHub Actions has storage limits. It is recommended to check manually or rely on the built-in auto-cleanup feature (runs every 5 days).
- **Disclaimer**: This tool is for technical exchange only. Flashing your device carries risks; please proceed with caution.

## 🤝 Credits & Plugins

- [payload-dumper-go](https://github.com/ssut/payload-dumper-go)
- [KernelSU](https://github.com/tiann/KernelSU)
- [Magisk](https://github.com/topjohnwu/Magisk)
- [delete-workflow-runs](https://github.com/Mattraks/delete-workflow-runs)
- [delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
