# skack-approval

custom action to send approval request to Slack

![slack-approval](./img/approval)

- Post a message in Slack with a button like the one above.
- Clicking on "Approve" will execute the subsequent workflow.
- Clicking on "Reject" will cause the workflow to fail.

# How To Use

- First, create a Slack App and install in your workspace.
- Second, add `chat:write` and `im:write` to OAuth Scope on OAuth & Permissions page.
- Finally, **Enable Socket**.

```
jobs:
  approval:
    runs-on: ubuntu-latest
    steps:
      - name: send approval
        uses: varu3/slack-approval@master
        env:
          SLACK_APP_TOKEN: ${{ secrets.SLACK_APP_TOKEN }}
          SLACK_BOT_TOKEN: ${{ secrets.SLACK_BOT_TOKEN }}
          SLACK_SIGNING_SECRET: ${{ secrets.SLACK_SIGNING_SECRET }}
          CHANNEL_ID: ${{ secrets.CHANNEL_ID }}
        timeout-minutes: 10
```

- Set environment variables

  - `SLACK_APP_TOKEN`

    - App-level tokens on Basic Information page. (starting with xapp-)

  - `SLACK_BOT_TOKEN`

    - Bot-level tokens on OAuth & Permissions page. (starting with xoxb-)

  - `SLACK_SIGNING_SECRET`

    - Signing Secret on Basic Information page.

  - `CHANNEL_ID`

    - Channel ID for which you want to send approval.

- Set `timeout-minutes`
  - Set the time to wait for approval.