---
title: "Configuring a Team with Okta"
menu:
  main:
    parent: 'reference'
    weight: 2
---

1. After choosing your teamname and billing plan, select the "Okta" option for the auth backend and click "Next". You should see a page that tells you what values to enter for "Base URL" and "Audience URI"
2. In a separate tab, log in to your Okta instance
3. Click the "Admin" button in the upper right corner
4. Go to your Applications page by clicking the “Applications” tab and selecting “Applications”
5. Click the “Add Application” button
6. Search for “ScaleFT” and click the “Add” button
7. Here, you’ll fill in the information from Step 1 for the “Base URL” and “Audience Restriction;" click "Next"
8. Make sure to assign the app to anyone you want to be able to log in to your team and click “Next”
9. Choose your ScaleFT username and click “Done.”
10. Go to the “Sign On” tab, click the “View Setup Instructions" button
11. Follow the instructions on the "View Setup Instructions" page to setup your `sshUserName` attribute, if desired.
12. From this page, you will need the `Login URL/SignOn URL`, the `IDP Issuer/Entity ID`, and the `x.509 Certificate` in PEM format
13. Back on the ScaleFT Signup page, enter each of the values from Step 12 in the corresponding place in the form and click “Authenticate With Okta”
14. Your team should now be successfully configured! When you log in to ScaleFT you will be redirected to Okta for authentication.
