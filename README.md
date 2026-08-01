This is a sample theme for Obsidian ([https://obsidian.md](https://obsidian.md/)).

## First Time publishing a theme?

### Quick start

<img width="244" alt="Pasted image 20220822135601" src="https://user-images.githubusercontent.com/693981/186000386-4f4da987-fcaf-4aa5-aed4-e34b5901255d.png">

First, choose **Use this template**. That will create a copy of this repository (repo) under your Github profile. Then, you will want to _clone_ your new repository to your computer.

Once you have the repo locally on your computer, there are a couple of placeholder fields you will need to fill in.

1. Inside the `manifest.json` file, change the "name" field to whatever you want the name of your theme to be. For example:

  ```json
  {
    "name": "Moonstone",
    "version": "0.0.0",
    "minAppVersion": "1.0.0"
  }
  ```

2. Also inside the manifest.json file, you can include your name under next to the "author" field.

After you have those fields configured, all that's left to do is add your styles! All of your CSS needs to be inside the file `theme.css` which is located at root of your repository.

For a deeper walkthrough, see the official [Build a theme](https://docs.obsidian.md/Themes/App+themes/Build+a+theme) tutorial.

## Adding your theme to the Theme Gallery

Before you continue, review the [Theme guidelines](https://docs.obsidian.md/Themes/App+themes/Theme+guidelines) for best practices, such as using CSS variables, avoiding `!important`, and keeping assets local. Themes that don't follow them are more likely to break on future Obsidian versions or get flagged during review.

### Add a screenshot thumbnail

Inside the repository, include a screenshot thumbnail of your theme. We recommend storing it in a `screenshots` folder at the root of your repository, for example `screenshots/screenshot.png`. This image will be used for the small preview in the theme list.

Your screenshot file should be `16:9` aspect ratio.
The recommended size is 512x288.

## Releasing Versions

Obsidian downloads your theme's `manifest.json` and `theme.css` from a GitHub Release, so publishing a release is a required step, not an optional one. Introduced in v0.16 of Obsidian, themes support [Github Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository). This means that you can specify which versions of your theme are compatible with which versions of Obsidian.

This repository already includes a [GitHub Actions workflow](.github/workflows/release.yml) that automates this: pushing a tag matching your `manifest.json` version creates a draft release with `manifest.json` and `theme.css` attached, which you can then review and publish. See [Release your theme with GitHub Actions](https://docs.obsidian.md/Themes/App+themes/Release+your+theme+with+GitHub+Actions) for details, or follow the manual steps below.

### Steps for releasing the initial version of your theme (1.0.0)

1. From your theme's repository, click on "Releases".
   
<img width="235" alt="Pasted image 20220822145001" src="https://user-images.githubusercontent.com/693981/186000441-287a1a97-65f6-4b5f-ba66-810ceae91cd3.png">

2. On the Releases page, there should be a button to **Draft a new Release**. Press it.

<img width="202" alt="Pasted image 20220822145048" src="https://user-images.githubusercontent.com/693981/186000664-6c63ae14-f685-4d39-bfe6-324f95cd9669.png">

3. Fill out the Release information form.
	- **Choose a Tag**: Type in the name of the version number here. At the bottom of the dropdown should be a button to create a new tag with your latest theme changes. Choose this option.
		<img width="340" alt="Pasted image 20220822145648" src="https://user-images.githubusercontent.com/693981/186000848-bd1c2619-ea09-4e70-a886-40769cda6921.png">
	- **Release Title**: This can be the version number.
	- **Description** _Optional_: Anything that changed
	- **Files:** The most important part of this form is uploading the files. You can do this by dragging 'n dropping the `manifest.json` file and the `theme.css` file your for theme inside the file upload field.

<img width="946" alt="Pasted image 20220822145356" src="https://user-images.githubusercontent.com/693981/186000772-e689ecea-c3b7-4e9d-9204-7ad62c0123aa.png">

4. Click "Publish Release."
5. Make sure that `versions.json` is set up correctly. This file is a map.
  ```json
  {
    "1.0.0": "0.16.0"
  }
  ```
  
  This means that version 1.0.0 of your theme is compatible with version 0.16.0 of Obsidian. For the initial release of your theme, you shouldn't need to make any changes to this file.
 
### Steps for releasing new versions

Releasing a new version of your theme is the same as releasing the initial version.

1. From your theme's repository, click on "Releases."
2. On the Releases page, there should be a button to **Draft a new Release**. Press it.
3. Fill out the Release information form.
	- **Choose a Tag**: Type in the name of the version number here. At the bottom of the dropdown should be a button to create a new tag with your latest theme changes. Choose this option.
		<img width="333" alt="Pasted image 20220822145812" src="https://user-images.githubusercontent.com/693981/186000912-f494def9-0f67-4662-92bf-bd278082455f.png">
	- **Release Title**: This can be the version number.
	- **Description** _Optional_: Anything that changed
	- **Files:** The most important part of this form is uploading the files. You can do this by dragging 'n dropping the `manifest.json` file and the `theme.css` file your for theme inside the file upload field.

4. Click "Publish Release."
5. Update the `versions.json` file in your repository. For the initial release of your theme, you probably didn't need to make any changes to the `versions.json` file. When you release subsequent versions of your theme; however, it's best practice to include the new version as entry in the versions.json file. So this might look like:
  ```json
  {  
		"1.0.0": "0.16.0",
		"1.0.1": "0.16.0"
  }
  ```

  What's important to note here is: the new version is included as the "key" and the "value" is the minimum version of Obsidian that your theme compatible with. So if the new version of your theme is only compatible with an Insider version of Obsidian, it's important to set this value accordingly. This will prevent users on older versions of Obsidian from updating to the newer version of your theme.

## Submit your theme for review

To have your theme included in the Theme Gallery, you'll submit it through the Obsidian Community directory. Make sure you've [added a screenshot](#add-a-screenshot-thumbnail) and [published a release](#releasing-versions) first, since the submission form needs both.

You'll also need a `LICENSE` file in the root of your repository, which isn't included in this template — see [Choose a License](https://choosealicense.com/) if you're not sure which one to use. See the official [Submit your theme](https://docs.obsidian.md/Themes/App+themes/Submit+your+theme) guide for more detail.

1. Go to [community.obsidian.md](https://community.obsidian.md) and sign in with your Obsidian account.
2. Link your GitHub account to your profile. This lets the directory verify that you own the repository you're submitting.
3. In the sidebar, select **Themes**, then select **New theme**.
4. Fill out the submission form:
   - **GitHub repository URL**: your repository's URL, for example `https://github.com/your-username/your-repo-name`.
   - **Owner**: who will own and maintain this entry. This doesn't have to match the repository's GitHub owner.
   - **Screenshot path**: the path to your screenshot, relative to the repository root, for example `screenshots/screenshot.png`.
   - **Supported modes**: check Dark and/or Light depending on which your theme supports.
5. Read and agree to the Developer Policies, and confirm that you'll continue to support your theme (or remove/transfer it if you can no longer provide support).
6. Select **Submit**.

The directory processes the `manifest.json` at the HEAD of your repository's default branch, so make sure it's accurate and committed before submitting. Obsidian downloads `manifest.json` and `theme.css` from the GitHub release whose tag matches the version in your manifest, which is why a published release is required.
