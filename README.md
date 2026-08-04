This is a sample theme for Obsidian ([https://obsidian.md](https://obsidian.md/)).

## First time creating a theme?

### Quick start

<img width="244" alt="Pasted image 20220822135601" src="https://user-images.githubusercontent.com/693981/186000386-4f4da987-fcaf-4aa5-aed4-e34b5901255d.png">

First, select **Use this template** to create a copy of this repository under your GitHub profile. Then, clone your new repository to your computer.

Once you have the repository locally on your computer, there are a couple of placeholder fields you'll need to fill in.

1. Inside the `manifest.json` file, update the placeholder fields to describe your theme. For example:

  ```json
  {
    "name": "Moonstone",
    "author": "Your Name",
    "version": "0.0.0",
    "minAppVersion": "1.10.6"
  }
  ```

   - **name** is the name of your theme.
   - **author** is your name.
   - **version** is the version of your theme.
   - **minAppVersion** should only be changed as you add new CSS from Obsidian updates.

After you have those fields configured, all that's left to do is add your styles! All of your CSS needs to be inside the file `theme.css` as a part of your [release](#releasing-versions).

For a deeper walkthrough, see the official [Build a theme](https://docs.obsidian.md/Themes/App+themes/Build+a+theme) tutorial.

## Preparing your theme for the community directory

Before you can submit your theme to the [community directory](https://community.obsidian.md/), there are a few things you'll need to prepare.

Review the [Theme guidelines](https://docs.obsidian.md/Themes/App+themes/Theme+guidelines) for best practices, such as using CSS variables, avoiding `!important`, and keeping assets local. Themes that don't follow them are more likely to break on future Obsidian versions or get flagged during review.

This template already includes [`stylelint-config-obsidianmd`](https://github.com/obsidianmd/stylelint-config), which enforces the same CSS rules used during theme review. Run `npm install` once, then `npm run lint` to check `theme.css` against them. This also runs automatically on every pull request via the [lint workflow](.github/workflows/lint.yml).

### Add a screenshot thumbnail

Inside the repository, include a screenshot thumbnail of your theme. We recommend storing it in a `screenshots` folder at the root of your repository, for example `screenshots/screenshot.png`. This image will be used for the small preview in the theme list.

Your screenshot file should be `16:9` aspect ratio.
The recommended size is 512x288.

### Releasing versions

Themes support [GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository), introduced in v0.16 of Obsidian. This lets you specify which versions of your theme are compatible with which versions of Obsidian.

This repository already includes a [GitHub Actions workflow](.github/workflows/release.yml) that automates this. Pushing a tag matching your `manifest.json` version creates a draft release with `manifest.json` and `theme.css` attached, which you can then review and publish. See [Release your theme with GitHub Actions](https://docs.obsidian.md/Themes/App+themes/Release+your+theme+with+GitHub+Actions) for the full walkthrough.

Before you push a tag, make sure `versions.json` is up to date. This file maps your theme's version to the minimum Obsidian version it's compatible with:

```json
{
  "1.0.0": "1.10.6"
}
```

For the initial release of your theme, you shouldn't need to make any changes to this file. When you release a new version, add an entry for it:

```json
{
  "1.0.0": "1.10.6",
  "1.0.1": "1.10.6"
}
```

The "key" is your theme's version, and the "value" is the minimum version of Obsidian that version is compatible with. If a new version of your theme only works with an Insider build of Obsidian, set this value accordingly, so users on older versions of Obsidian won't be prompted to update to a version that won't work for them.

## Submit your theme for review

To have your theme included in the Theme Gallery, you'll submit it through the Obsidian Community directory. Make sure you've [added a screenshot](#add-a-screenshot-thumbnail) and [published a release](#releasing-versions) first, since the submission form needs both.

You'll also need a `LICENSE` file in the root of your repository, which isn't included in this template. See [Choose a License](https://choosealicense.com/) if you're not sure which one to use. See the official [Submit your theme](https://docs.obsidian.md/Themes/App+themes/Submit+your+theme) guide for more detail.

1. Go to [community.obsidian.md](https://community.obsidian.md) and sign in with your Obsidian account.
2. Link your GitHub account to your profile. This lets the directory verify that you own the repository you're submitting.
3. In the sidebar, select **Themes**, then select **New theme**.
4. Fill out the submission form:
   - **GitHub repository URL** is your repository's URL, for example `https://github.com/your-username/your-repo-name`.
   - **Owner** is who will own and maintain this entry, and doesn't have to match the repository's GitHub owner.
   - **Screenshot path** is the path to your screenshot, relative to the repository root, for example `screenshots/screenshot.png`.
   - For **Supported modes**, select Dark and/or Light depending on which your theme supports.
5. Read and agree to the [Developer Policies](https://docs.obsidian.md/Developer+policies), and confirm that you'll continue to support your theme (or remove/transfer it if you can no longer provide support).
6. Select **Submit**.

The directory processes the `manifest.json` at the HEAD of your repository's default branch, so make sure it's accurate and committed before submitting. Obsidian downloads `manifest.json` and `theme.css` from the GitHub release whose tag matches the version in your manifest, which is why a published release is required.
