# Post to Slack

```bash
brew install python3
pip3 install requests
```

```python
import requests
import json

def post_to_slack(channel_id, text, color):
    url = "https://slack.com/api/chat.postMessage"
    params = {
            'token': 'your_token',
            'username': 'User Name'
            'icon_emoji': 'icon'
            'channel': channel_id,
            'text': '',
            'attachments': json.dumps([
                {
                    'fallback': text,
                    'text': text,
                    'color': color
                }
            ])
    }
    headers = {'Content-Type': 'application/x-www-form-urlencoded'}
    r = requests.post(url, data=params, headers=headers)
    print(r.text)
```
