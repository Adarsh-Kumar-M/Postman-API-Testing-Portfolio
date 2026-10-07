# Publish on GitHub from your Mac

1. Download and unzip `Postman-API-Testing-Portfolio.zip`. Move the extracted `Postman-API-Testing-Portfolio` folder to Desktop. Keep the folder contents together.
2. Review README.md and the collections. Import the corrected files into Postman and run the CRUD workflows before claiming a successful live run. Use local copies for credentials.
3. Open https://github.com/new in your GitHub account.
4. Name the repository `Postman-API-Testing-Portfolio`; choose Public so recruiters can see it.
5. Use description: `Postman API testing portfolio: CRUD workflows, authentication, OAuth, JavaScript assertions, and request chaining.`
6. Leave the options to add a README, .gitignore, and license unchecked. The folder already contains the first two; a license can be chosen later.
7. Click Create repository.
8. Open Terminal and run these commands (adjust the folder path if you saved it elsewhere):

```bash
cd ~/Desktop/Postman-API-Testing-Portfolio
git init
git branch -M main
git add .
git status
git commit -m "Add Postman API testing portfolio"
git remote add origin https://github.com/Adarsh-Kumar-M/Postman-API-Testing-Portfolio.git
git push -u origin main
```

Check `git status` before committing. It should contain only this prepared portfolio, not the original uploaded exports or locally filled-in private environments. Replace the username in the remote if publishing under a different account. Use your established GitHub command-line authentication; an authentication error must be resolved before push can succeed.

9. Refresh the repository page. Confirm README renders, collections/ has 7 files, and environments/ has 6 files.
10. Add relevant topics such as `postman`, `api-testing`, `qa`, `rest-api`, and `oauth`. Pin the repository on your profile.

Official GitHub instructions: https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github

This is repository publishing; GitHub Pages hosting is unnecessary for a Postman collection portfolio.
