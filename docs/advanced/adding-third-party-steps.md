---
id: adding-third-party-steps
title: Adding Third-Party Steps
---

## Supported Plugins

-   [Turbo Builder PRO](https://assetstore.unity.com/packages/slug/98714) by [Crosstales](https://assetstore.unity.com/publishers/9785)
-   [Turbo Switch PRO](https://assetstore.unity.com/packages/slug/60040) by [Crosstales](https://assetstore.unity.com/publishers/9785)
-   [Turbo Backup PRO](https://assetstore.unity.com/packages/slug/98711) by [Crosstales](https://assetstore.unity.com/publishers/9785)
-   [Maintainer](https://assetstore.unity.com/packages/slug/32199) by [CodeStage](https://assetstore.unity.com/publishers/3918)

---

## Including Third-Party Steps

For this example, we'll include [Maintainer](https://assetstore.unity.com/packages/slug/32199) steps into the project. Be sure to have the plugin added into the project in advance or there will be compilation errors.

1. [Download the GitHub repository as Zip](https://github.com/RockTomate/Steps). Ensure you're on `stable` branch.

> The `develop` branch could reference some features which the current version of RockTomate does not support yet, which may result in compilation errors.<br><br>
> Use `stable` branch instead.

2. Unzip the downloaded file and navigate to `Steps-stable/Classes/Third-Party/PUBLISHER` (where `PUBLISHER` would be "Codestage"). Copy the plugin folder ("Maintainer" in our case).

3. In Unity project, navigate to `RockTomate/Scripts/Steps/Classes/` and create a "Third-Party" directory.
4. Paste the "Maintainer" folder into "Third-Party" directory.
5. After Unity finished compiling, you should now see new steps in the [Step Browser](ui/step-browser-window.md) window.

![](/assets/advanced/third-party-step-added.png)
