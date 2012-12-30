```
vulcan build -v \
  -n fontconfig \
  -c "./configure --prefix /app/vendor/fontconfig \
    --disable-static --disable-docs && make install" \
  -p /app/vendor/fontconfig
```
