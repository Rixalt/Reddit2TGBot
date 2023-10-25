# Reddit2TGBot

Reddit2TGBot is a Python script that retrieves media (images, GIFs, and videos) from specified subreddits and sends them to a Telegram channel. This project is designed to automate the process of maintaining Telegram channels.

## Prerequisites

Before you begin, ensure you have met the following requirements:

## Database

- Install MariaDB or another programm for setting up the database.
  ```shell
  sudo apt install mariadb-client mariadb-server
  sudo systemctl start mariadb
  sudo mariadb
  ```
The script uses a MySQL database to keep track of shared images. You can create the necessary database, user, and table using the following SQL commands:

```sql
CREATE USER 'user'@'localhost' IDENTIFIED BY 'Password';

CREATE DATABASE DB_name;

GRANT ALL PRIVILEGES ON DB_name.* TO 'user'@'localhost';

CREATE TABLE IF NOT EXISTS used_images (id INT AUTO_INCREMENT PRIMARY KEY, image_url VARCHAR(255) NOT NULL);
```

- Create a virtual environment to manage your Python dependencies.
  ```shell
  python -m venv Reddit2TGBot
  source TGRBot/bin/activate
  ```

## Installation

To run the Reddit2TGBot script, install the required Python libraries using pip:

```shell
pip install praw python-telegram-bot==12.8 requests Pillow imageio moviepy mysql-connector-python
```

## Configuration

You need to create a `config.ini` file to store your API keys, database connection information, and a list of subreddits you want to pull content from. Here's a template for the `config.ini`:

```ini
[cats]
subred_C = cats, blackcats, aww, <other subreddits>

[API]
channel = <telegram channel ID>
tgtoken = <telegram bot token>
client = <Reddit client>
secret = <Reddit secret>
agent = <Reddit agent>

[SQL]
host = localhost
password = <DB password>
user = <DB_Username>
name = <DB_name>
```

Replace `<telegram channel ID>`, `<telegram bot token>`, `<Reddit client>`, `<Reddit secret>`, `<Reddit agent>`, `<DB password>`, `<DB_Username>`, and `<DB_name>` with your own values.

## Usage

TTo run Reddit2TGBot, go to the virtual environment folder you created, activate it, and run the script:

```shell
source Reddit2TGBot/bin/activate
python Reddit2TGBot.py
```

The bot will continuously pull media content from the specified subreddits and share them to your Telegram channel. The script includes a delay to prevent overloading the Telegram API.
