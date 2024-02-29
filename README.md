signing-api
===========

This is a minimal API for signing WACZ files using [wacz-signing](https://pypi.org/project/wacz_signing/). You might run it behind a proxy as a systemd service, something like this:

```
[Unit]
Description=WACZ signing web application
After=network.target

[Service]
WorkingDirectory=/path/to/dir
Environment=DOMAIN=some.example.com
Environment=CERTNAME=some.cert.name
ExecStart=/path/to/venv/bin/gunicorn -b localhost:8000 -w 4 app:app
Restart=always

[Install]
WantedBy=multi-user.target
```

Maintenance
-----------

Upgrade `wacz-signing` (or other packages) as needed with `poetry update wacz-signing`, then run `poetry export -o requirements.txt` to produce a regular requirements file for use in non-Poetry virtual environments. 
