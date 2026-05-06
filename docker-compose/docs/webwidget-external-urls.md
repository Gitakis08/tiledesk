# Web Widget External URLs

When the Tiledesk web widget is embedded on an external website, the widget must use absolute external URLs for API and MQTT endpoints.

Required runtime `.env` values:

EXTERNAL_BASE_URL=https://zemark-chat.pobuca.com
EXTERNAL_MQTT_BASE_URL=wss://zemark-chat.pobuca.com

Without these values, the widget may resolve `/api/` and `/chatapi/api` relative to the host website domain, for example:

https://staging.hondoscenter.com/api/...

The correct target is:

https://zemark-chat.pobuca.com/api/...
wss://zemark-chat.pobuca.com/mqws/ws

After changing `.env`, recreate the widget container:

docker compose up -d --force-recreate webwidget
