# Deployment with GitHub Pages

Aether is a static site and can be hosted directly from a GitHub repository.

## 1. Create the repository

Create a repository on GitHub. A suggested repository name is:

```text
aether-by-iomi-roman-and-co
```

For public distribution, choose **Public** visibility. Review the license decision in `README.md` before inviting reuse or accepting contributions.

## 2. Push the project

From the project directory:

```bash
git init
git add .
git commit -m "Prepare Aether for GitHub"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/aether-by-iomi-roman-and-co.git
git push -u origin main
```

Replace the placeholders with the actual GitHub username and repository URL. Do not paste credentials into source files or commit them.

## 3. Enable GitHub Pages

1. Open the repository's **Settings**.
2. Select **Pages** in the sidebar.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch `main` and folder `/ (root)`.
5. Save the settings.
6. Open the published Pages URL shown by GitHub.

## 4. Verify the deployment

- Open the public site in a private/incognito browser window.
- Confirm the timer, stopwatch, and clock load.
- Test the custom-duration slider.
- Test saving and deleting a study record.
- Refresh and confirm local storage persists for that browser and site origin.
- Test the mobile layout.
- Confirm that no private files, credentials, or unrelated personal data were committed.

## Notes

- The app currently loads Tailwind CSS and Lucide icons from public CDNs, so those assets require internet access.
- Browser local storage is scoped to the published site origin and browser profile. Local development data will not automatically appear on the GitHub Pages domain.
- GitHub Pages hosting does not provide a database or user synchronization for this app.
