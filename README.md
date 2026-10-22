# ISKCON Hadapsar - Firebase-free Live Darshan demo

This independent test repository has a public YouTube Live Darshan page, a link control panel, and a small static live.json file. No Firebase SDK required.

## Publish your website
Go to https://github.com/bjendermisra-ops/yt/settings/pages. Set Source = Deploy from a branch, Branch = main, folder = /(root), Save. Site should appear at https://bjendermisra-ops.github.io/yt/.

## Update the live video
Open https://bjendermisra-ops.github.io/yt/admin.html . You will need a GitHub fine-grained personal access token restricted to only repository bjendermisra-ops/yt and permission Contents: Read and write. Create it from GitHub Settings > Developer settings > Personal access tokens > Fine-grained tokens. Use a short token lifetime for testing.

Paste the token into the admin page each time you save. Toggle Live ON, enter the **direct YouTube video link** or 11-character video ID, and click Save. GitHub will commit a new live.json. After hosting deploys the commit, https://bjendermisra-ops.github.io/yt/darshan.html shows that stream. Toggle Live OFF to show the offline message.

## Security
Never share, commit, or screenshot your token. The test page does not save the token in files, localStorage, or cookies. It sends the token only to the GitHub HTTPS API, then clears the field on success. For production, a private, authenticated Cloudflare Worker with a GitHub secret is better than a browser-entered token.

## Constraints
A static site cannot change GitHub files without authorization. GitHub Pages may take up to about 10 minutes to deploy new commits. Public pages check static JSON approximately once per minute; changes are not instantaneous. YouTube delivers the video bytes, and embedding needs to be permitted by YouTube. No 20,000-concurrent-user capacity has been load tested.

## Existing ISKCON app
This demo does NOT change the existing iskcon-mob repo. If the test works, we can integrate this static link system into iskcon-mob and remove its live status Firebase listeners carefully.