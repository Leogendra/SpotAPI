# SpotAPI

Welcome to SpotAPI! This Python library is designed to interact with the private and public Spotify APIs, emulating the requests typically made through a web browser. This wrapper provides a convenient way to access Spotify’s rich set of features programmatically.

**Note**: This project is intended solely for educational purposes and should be used responsibly. Accessing private endpoints and scraping data without proper authorization may violate Spotify's terms of service

## Features
- **Public API Access**: Fetch and manipulate public Spotify data such as playlists, albums, and tracks.
- **Private API Access**: Experiment with less commonly used Spotify endpoints.
- **Browser-like Requests**: Mimics the HTTP requests Spotify makes in the browser perfectly, providing an accurate representation of what you’d see on the web interface.

## Installation
```
pip install spotapi
```

## Quick Example
```py
from spotapi import (
    Login, 
    Config, 
    NoopLogger, 
    solver_clients, 
    PrivatePlaylist, 
    MongoSaver
)

cfg = Config(
    solver=solver_clients.Capsolver("YOUR_API_KEY", proxy="YOUR_PROXY"),
    logger=NoopLogger(),
    # You can add a proxy by passing a custom TLSClient
)

instance = Login(cfg, "YOUR_PASSWORD", email="YOUR_EMAIL")
# Now we have a valid Login instance to pass around
instance.login()

# Do whatever you want now
playlist = PrivatePlaylist(instance, "SOME_PLAYLIST")
playlist.create_playlist("Spotapi Showcase!")

# Save the session
instance.save(MongoSaver())
```

[GPL 3.0](https://choosealicense.com/licenses/gpl-3.0/)

