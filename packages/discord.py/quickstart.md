### QuickStart
Using ` discord.Client `:
```py
from discord import Client, Intents


# Configure intents
intents: Intents = Intents.default()

# Initiate Client instance
client = Client(intents = intents)

# Listen for when the bot is ready
@client.event
async def on_ready() -> None:
  print(f"{client.user} is online.")

# Run and connect your bot to Discord
client.run("DISCORD_BOT_TOKEN")
```

Using ` commands.Bot `:
```py
from discord import Intents
from discord.ext.commands import Bot


# Configure intents
intents: Intents = Intents.default()

# Initiate Bot instance
bot = Bot(
  command_prefix = "!",
  intents = intents
)

# Listen for when the bot is ready
@bot.listen()
async def on_ready() -> None:
  print(f"{bot.user} is online.")

# Run and connect your bot to Discord
bot.run("DISCORD_BOT_TOKEN")
```