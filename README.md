import requests

# Replace 'YOUR_BOT_TOKEN' with your bot's token
BOT_TOKEN = 'YOUR_BOT_TOKEN'
# Replace 'YOUR_CHANNEL_ID' with your channel's ID
CHANNEL_ID = '@your_channel_username'

# API URL to get chat members count
url = f'https://api.telegram.org/bot{BOT_TOKEN}/getChatMembersCount?chat_id={CHANNEL_ID}'

try:
    # Send request to the API
    response = requests.get(url)
    response.raise_for_status()  # Raise HTTPError for bad responses

    # Parse the JSON response
    data = response.json()
    if data['ok']:
        member_count = data['result']
        print(f'Total members in the channel: {member_count}')
    else:
        print(f'Failed to get member count: {data["description"]}')
except requests.exceptions.RequestException as e:
    print(f'Error connecting to the API: {e}')
except Exception as e:
    print(f'An unexpected error occurred: {e}')
