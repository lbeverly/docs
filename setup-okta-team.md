---
title: "Configuring a Team with Okta"
menu:
  main:
    parent: 'reference'
    weight: 2
---

1\. After choosing your teamname and billing plan, select the "Okta" option for the auth backend and click "Next". You should see a page that tells you what values to enter for "Base URL" and "Audience URI"

<img src="/docs/static/okta-config-page.png" style="max-height: 621px;" />

2\. In a separate tab, log in to your Okta instance

3\. Click the "Admin" button in the upper right corner

<img src="/docs/static/click-admin-button.png" style="max-height: 621px;" />

4\. Go to your Applications page by clicking the “Applications” tab and selecting “Applications”

<img src="/docs/static/click-applications-tab.png" style="max-height: 621px;" />

5\. Click the “Add Application” button

<img src="/docs/static/click-add-application.png" style="max-height: 621px;" />

6\. Search for “ScaleFT” and click the “Add” button

<img src="/docs/static/add-scaleft.png" style="max-height: 621px;" />

7\. Here, you’ll fill in the information from Step 1 for the “Base URL” and “Audience Restriction;" click "Next"

<img src="/docs/static/enter-config-info.png" style="max-height: 621px;" />

8\. Make sure to assign the app to anyone you want to be able to log in to your team and click “Next”

<img src="/docs/static/assign-to-people.png" style="max-height: 621px;" />

9\. Choose your ScaleFT username and click “Done.”

<img src="/docs/static/enter-username.png" style="max-height: 621px;" />

10\. Go to the “Sign On” tab, click the “View Setup Instructions" button

<img src="/docs/static/view-setup-instructions-button.png" style="max-height: 621px;" />

11\. Follow the instructions on the "View Setup Instructions" page to setup your `sshUserName` attribute, if desired.

12\. From this page, you will need the `Login Provider SSO URL`, the `Identity Provider Issuer`, and the `Identity Provider x.509 Certificate` in PEM format

<img src="/docs/static/setup-instructions.png" style="max-height: 621px;" />

13\. Back on the ScaleFT Signup page, enter each of the values from Step 12 in the corresponding place in the form and click “Authenticate With Okta”

<img src="/docs/static/enter-info-in-signup.png" style="max-height: 621px;" />

14\. Your team should now be successfully configured! When you log in to ScaleFT you will be redirected to Okta for authentication.
