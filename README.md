# Abran custom contribution

Base: v4.250.146

Targeted Wipad contribution:
  git checkout v4.250.146
  git am 0001-morebot-single-transfer-fix.patch
  git am 0002-wipad-provider.patch

All custom features (repair, CF blocks, Morebot/Wipad provider, matching fix):
  git checkout v4.250.146
  git apply full-features.patch

Wipad bridge:
  tar -xzf wipad-api-src.tar.gz -C /opt/wipad-api
  install -m 644 wipad-api.service /etc/systemd/system/wipad-api.service
  systemctl daemon-reload && systemctl enable --now wipad-api

The bridge needs a proxy with an Iranian residential/mobile IP for the Wepad
SSO. It exposes /status, /login, /otp, /token, /transactions, /balance on
127.0.0.1:8089.
