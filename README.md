# CQORC Interfaces (`cqorc_interfaces`)

Reusable Python API wrappers and interfaces for Google (Drive, Sheets, Calendar), Eventbrite, Zoom, and Slack.

Originally developed by Calcul Québec for training and event logistics automation.

## Installation

Install the package directly from GitHub:

```bash
# Install everything:
pip install "cqorc_interfaces[all] @ git+https://github.com/calculquebec/cqorc_interfaces.git"

# Or install only specific interface dependencies:
pip install "cqorc_interfaces[google] @ git+https://github.com/calculquebec/cqorc_interfaces.git"
pip install "cqorc_interfaces[slack] @ git+https://github.com/calculquebec/cqorc_interfaces.git"
pip install "cqorc_interfaces[zoom] @ git+https://github.com/calculquebec/cqorc_interfaces.git"
pip install "cqorc_interfaces[eventbrite] @ git+https://github.com/calculquebec/cqorc_interfaces.git"
```

For local editable development:

```bash
git clone https://github.com/calculquebec/cqorc_interfaces.git
cd cqorc_interfaces
pip install -e ".[all]"
```

## Available Interfaces

### Google (`cqorc_interfaces.google`)

Supports Google Drive, Sheets, and Calendar with OAuth2 user or service account flows.

```python
from cqorc_interfaces.google import GSheetsInterface, GDriveInterface, GCalInterface

sheets = GSheetsInterface(key_file="secrets/credentials.json")
drive = GDriveInterface(key_file="secrets/credentials.json")
calendar = GCalInterface(key_file="secrets/credentials.json", calendar_id="primary")
```

### Eventbrite (`cqorc_interfaces.eventbrite`)

Handles Eventbrite event listing, attendees, ticket classes, and attendee normalization.

```python
from cqorc_interfaces.eventbrite import EventbriteInterface

eb = EventbriteInterface(token="YOUR_EVENTBRITE_TOKEN")
events = eb.get_events()
```

### Zoom (`cqorc_interfaces.zoom`)

Handles Zoom Server-to-Server OAuth authentication, meeting creation, webinars, and attendance tracking.

```python
from cqorc_interfaces.zoom import ZoomInterface

zoom = ZoomInterface(
    account_id="...",
    client_id="...",
    client_secret="...",
    timezone="America/Montreal"
)
```

### Slack (`cqorc_interfaces.slack`)

Wraps `slack_sdk` for managing channels, users, and messaging.

```python
from cqorc_interfaces.slack import SlackInterface

slack = SlackInterface(bot_token="xoxb-...")
channel_id = slack.get_channel_id("general")
```

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
