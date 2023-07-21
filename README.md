# Why?
Don't pull in a full docker container just to send a few messages.

## Script version (discord.sh)
```bash
TITLE=${1:-"Title"}
MESSAGE=${2:-"Message"}
COLOR=${3:-"999999"}
URL=${4:-'https://discord.com/api/webhooks/XXXXXXXXXXXXX/XXXXXXXXXXXXX'}
# API: https://discord.com/developers/docs/resources/channel#embed-object
curl "$URL" -H "Content-Type: application/json" -X POST -g --data '{"embeds":[{"title":"'"$TITLE"'","description":"'"$MESSAGE"'","color":"'"$((16#$COLOR))"'"}]}'
```
Usage
```bash
./discord.sh "Deploying" "$GIT_SHA" "009900"
```

## Function version
```bash
discord_message() {
	TITLE=${1:-"Title"}
	MESSAGE=${2:-"Message"}
	COLOR=${3:-"999999"}
	URL=${4:-'https://discord.com/api/webhooks/XXXXXXXXXXXXX/XXXXXXXXXXXXX'}
	# API: https://discord.com/developers/docs/resources/channel#embed-object
	curl "$URL" -H "Content-Type: application/json" -X POST -g --data '{"embeds":[{"title":"'"$TITLE"'","description":"'"$MESSAGE"'","color":"'"$((16#$COLOR))"'"}]}'
}
```
Usage
```bash
discord_message "Deploying" "$GIT_SHA" "009900"
```

Thanks for coming to my TED talk.
