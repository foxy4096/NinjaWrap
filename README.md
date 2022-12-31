# NinjaWrap 🐱‍👤

    A package for making API Wrappers for Django Ninja or Fast API 🐱‍👤

---

## Installing

<small>Coming Soon</small>

```powershell
pip install NinjaWrap
```

## Usage

```python
from getpass import getpass
from pprint import pprint

from NinjaWrap import NinjaWrap

USERNAME = input("Username: ")
PASSWORD = getpass("Password: ")

BASE_URL = "https://vitary.pythonanywhere.com"

# Create a new instance of NinjaWrap.
vitary = NinjaWrap(base_url=BASE_URL)

# Login to the site.
AUTH_KEY = (
    vitary.post(
        "/api/login/",
        data={
            "username": USERNAME,
            "password": PASSWORD,
        },
    )
    .json()
    .get("token")
)

vitary.set_attr("AUTHORIZATION_KEY", AUTH_KEY)

# Get the current user
myself = vitary.get("/api/myself").json()
feeds = vitary.get("/api/feeds", params={"limit": 5}).json()

pprint(myself)
pprint(feeds)

```

It is that simple,

You will get the following response:

```ps
➜ NinjaWrap git:(main) python test.py
Username: foxy4096
Password: ********

{
    "id": 1,
    "first*name": "Aditya",
    "last_name": "Priyadarshi",
    "username": "foxy4096"
    "profile": {
    "allow_nsfw": True,
    "badges": [
        {
            "id": 1,
            "name": "Developer 👩‍💻👨‍💻"
            "description": "The devs of Vitary",
        }
    ],
    "bio": "\_A dumb developer who loves Django*",
    "follower_count": 4,
    "following_count": 9,
    "header_image": "/media/uploads/DSC00406.JPG",
    "image": "/media/uploads/profile.jpeg",
    "status": "online"
    }
}

```
