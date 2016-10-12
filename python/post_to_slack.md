# Post to Slack

```python
import urllib
import urllib2

def post_to_slack(channel_id, text, color):
    url = "https://slack.com/api/chat.postMessage"
    params = {
            'token': 'your_token',
            'channel': channel_id,
            'text': '',
            'attachments': [
                {
                    'fallback': text,
                    'text': text,
                    'color': color
                }
            ]
    }
    params = urllib.urlencode(params)
    req = urllib2.Request(url)
    req.add_header('Content-Type', 'application/x-www-form-urlencoded')
    req.add_data(params)
    res = urllib2.urlopen(req)
    body = res.read()
```
