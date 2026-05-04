FROM tiledesk-dashboard:local

COPY pobuca-footer.js /usr/share/nginx/html/pobuca-footer.js
COPY pobuca-ui.css /usr/share/nginx/html/pobuca-ui.css

RUN set -eux; \
  INDEX="$(find /usr/share/nginx/html -name index.html | head -n 1)"; \
  sed -i '/pobuca-footer.js/d' "$INDEX"; \
  sed -i '/pobuca-ui.css/d' "$INDEX"; \
  sed -i 's#</head>#  <link rel="stylesheet" href="./pobuca-ui.css?v=pobuca-helpcenter-20260504">\n</head>#' "$INDEX"; \
  sed -i 's#</body>#  <script src="./pobuca-footer.js?v=pobuca-footer-working-20260504"></script>\n</body>#' "$INDEX"
