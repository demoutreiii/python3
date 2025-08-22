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
  - [Editing a Message with New/Updated Components](<#editing-a-message-with-newupdated-components>)
  - [View](<#view>)
    - [Adding an Item to the View](<#adding-an-item-to-the-view>)
    - [Handling View Timeouts](<#handling-view-timeouts>)
    - [Setting Persistent Views](<#setting-persistent-views>)
  - [LayoutView](<#layoutview>)
    - [Adding an Item to the LayoutView](<#adding-an-item-to-the-layoutview>)
    - [Handling LayoutView Timeouts](<#handling-layoutview-timeouts>)
    - [Setting Persistent LayoutViews](<#setting-persistent-layoutviews>)
  - [Modal](<#modal>)
    - [Adding Components to a Modal](<#adding-components-to-a-modal>)
    - [Handling Modal Submissions](<#handling-modal-submissions>)
    - [Accessing Value of TextInputs](<#accessing-value-of-textinputs>)
  - [Button](<#button>)
    - [Creating a Button Object](<#creating-a-button-object>)
    - [Button Styles](<#button-styles>)
  - [Select Menus](<#select-menus>)
    - [Creating a Select Menu Object](<#creating-a-select-menu-object>)
    - [Handling Callbacks](<#handling-callbacks>)
    - [Options](<#options>)
      - [Adding an Option to a Select Menu](<#adding-an-option-to-a-select-menu>)
      - [Accessing Selected Options](<#accessing-selected-options>)
    - [Select](<#select>)
    - [ChannelSelect](<#channelselect>)
    - [RoleSelect](<#roleselect>)
    - [MentionableSelect](<#mentionableselect>)
    - [UserSelect](<#userselect>)
  - [TextInput](<#textinput>)
  - [Container](<#container>)
  - [File](<#file>)
  - [Label](<#label>)
  - [MediaGallery](<#mediagallery>)


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


## Editing a Message with New/Updated Components

Likewise with [sending a message with components](<#sending-a-message-with-components>), you pass a new ` View ` or ` LayoutView ` object, or the updated "state" of an existing one.

```py
class SampleButton(Button, label = "Disable Button"):
  def __init__(self: Self) -> None:
    super().__init__()

  async def callback(self: Self, interaction: Interaction) -> None:
    self.disabled: bool = True
    await interaction.response.edit_message(view = self.view)

view: View = View().add_item(SampleButton())
await channel.send(view = view)
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

**Parameters**:
- **timeout**: Optional[` float `] - timeout in seconds from last interaction with the UI before no longer accepting input. If ` None ` then there is no timeout. Defaults to ` 180.0 ` seconds.


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


### Setting Persistent Views

Your bot loses its views upon process restart when it's not persistent, i.e. it will not receive any message component interaction from non-persistent views.

To set up a persistent view, [` def Bot.add_view() `](<https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_view>) is called, and the view instance you want to make "persistent" is passed to the method. Optionally you can pass a Message ID to the method to "refresh" the state of an old view rather than having to send a new one.

```py
class SampleView(View, timeout = None): ...

bot.add_view(SampleView())
```

> [!NOTE]
> For the view to become persistent, [` View.timeout `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.timeout>) must be set to ` None `.


## LayoutView

[` LayoutView `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView>) differs from [` View `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View>) in that it supports all component types and uses what Discord refers to as "v2 components".

**Parameters**:
- **timeout**: Optional[` float `] - timeout in seconds from last interaction with the UI before no longer accepting input. If ` None ` then there is no timeout. Defaults to ` 180.0 ` seconds.


### Adding an Item to the LayoutView

Adding an item to the ` LayoutView ` object is similarly done with a ` View `. See how to [add an item to the ` View `](<#adding-an-item-to-the-view>).

```py
class SampleLayoutView(LayoutView):
  container: Container = Container(...)

@tree.command()
async def sample(interaction: Interaction) -> None:
  layout: LayoutView = SampleLayoutView()
  layout.add_item(Container(...))
  await interaction.response.send_message(view = layout)
```


### Handling LayoutView Timeouts

Handling ` LayoutView ` timeouts is similarly done with a ` View `. See how to [handle ` View ` timeouts](<#handling-view-timeouts>).

```py
class SampleLayoutView(LayoutView):
  def __init__(self) -> None:
    self._message: Union[InteractionMessage, Message] = ...

  async def on_timeout(self) -> None:
    self.stop()
    if self._message not in (Ellipsis, None):
      await self._message.edit(...)

@tree.command()
async def slash_command(interaction: Interaction) -> None:
  layout: LayoutView = SampleLayoutView()
  await interaction.response.send_message(view = layout)
  layout._message: InteractionMessage = await interaction.original_response()

@bot.command()
async def prefix_command(ctx: Context) -> None:
  layout: LayoutView = SampleLayoutView()
  layout._message: Message = await ctx.send(view = layout)
```


### Setting Persistent LayoutViews

Setting "persistent" ` LayoutView `s is similarly done with a ` View `. See how to [set up persistent ` View `](<#setting-persistent-views>)s.

```py
class SampleLayoutView(LayoutView, timeout = None): ...

bot.add_view(SampleLayoutView())
```


## Modal

[` Modal `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal>) represents a UI modal. This object must be inherited to create a modal popup window within Discord.

**Parameters**: *(All parameters are keyword-arguments)*
- **custom_id**: ` str ` - ID of the modal that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **timeout**: Optional[` float `] - timeout in seconds from last interaction with the UI before no longer accepting input. If ` None ` then there is no timeout. Defaults to ` None `.
- **title**: ` str ` - title of the modal. Can only be up to 45 characters.

```py
class SampleModal(Modal, title = "Sample Modal"):
  text: TextInput = TextInput(...)

  async def on_submit(self: Modal, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Your text: {self.text}")
```


### Adding Components to a Modal

There are two ways to add components to your modal.

**1. [` def Modal.add_item() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.add_item>) method**

This method takes one positional argument: the [` Item `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item>) to add to the modal.

```py
sample_modal: Modal = Modal(...)
text_input: TextInput = TextInput(...)
sample_modal.add_item(text_input)
```

**2. Setting as class variables in a subclassed modal**

```py
class SampleModal(Modal, ...):
  text1: TextInput = TextInput(...)
  text2: TextInput = TextInput(...)
  text3: TextInput = TextInput(...)
```

> [!NOTE]
> Currently you can only have up to 5 components in the modal.


### Handling Modal Submissions

When a modal is submitted by the user, i.e. clicking on the "Submit" button, the [` async Modal.on_submit() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_submit>) method is called. This method should be overriden, and takes two positional arguments: the [` Modal `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal>) itself, and the [` Interaction `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction>) that you receive.

```py
class SampleModal(Modal, ...):
  async def on_submit(self: Modal, interaction: Interaction) -> None:
    await interaction.response.send_message("Modal submitted!")
```


### Accessing Value of TextInputs

If subclassed, you can access the user's input value of a particular ` TextInput ` component via the class variable it's stored in, and the [` TextInput.value `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.value>) is accessed/referenced.

```py
class SampleModal(Modal, ...):
  text: TextInput = ...

  async def on_submit(self: Modal, interaction: Interaction) -> None:
    await interaction.response.send_message(f"You typed: {self.text.value}")
    # or
    await interaction.response.send_message(f"You typed: {self.text}")
```


## Button

[` Button `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button>) is used to create a UI button.

**Parameters**:
- **custom_id**: Optional[` str `] - ID of the button that gets received during an interaction. If this button is for a URL, it does not have a custom ID. Can only be up to 100 characters.
- **disabled**: ` bool ` - whether the button is disabled or not. Defaults to ` False `.
- **emoji**: Optional[Union[[` PartialEmoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji>), [` Emoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji>), ` str `]] - emoji of the button, if available.
- **label**: Optional[` str `] - label of the button. Can only be up to 80 characters.
- **id**: Optional[` int `] - ID of this component. Must be unique across the view.
- **row**: Optional[` int `] - relative row this button belongs to. Defaults to ` None `, which is automatic ordering. The row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.
- **sku_id**: Optional[` int `] - SKU ID this button sends you to. Can't be combined with ` url `, ` label `, ` emoji `, nor ` custom_id `.
- **style**: [` ButtonStyle `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle>) - *kwarg*; style of the button. Defaults to [` ButtonStyle.secondary `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.secondary>).
- **url**: Optional[` str `] - URL this button sends you to.


### Creating a Button Object

**1. Constructor**

```py
from collections.abc import Coroutine
from discord import Interaction
from discord.ui import Button

async def callback(self: Button, interaction: Interaction) -> None:
  await interaction.response.send_message("Button is clicked!")

button: Button = Button(label = "Click me!")
button.callback: Coroutine[None, [Button, Interaction], None] = callback
```

**2. SubClass**

```py
from discord import Interaction
from discord.ui import Button

class SampleButton(Button):
  def __init__(self: Button) -> None:
    super().__init__(label = "Click me!")

  async def callback(self: Button, interaction: Interaction) -> None:
    await interaction.response.send_message("Button is clicked!")
```

**3. [` @discord.ui.button() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.button>) decorator**

The function being decorated should have three parameters, ` self ` representing [` View `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View>), the [` Interaction `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction>) you receive, and the [` Button `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button>) being pressed. Parameters are not interchangeable.

```py
from discord import Interaction
from discord.ui import button, Button, View

class SampleView(View):
  def __init__(self: View) -> None:
    super().__init__()

  @button(label = "Click me!")
  async def sample_button(self: View, interaction: Interaction, button: Button) -> None:
    await interaction.response.send_message("Button is clicked!")
```


### Button Styles

| Style | Description | Alias |
|-------|-------------|-------|
| [` ButtonStyle.primary `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.primary>) | Represents a blurple button for the primary action. | [` ButtonStyle.blurple `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.blurple>) |
| [` ButtonStyle.secondary `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.secondary>) | Represents a grey button for the secondary action. | [` ButtonStyle.grey `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.grey>), [` ButtonStyle.gray `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.gray>) |
| [` ButtonStyle.success `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.success>) | Represents a green button for a successful action. | [` ButtonStyle.green `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.green>) |
| [` ButtonStyle.danger `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.danger>) | Represents a red button for a dangerous action. | [` ButtonStyle.red `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.red>) |
| [` ButtonStyle.link `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.link>) | Represents a link button. | [` ButtonStyle.url `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.url>)
| [` ButtonStyle.premium `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.premium>) | Represents a button denoting that buying a SKU is required to perform this action. |  |

[![Discord Button Styles](<https://guide.pycord.dev/assets/images/button-styles-6cde2084662b01fd98801e4444eb89ef.png>)](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle>)


## Select Menus

There are different types of select menus you can create. Select menus are represented to the user as a dropdown menu.
- [` Select `](<#select>)
- [` ChannelSelect `](<#channel-select>)
- [` RoleSelect `](<#role-select>)
- [` MentionableSelect `](<#mentionable-select>)
- [` UserSelect `](<#user-select>)


### Creating a Select Menu Object

**1. Constructor**

```py
from collections.abc import Coroutine
from discord import Interaction, SelectOption
from discord.ui import Select, View

async def select_callback(self: Select, interaction: Interaction) -> None:
  await interaction.response.send_message(f"You selected: {self.values[0]}")

options: list[SelectOption] = [...]
select: Select = Select(options = options)
select.callback: Coroutine[None, [Select, Interaction], None] = select_callback
view: View = View().add_item(select)
```

**2. SubClass**

```py
from discord import Interaction
from discord.ui import Select, View

class SampleSelect(Select):
  def __init__(self: Self) -> None:
    super().__init__(options = [...])

  async def callback(self: Select, interaction: Interaction) -> None:
    await interaction.response.send_message(f"You selected: {self.values[0]}")

view: View = View().add_item(SampleSelect())
```

**3. [` discord.ui.select() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.select>) decorator**

| Select Type | Resolved Values |
|-------------|-----------------|
| [` Select `](<#select>) | list[` str `] |
| [` UserSelect `](<#userselect>) | list[Union[[` Member `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Member>), [` User `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.User>)]] |
| [` RoleSelect `](<#roleselect>) | list[[` Role `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Role>)] |
| [` MentionableSelect `](<#mentionableselect>) | list[Union[[` Role `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Role>), [` Member `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Member>), [` User `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.User>)]] |
| [` ChannelSelect `](<#channelselect>) | list[Union[[` AppCommandChannel `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel>), [` AppCommandThread `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread>)]] |

**Parameters**: *(All parameters are keyword-arguments)*
- **channel_types**: list[[` ChannelType `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType>)] - types of channels to show in the select menu. Defaults to all channels. Can only be used with [` ChannelSelect `](<#channel-select>) instances.
- **cls**: Union[[` Select `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select>), [` UserSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.UserSelect>), [` RoleSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.RoleSelect>), [` MentionableSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MentionableSelect>), [` ChannelSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ChannelSelect>)] - class to use for the select menu. Defaults to [` SelectMenu `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select>). See the table above for the different values you can get from each select type.
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. It is recommended not to set this parameter to prevent conflicts. Can only be up to 100 characters.
- **default_values**: Sequence[[` Snwoflake `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake>)] - list of objects representing the default values for the select menu. Cannot be used with regular [` Select `](<#select>) instances. If ` cls ` is [` MentionableSelect `](<#mentionable-select>) and [` Object `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Object>) is passed, then the type must be specified in the constructor. Number of items must be in range of ` min_values ` and ` max_values `.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **id**: Optional[` int `] - ID of the component. Must be unique across the view.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 0 ` and ` 25 `.
- **options**: list[[` SelectOption `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption>)] - list of options that can be selected in this menu. This can only be used with [` Select `](<#select>) instances. Can only contain up to 25 items.
- **placeholder**: Optional[` str `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.

```py
from discord import Interaction
from discord.ui import select, Select, View

class SampleView(View):
  @select(options = [...])
  async def sample_select(self: View, interaction: Interaction, select: Select) -> None:
    await interaction.response.send_message(f"You selected: {select.values[0]}")
```


### Handling Callbacks

The asynchronous ` callback ` method of a select menu object is overriden, which is called when an interaction is created from the component. This method takes one required positional argument, an [` Interaction `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction>) object.

```py
class SampleSelect(Select):
  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"You selected: {self.values[0]}")
```

When [` @select() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.select>) decorator is used, the function it's attached to becomes its callback.

```py
class SampleView(View):
  @select(...)
  async def sample_select(self: View, interaction: Interaction, select: Select) -> None:
    await interaction.response.send_message(f"You selected: {self.values[0]}")
```


### Options

[` SelectOption `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption>) is used to create an option for a select menu.

**Parameters**: *(All parameters are keyword-arguments)*
- **label**: ` str ` - label of the option. This is displayed to users. Can only be up to 100 characters.
- **value**: ` str ` - value of the option. This is not displayed to users. If not provided when constructed then it defaults to the label. Can only be up to 100 characters.
- **description**: Optional[` str `] - additional description of the option, if any. Can only be up to 100 characters.
- **emoji**: Optional[Union[[` Emoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji>), [` PartialEmoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji>), ` str `]] - emoji of the option, if available. This can either be a string representing the custom or unicode emoji or an instance of [` PartialEmoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji>) or [` Emoji `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji>).
- **default**: ` bool ` - whether this option is selected by default.


#### Adding an Option to a Select Menu

> [!NOTE]
> You are not able to add "custom" options to [` ChannelSelect `](<#channelselect>), [` RoleSelect `](<#roleselect>), [` MentionableSelect `](<#mentionableselect>), and [` UserSelect `](<#userselect>) instances.

To add an option to a [` Select `](<#select>) instance, ` options ` parameter can be passed to the constructor containing a list of [` SelectOption `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption>) instances, or via the [` def Select.add_option() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select.add_option>) method (its parameters are similar to that stated in [` SelectOption `](<#options>)):

```py
from discord.ui import Select

sample_select: Select = Select(options = [...])
sample_select.add_option(...)
```

When the [` @select() `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.select>) decorator is used, the ` options ` parameter is used for appending options.

```py
from discord import Interaction
from discord.ui import select, Select, View

class SampleView(View):
  @select(options = [...])
  async def sample_select(self: View, interaction: Interaction, select: Select) -> None:
    await interaction.response.send_message(f"You selected: {select.values[0]}")
```


#### Accessing Selected Options

The ` values ` property returns a list of strings that corresponds to the [value](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.value>)s of selected options of the select menu.

```py
from discord import Interaction, SelectOption
from discord.ui import Select

class SampleSelect(Select):
  def __init__(self: Select) -> None:
    super().__init__(
      options = [
        SelectOption(label = "One"),
        SelectOption(label = "Two"),
        SelectOption(label = "Three")
      ]
    )

  async def callback(self: Select, interaction: Interaction) -> None:
    await interaction.response.send_message(f"You selected: {self.values[0]}")
```


### Select

[` Select `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select>) represents a UI select menu with a list of custom options.

**Parameters**:
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 0 ` an ` 25 `.
- **options**: list[` SelectOption `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption>) - list of options that can be selected in this menu. Can only contain up to 25 items.
- **placeholder**: Optional[` str `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **required**: ` bool ` - whether the select is required. Only applicable within modals.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. The row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.
- **id**: Optional[` int `] - ID of the component. Must be unique across the view.

```py
class SampleSelect(Select):
  def __init__(self: Self) -> None:
    super().__init__(options = [...])

  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Selected option: {self.values[0]}")
```


### ChannelSelect

[` ChannelSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ChannelSelect>) represents a UI select menu with a list of predefined options with the current channels in the guild.

> [!NOTE]
> If used in a private message with a user, no channels will be displaye to the user.

**Parameters**: *(All parameters are keyword-arguments)*
- **channel_types**: list[[` ChannelType `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType>)] - types of channels to show in the select menu. Defaults to all channels.
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **default_values**: Sequence[[` Snowflake `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake>)] - list of objects representing the channels that should be selected by default. Number of items must be in range of ` min_values ` and ` max_values `.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **id**: Optional[` int `] - ID of the component. Must be unique across the view.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 0 ` and ` 25 `.
- **placeholder**: Optional[` str `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.

```py
class SampleSelect(ChannelSelect):
  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Selected channel: {self.values[0]}")
```


### RoleSelect

[` RoleSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.RoleSelect>) represents a UI select menu with a list of predefined options with the current roles of the guild.

> [!NOTE]
> If used in a private message with a user, no roles will be displayed to the user.

**Parameters**: *(All parameters are keyword-arguments)*
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **default_values**: Sequence[[` Snowflake `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake>)] -list of objects representing the roles that should be selected by default. Number of items must be in range of ` min_values ` and ` max_values `.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **id**: Optional[` int `] - ID of the component. Must be unique across the view.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 0 ` and ` 25 `.
- **placeholder**: Optional[` int `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.

```py
class SampleSelect(RoleSelect):
  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Selected role: {self.values[0]}")
```


### MentionableSelect

[` MentionableSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MentionableSelect>) represents a UI select menu with a list of predefined options with the current members and roles in the guild.

> [!NOTE]
> If sent in a private message, it will only allow the user to select the client or themselves. Every selected option in a private message will resolve to a [` User `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.User>). It will not give the user any roles to select.

**Parameters**: *(All parameters are keyword-arguments)*
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **default_values**: Sequence[[` Snowflake `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake>)] - list of objects representing the users/roles that should be selected by default. If [` Object `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Object>) is passed, then the type must be specified in the constructor. Number of items must be in range of ` min_values ` and ` max_values `.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **id**: Optional[` int `] - ID of the component. Must be unique across the view.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 0 ` and ` 25 `.
- **placeholder**: Optional[` str `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.

```py
class SampleSelect(MentionableSelect):
  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Selected mentionable: {self.values[0]}")
```


### UserSelect

[` UserSelect `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.UserSelect>) represents a UI select menu with a list of predefined options with the current members of the guild.

> [!NOTE]
> If used in a private message, it will only allow the user to select the client or themselves. Every selected option in a private message will resolve to a [` User `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.User>).

**Parameters**: *(All parameters are keyword-arguments)*
- **custom_id**: ` str ` - ID of the select menu that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **default_values**: Sequence[[` SNowflake `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake>)] - list of objects representing the users that should be selected by default. Number of items must be in range ` min_values ` and ` max_values `.
- **disabled**: ` bool ` - whether the select is disabled or not. Defaults to ` False `.
- **id**: Optional[` int `] - ID of the component. This must be unique across the view.
- **max_values**: ` int ` - maximum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 ` and ` 25 `.
- **min_values**: ` int ` - minimum number of items that must be chosen for this select menu. Defaults to ` 1 ` and must be between ` 1 `  and ` 25 `.
- **placeholder**: Optional[` str `] - placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
- **row**: Optional[` int `] - relative row this select menu belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
  > [!NOTE]
  > This parameter is ignored when used in an [` ActionRow `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow>) or v2 component.

```py
class SampleSelect(UserSelect):
  async def callback(self: Self, interaction: Interaction) -> None:
    await interaction.response.send_message(f"Selected user: {self.values[0]}")
```


## TextInput

[` TextInput `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput>) represents a UI text input in a modal.

**Parameters**: *(All parameters are keyword-arguments)*
- **custom_id**: ` str ` - ID of the text input that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
- **default**: Optional[` str `] - default value of the text input. Can only be up to 4000 characters.
- **id**: Optional[` int `] - ID of the component. This must be unique across the view.
- **label**: Optional[` str `] - label to display above the text input. Can only be up to 45 characters.
  > [!WARNING]
  > This parameter is deprecated, use [` Label `](<#label>) instead.
- **max_length**: Optional[` int `] - maximum length of the text input. Must be between ` 1 ` and ` 4000 `.
- **min_length**: Optional[` int `] - minimum length of the text input. Must be between ` 0 ` and ` 4000 `.
- **placeholder**: Optional[` str `] - placeholder text to display when the text input is empty. Can only be up to 100 characters.
- **required**: ` bool ` - whether the text input is required. Defaults to ` True `.
- **row**: Optional[` int `] - relative row this text input belongs to. Defaults to ` None `, which is automatic ordering. Row number must be between ` 0 ` and ` 4 `.
- **style**: [` TextStyle `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle>) - style of the text input. Defaults to [` TextStyle.short `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle.short>).


## Container

[` Container `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container>) represents a UI container. This is a top-level layout component that can only be used on [` LayoutView `](<#layoutview>) and can contain [` ActionRow `](<#actionrow>)s, [` TextDisplay `](<#textdisplay>)s, [` Section `](<#section>)s, [` MediaGallery `](<#mediagallery>)s, [` File `](<#file>)s, and [` Separator `](<#separator>)s in it.

**Parameters**: *(All parameters are keyword-arguments)*
- ***children**: [` Item `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item>) - initial children of this container.
- **accent_colour**: Optional[Union[[` Colour `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour>), ` int `]] - colour of the container. Defaults to ` None `.
- **accent_color**: Optional[Union[[` Colour `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour>), ` int `]] - color of the container. Defaults to ` None `.
- **spoiler**: ` bool ` - whether to flag this container as a spoiler. Defaults to ` False `.
- **id**: Optional[` int `] - ID of this component. Must be unique across the view.


```py
class SampleContainer(Container):
  text_display: TextDisplay = ...
  action_row: ActionRow = ...
  section: Section = ...
  media_gallery: MediaGallery = ...
  separator: Separator = ...
  file: File = ...

layout: LayoutView = LayoutView(...)
layout.add_item(SampleContainer())
```


## File

[` File `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File>) represents a UI file component. This is a top-level layout component that can only be used on a [` LayoutView `](<#layoutview>).

**Parameters**:
- **media**: Union[[` UnfurledMediaItem `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.UnfurledMediaItem>), [` discord.File `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.File>), ` str `] - this file's media. If this is a string it must point to a local file uploaded within the parent view of this item, and must meet the ` attachment://<filename> ` format.
- **spoiler**: ` bool ` - *kwarg*; whether to flag this file as a spoiler. Defaults to ` False `.
- **id**: Optional[` int `] - *kwarg*; ID of this component. Must be unique across the view.

```py
class SampleLayout(LayoutView):
  file: File = File('attachment://text.txt')
```


## Label

[` Label `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label>) represents a UI label within a modal.

**Parameters**: *(All parameters are keyword-arguments)*
- **text**: ` str ` - text to display above the input field. Can only be up to 45 characters.
- **description**: Optional[` str `] - description text to display right below the label text. Can only be up to 100 characters.
- **component**: Union[[` TextInput `](<#textinput>), [` Select `](<#select>)] - component to display below the label.
- **id**: Optional[` int `] - ID of the component. This must be unique across the view.

```py
class SampleModal(Modal, ...):
  label1: Label = Label(text = "Hello", component = TextInput(...))
  label2: Label = ...
```


## MediaGallery

[` MediaGallery `](<https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery>) represents a UI media gallery.

Can contain up to 10 [` MediaGalleryItem `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.MediaGalleryItem>)s. This is a top-level layout component that can only be used on [` LayoutView `](<#layoutview>).

**Parameters**:
- ***items**: [` MediaGalleryItem `](<https://discordpy.readthedocs.io/en/stable/api.html#discord.MediaGalleryItem>) - initial items of this gallery.
- **id**: Optional[` int `] - *kwarg*; ID of this component. Must be unique across the view.

```py
class SampleLayout(LayoutView):
  gallery: MediaGallery = ...
```