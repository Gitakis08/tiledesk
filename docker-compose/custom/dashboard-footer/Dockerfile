FROM tiledesk-dashboard:local

COPY pobuca-footer.js /usr/share/nginx/html/pobuca-footer.js
COPY pobuca-ui.css /usr/share/nginx/html/pobuca-ui.css

RUN set -eux; \
  INDEX="$(find /usr/share/nginx/html -name index.html | head -n 1)"; \
  sed -i '/pobuca-footer.js/d' "$INDEX"; \
  sed -i '/pobuca-ui.css/d' "$INDEX"; \
  sed -i 's#<title>.*</title>#<title>Pobuca Converse</title>#g' "$INDEX"; \
  sed -i 's#</head>#  <link rel="stylesheet" href="./pobuca-ui.css?v=pobuca-helpcenter-20260504">\n</head>#' "$INDEX"; \
  sed -i 's#</body>#  <script src="./pobuca-footer.js?v=pobuca-footer-working-20260504"></script>\n</body>#' "$INDEX"

# Pobuca/Zemark dashboard image assets
COPY favicon.ico /usr/share/nginx/html/assets/img/logos/favicon.ico
COPY tiledesk-logo.svg /usr/share/nginx/html/assets/img/logos/tiledesk-logo.svg
COPY tiledesk_logo_no_text.svg /usr/share/nginx/html/assets/img/logos/tiledesk_logo_no_text.svg
COPY tiledesk-solo-logo.png /usr/share/nginx/html/assets/img/logos/tiledesk-solo-logo.png
COPY tilebot_logo_small.png /usr/share/nginx/html/assets/img/tilebot_logo_small.png
