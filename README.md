# test-1
import requests

# Replace 'YOUR_BOT_TOKEN' with your bot's token
BOT_TOKEN = 'YOUR_BOT_TOKEN'
# Replace 'YOUR_CHANNEL_ID' with your channel's ID
CHANNEL_ID = '@your_channel_username'

# API URL to get chat members count
url = f'https://api.telegram.org/bot{BOT_TOKEN}/getChatMembersCount?chat_id={CHANNEL_ID}'

# Send request to the API
response = requests.get(url)

# Check the response status
if response.status_code == 200:
    data = response.json()
    if data['ok']:
        member_count = data['result']
        print(f'Total members in the channel: {member_count}')
    else:
        print('Failed to get member count:', data['description'])
else:
    print('Failed to connect to the API:', response.status_code)
