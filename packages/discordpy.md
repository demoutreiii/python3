# Table of Contents
- [Official Documentation](#official-documentation)
- [Installation](<#installation>)
- [QuickStart](<#quickstart>)
- [Application Commands](<#application-commands>)
  - [Slash Commands](<#slash-commands>)
    - [Command Options](<#command-options>)
    - [Command Choices](<#command-choices>)
    - [Command Autocompletes](<#command-autocompletes>)
    - [Construct](<#construct>)
  - [Context Menu Commands](<#context-menu-commands>)
    - [Member Context Menu Commands](<#member-context-menu-commands>)
    - [User Context Menu Commands](<#user-context-menu-commands>)
    - [Message Context Menu Commands](<#message-context-menu-commands>)
    - [Construct](<#construct-1>)
  - [Guild-Specific Application Commands](<#guild-specific-application-commands>)
  - [User-Installable Application Commands](<#user-installable-application-commands>)
  - [Responding to an Interaction](<#responding-to-an-interaction>)
    - [Sending a message](<#sending-a-messsage>)
    - [Deferring the response](<#deferring-the-response>)
    - [Sending a modal](<#sending-a-modal>)
  - [Registering Application Commands](<#registering-application-commands>)
- [Components](<#components>)
  - [Sending a Message with Components](<#sending-a-message-with-components>)
  - [View](<#view>)
    - [Adding an Item to the View](<#adding-an-item-to-the-view>)
    - [Handling View Timeouts](<#handling-view-timeouts>)


# Official Documentation
For official documentation on the library, visit [discordpy.readthedocs.io/en/stable](<https://discordpy.readthedocs.io>).

**Indices**:
- [Getting Started](<https://discordpy.readthedocs.io/en/stable/#getting-started>)
  - [Introduction](<https://discordpy.readthedocs.io/en/stable/intro.html>)
  - [QuickStart](<https://discordpy.readthedocs.io/en/stable/quickstart.html>)
  - [Setting Up Logging](<https://discordpy.readthedocs.io/en/stable/logging.html>)
  - [Creating a Bot Account](<https://discordpy.readthedocs.io/en/stable/discord.html>)
  - [A Primer to Gateway Intents](<https://discordpy.readthedocs.io/en/stable/intents.html>)
  - [Examples](<https://github.com/Rapptz/discord.py/tree/v2.5.2/examples>)
- [Getting Help](<https://discordpy.readthedocs.io/en/stable/#getting-help>)
  - [Frequently Asked Questions](<https://discordpy.readthedocs.io/en/stable/faq.html>)
  - Join the [discord.gg/dpy](<https://discord.gg/r3sSKJJ>) Discord server
  - Try the [index](<https://discordpy.readthedocs.io/en/stable/genindex.html>) or [searching](<https://discordpy.readthedocs.io/en/stable/search.html>)
  - Report bugs in the [issue tracker](<https://github.com/Rapptz/discord.py/issues>)
  - Ask in the [Github discussions page](<https://github.com/Rapptz/discord.py/discussions>)
- [Manuals](<https://discordpy.readthedocs.io/en/stable/#manuals>)
  - [API Reference](<https://discordpy.readthedocs.io/en/stable/api.html>)
  - [Interactions API Reference](<https://discordpy.readthedocs.io/en/stable/interactions/api.html>)
  - [discord.ext.commands API Reference](<https://discordpy.readthedocs.io/en/stable/ext/commands/api.html>)
    - [Commands](<https://discordpy.readthedocs.io/en/stable/ext/commands/commands.html>)
    - [Cogs](<https://discordpy.readthedocs.io/en/stable/ext/commands/cogs.html>)
    - [Extensions](<https://discordpy.readthedocs.io/en/stable/ext/commands/extensions.html>)
    - [API Reference](<https://discordpy.readthedocs.io/en/stable/ext/commands/api.html>)
  - [discord.ext.tasks API Reference](<https://discordpy.readthedocs.io/en/stable/ext/tasks/index.html>)
- [Meta](<https://discordpy.readthedocs.io/en/stable/#meta>)
  - [Changelog](<https://discordpy.readthedocs.io/en/stable/whats_new.html>)
  - [Version Guarantees](<https://discordpy.readthedocs.io/en/stable/version_guarantees.html>)
  - [Migrating to v2.0](<https://discordpy.readthedocs.io/en/stable/migrating.html>)
  - [Migrating to v1.0](<https://discordpy.readthedocs.io/en/stable/migrating.html#migrating-to-v1-0>)


# Installation
To install ` discord.py `, run the following command in a terminal:
```py
$ python -m pip install discord.py
```

# QuickStart
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


# Application Commands
Application commands, such as slash commands and context menu commands, allows you to handle commands better, without the need of the ` message_content ` intent.


## Slash Commands
There are multiple ways to create slash commands:

**1. Using ` @CommandTree.command() ` decorator.**
Your ` CommandTree ` instance can be found in the ` tree ` property of your bot. If you're using ` discord.Client ` class, you have to assign it yourself:
```py
from discord import Client, Intents
from discord.app_commands import CommandTree

client = Client(intents = Intents.default())
client.tree = CommandTree(client)
```

Example:
```py
from discord import Interaction

@bot.tree.command()
async def sample(interaction: Interaction) -> None: ...
```

**2. Using ` @app_commands.command() ` decorator.**
This decorator requires you to use ` commands.Bot `.

The decorator can be used inside a ` Cog ` or ` GroupCog `:
```py
from discord import app_commands, Interaction
from discord.ext.commands import Cog, GroupCog

# Inside a Cog:
class SampleCog(Cog):
  @app_commands.command()
  async def sample(self, interaction: Interaction) -> None: ...
  # /sample

# Inside a GroupCog:
class SampleGroupCog(GroupCog, name = "test"):
  @app_commands.command()
  async def sample(self, interaction: Interaction) -> None: ...
    # /test sample
```

If the decorator is created outside a cog, you have to manually add it to the ` CommandTree ` yourself:
```py
from discord import app_commands, Interaction

@app_commands.command()
async def sample(interaction: Interaction) -> None: ...

bot.tree.add_command(sample)
```

**3. Using ` @Group.command() ` decorator.**
Similarly to the ` @app_commands.command() ` decorator, this one can be done inside and outside a cog or group cog.

With a cog or group cog:
```py
from discord import Interaction
from discord.app_commands import Group
from discord.ext.commands import Cog, GroupCog

# Inside a Cog:
class SampleCog(Cog):
  sample = Group(name = "sample")

  @sample.command()
  async def test(self, interaction: Interaction) -> None: ...
    # /sample test


# Inside a GroupCog:
class SampleGroupCog(GroupCog, name = "sample"):
  test = Group(name = "test")

  @test.command()
  async def foo(self, interaction: Interaction) -> None: ...
    # /sample test foo
```

When done outside a cog or group cog, you have to add the ` Group ` object, not its commands:
```py
from discord import Interaction
from discord.app_commands import Group

sample = Group(name = "sample")

@sample.command()
async def test(interaction: Interaction) -> None: ...
  # /sample test

bot.tree.add_command(sample)
```


### Command Options
To append options to the command, simply append one or more argument to the function with its correspoding type annotation after the ` Interaction ` argument:
```py
from discord import Attachment, GuildChannel, Interaction, Member, User

# String option
@bot.tree.command()
async def sample(interaction: Interaction, string: str) -> None: ...

# Integer option
@bot.tree.command()
async def sample(interaction: Interaction, number: int) -> None: ...

# Boolean option
@bot.tree.command()
async def sample(interaction: Interaction, boolean: bool) -> None: ...

# Channel option
@bot.tree.command()
async def sample(interaction: Interaction, channel: GuildChannel) -> None: ...

# Member option
@bot.tree.command()
async def sample(interaction: Interaction, member: Member) -> None: ...

# User option
@bot.tree.command()
async def sample(interaction: Interaction, user: User) -> None: ...

# Attachment option
@bot.tree.command()
async def sample(interaction: Interaction, attachment: Attachment) -> None: ...
```

You can make a command option be optionally filled with ` typing.Optional ` or assigning a default value to the argument:
```py
from discord import Interaction
from typing import Optional

# Using typing.Optional
@bot.tree.command()
async def sample(interaction: Interaction, string: Optional[str]) -> None: ...

# Setting a default value
@bot.tree.command()
async def sample(interaction: Interaction, string: str = "Hello world") -> None: ...
```


### Command Choices
Similarly to command options, choices lets the user type a value to the option, except the values are only limited to what's given to the command.

There are two ways to append choices to the command:

**1. Using ` @app_commands.choices() ` decorator.**
The decorator takes in keyword arguments. These arguments must be passed with a list of ` Choice ` objects whose ` value ` matches the type annotation of its corresponding argument.
```py
from discord import Interaction
from discord.app_commands import Choice, choices

@bot.tree.command()
@choices(
  languages = [
    Choice(name = "Python", value = "py"),
    Choice(name = "JavaScript", value = "js)
  ]
)
async def sample(interaction: Interaction, languages: str) -> None: ...
```

**2. Using ` Literal ` type hinting.**
All values inside the type hint must have the same types.
```py
from discord import Interaction
from typing import Literal

@bot.tree.command()
async def sample(interaction: Interaction, languages: Literal["py", "js"]) -> None: ...
```


### Command Autocompletes
Autocompletes allow you to have dynamic set of choices that relies on certain criterias given the typed out text by the user.

[` @autocomplete() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.autocomplete>) decorator is used to configure the autocomplete handler of the slash command option. The autocomplete handler takes two arguments: the [` Interaction `](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction) object; and the current string of text the user has typed out.

```py
async def numbers_autocomplete(interaction: Interaction, current: str) -> list[Choice]:
  numbers: dict[str, int] = { "one": 1, "two": 2, "three": 3 }
  return [ Choice(name = name, value = numbers.get(name)) for name in numbers if current.lower() in name.lower() ]


@app_commands.command()
@app_commands.autocomplete(number = numbers_autocomplete)
async def sample(interaction: Interaction, number: int) -> None:
  ...
```

> [!NOTE]
> Autocompletes are not strict and the user can input any text they want despite the value not as valid as an choice.


### Construct
**1. Command Name**
The name of the slash command will default to the name of the function the decorator is attached to. If you wish to change its name, pass in the ` name ` parameter to the ` @command() ` decorator:
```py
from discord import Interaction

@bot.tree.command(name = "test")
async def sample(interaction: Interaction) -> None: ...
  # /test
```

**2. Command Description**
To set the description for the command, pass the ` description ` parameter to the ` @command() ` decorator. If not specified, it defaults to an ellipsis ` ... ` in the UI:
```py
from discord import Interaction

@bot.tree.command(description = "Hello world")
async def sample(interaction: Interaction) -> None: ...
```


## Context Menu Commands
Context menu commands can be ran when you right-click a message or user/member and are found under the **Apps** section.

To create a context menu command, we are to use the ` @CommandTree.context_menu() ` decorator. Unlike slash commands, there are two required arguments for the context menu command's callback: the ` Interaction ` object, and the context at which this command can be ran on, i.e to a ` Member `, ` User `, or ` Message `.


### Member Context Menu Commands
These types of context menu commands can be ran on a guild member. The second argument is a ` Member ` object, the guild member that the command was actioned on.
```py
from discord import Interaction, Member

@bot.tree.context_menu()
async def sample(interaction: Interaction, member: Member) -> None: ...
```


### User Context Menu Commands
These types of context menu commands can be ran on a user. The second argument is a ` User ` object, the user that the command was actioned on.
```py
from discord import Interaction, User

@bot.tree.context_menu()
async def sample(interaction: Interaction, user: User) -> None: ...
```

This can also be union'd with the ` Member ` type:
```py
from discord import Interaction, Member, User
from typing import Union

@bot.tree.context_menu()
async def sample(interaction: Interaction, user: Union[Member, User]) -> None: ...
```


### Message Context Menu Commands
These types of context menu commands can be ran on a message. The second argument is a ` Message ` object, the message that the command was actioned on.
```py
from discord import Interaction, Message

@bot.tree.context_menu()
async def sample(interaction: Interaction, message: Message) -> None: ...
```


### Construct
**1. Command Name**
Unlike slash commands, the name of the context menu commands can contain uppercase letters and spaces. These can be set inside the ` @context_menu() ` decorator:
```py
from discord import Interaction, Member, User
from typing import Union

@bot.tree.context_menu(name = "Say Hello")
async def sample(interaction: Interaction, user: Union[Member, User]) -> None: ...
```


## Guild-Specific Application Commands
Application commands can be registered as guild-specific, meaning, they'll only appear on the guilds you specified. There are two ways to construct the application command as guild-specific: passing the ` guild ` **or** ` guilds ` parameter to the [` @CommandTree.command() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.command>) decorator; or attaching the [` @app_commands.guilds() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guilds>) decorator.

```py
@bot.tree.command(guild = GUILD_ID)
async def sample(interaction: Interaction) -> None:
  ...
```

> [!NOTE]
> When registering guild-specific commands, make sure the Guild IDs in the decorators and in your [` async CommandTree.sync() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync>) match.


## User-Installable Application Commands
User-installable application commands allows you to use the application commands anywhere (as configured in the installation contexts) without the need of the bot user's presence in that context, e.g. in a server, DM or Group DM.

To configure an application command to be user-installable, ` users ` parameter of the [` @allowed_installs() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.allowed_installs>) is set to ` True `, or the [` @user_install() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.user_install>) is attached.

```py
@app_commands.command()
@allowed_installs(users = True)
async def sample(interaction: Interaction) -> None:
  ...
```

To set on which contexts the application command can be used, [` @allowed_contexts() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.allowed_contexts>) is provided.

**Parameters**:
- ` guilds `: ` bool ` = Whether the application command is executable in a Discord server.
- ` dms `: ` bool ` = Whether the application command is executable in the bot's DM.
- ` private_channels `: ` bool ` = Whether the application command is executable in DMs and Group DMs other than the bot's.

```py
@app_commands.command()
@user_install()
@allowed_contexts(guilds = True, dms = True, private_channels = True)
async def sample(interaction: Interaction) -> None:
  ...
```


## Responding to an Interaction
The ` response ` property of an ` Interaction ` object returns an ` InteractionResponse ` instance which contains methods of acknowledging the interaction.

> [!NOTE]
> You can only respond to an interaction **once**.


### Sending a messsage
Commonly, responding to the interaction is done via ` async InteractionResponse.send_message() `, which is similar to ` async Messageable.send() `.
```py
from discord import Interaction

@bot.tree.command()
async def sample(interaction: Interaction) -> None:
  await interaction.response.send_message("Hello world!")
```


### Deferring the response
By default, you are to acknowledge the interaction within 3 seconds, otherwise it will invalidate. If you wish to respond to the interaction later than 3 seconds, call ` async InteractionResponse.defer() `. To update the deferred response, the ` Interaction.followup ` property is used.
```py
from asyncio import sleep
from discord import Interaction

@bot.tree.command()
async def sample(interaction: Interaction) -> None:
  await interaction.response.defer()
  await sleep(5) # Wait 5 seconds
  await interaction.followup.send("Hello world")
```

> [!NOTE]
> If the interaction type is a slash command or context menu command, ` thinking ` parameter will always be ` True `.


### Sending a modal
To respond to an interaction with a modal, call ` async InteractionResponse.send_modal() ` with a ` Modal ` object passed into it.
```py
from discord import Interaction
from discord.ui import Modal

class SampleModal(Modal): ...

@bot.tree.command()
async def sample(interaction: Interaction) -> None:
  await interaction.response.send_modal(SampleModal())
```


## Registering Application Commands
For the application commands to show up, you have to register them first. This is done via calling [` async CommandTree.sync() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync>) and passing in the necessary arguments. Your [` CommandTree `](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree) object can be accessed from your [` Bot.tree `](<https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.tree>) property.

If you are using the [` Client `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Client>) class, you have to set the attribute yourself, passing your ` Client ` object to the [` CommandTree `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree>) constructor.

```py
client: Client = Client(...)
client.tree: CommandTree = CommandTree(client)
```

**Parameters**:
- **guild**: Optional[[` Snowflake `](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake)] = the guild-specific commands to register.

**Returns**: List[[` AppCommand `](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand)]

> [!CAUTION]
> You must not register your application commands automatically, e.g. in ` on_ready ` event, as this can cause your application to hit rate limit. Instead, have it done manually via command or something else ideal to your liking.

> [!CAUTION]
> If you are to do it through commands, you have to ensure that you, the bot owner/developer, can only run the command and not unwanted anybody else.

```py
@bot.command()
@commands.is_owner()
async def sync(ctx: Context) -> None:
  await ctx.tree.sync()
```


# Components


The components supported by Discord are:

- [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow>)

- [` Button `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button>)

- [` Container Component `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container>)

- [` FileComponent `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent>)

- [` MediaGalleryComponent `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent>)

- [` SectionComponent `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent>)

- [` SelectMenu `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectMenu>)

- [` SeparatorComponent `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent>)

- [` TextDisplay `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay>)

- [` TextInput `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput>)

- [` ThumbnailComponent `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent>)


## Sending a Message with Components

Components can be sent in a message by passing the ` view ` parameter in [` async Messageable.send() `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send>), [` async InteractionResponse.send_message() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_message>), [` async InteractionResponse.edit_message() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.edit_message>), or [` async Webhook.send() `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Webhook.send>). The object passed can either be a [` View `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View>) or [` LayoutView `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView>) object.

```py
@tree.command()
async def sample(interaction: Interaction) -> None:
  view: View = View()
  view.add_item(Button(...))
  await interaction.response.send_message(view = view)
```


## View

[` View `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View>) class is used to create a UI in Discord.

This class only supports the following components:

- [` Button `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button>)
- [` Select `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select>)
  - [` ChannelSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ChannelSelect>)
  - [` RoleSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.RoleSelect>)
  - [` MentionableSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#mentionableselect>)
  - [` UserSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#userselect>)

` View ` does not support "Components V2" components, you must use [` LayoutView `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView>) for them.


### Adding an Item to the View

There are two ways an item can be added:

[` def View.add_item() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.add_item>) is called to add an item to the instance. This method takes one argument: the [` Item `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item>) object to add to the view.

```py
@tree.command()
async def sample(interaction: Interaction) -> None:
  view: View = View()
  button: Button = Button(...)
  view.add_item(button)
  await interaction.response.send_message(view = view)
```

When a user-defined class is subclassed with ` View `, you can use directly create the components inside the class.

```py
class SampleView(View):
  @button(label = "Sample Button")
  async def button_callback(self, interaction: Interaction, button: Button) -> None:
    await interaction.response.send_message("You clicked a button!")

  @select(cls = UserSelect)
  async def select_callback(self, interaction: Interaction, select: UserSelect) -> None:
    await interaction.response.send_message(f"Hello, {select.values[0].mention}!")
```


### Handling View Timeouts

` View ` objects have a default timeout of ` 180 ` seconds. This can be modified in the constructor, and a ` None ` can be passed to indicate that there is no timeout.

The timeout resets when a message component interaction is created from the view. Once the timeout exceeds without being explicitly stopped, [` async View.on_timeout() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.on_timeout>) is called. This method can be overridden to handle view timeouts.

```py
class SampleView(View):
  async def on_timeout(self) -> None:
    self.stop()
    print("View has timed out.")
```

The method does not take any arguments. For you to be able to edit the message it belongs to, you must create an instance variable on the view containing the [` InteractionMessage `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage>) or [` Message `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Message>) object.

```py
class SampleView(View):
  def __init__(self) -> None:
    super().__init__()
    self._message: Union[InteractionMessage, Message] = ...

  async def on_timeout(self) -> None:
    self.stop()
    if self._message not in (Ellipsis, None):
      await self._message.edit(...)

@tree.command()
async def sample(interaction: Interaction) -> None:
  view: View = SampleView()
  await interaction.response.send_message(view = view)
  view._message: InteractionMessage = await interaction.original_response()

@bot.command()
async def sample(ctx: Context) -> None:
  view: View = SampleView()
  view._message: Message = await ctx.send(view = view)
```