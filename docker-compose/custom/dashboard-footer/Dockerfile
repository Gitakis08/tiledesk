FROM tiledesk-dashboard:local

COPY pobuca-footer.js /usr/share/nginx/html/pobuca-footer.js

RUN set -eux; \
  INDEX="$(find /usr/share/nginx/html -name index.html | head -n 1)"; \
  sed -i '/pobuca-footer.js/d' "$INDEX"; \
  if grep -q "</body>" "$INDEX"; then \
    sed -i 's#</body>#  <script src="./pobuca-footer.js?v=pobuca-20260504-3"></script>\n</body>#' "$INDEX"; \
  else \
    printf '\n<script src="./pobuca-footer.js?v=pobuca-20260504-3"></script>\n' >> "$INDEX"; \
  fi
