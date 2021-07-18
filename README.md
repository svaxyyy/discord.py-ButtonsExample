# discord.py-ButtonsExample
- For guys which want to operate with Buttons in Python but dont know how to.

# Please leave a reaction on Discord that would be nice!
- ✅ / 🆗

# Installing and Importing
Install:
```cmd
pip install discord-components
```

Importing:
```py
from discord_components import DiscordComponents, Button, Select, SelectOption, Component
from discord_components import *


@client.event
async def on_ready():
    
    print('We have logged in as {0.user}'.format(client))
    DiscordComponents(client)

```

# responding:
- You should respond to an interaction, or defer it.
- Defering allows you to not respond for the next 15 minutes but you will have to respond later.
- But almost nobody will stare at the buttons for 15 minutes so you could just defer the interaction by type 6.

Editing the message:
- Responding with type 7 edits the original message!
 ```py
 # Change
await msg.edit(SOMETHING)
await interaction.respond(type=6)
# to
await interaction.respond(type=7, SOMETHING)
```


Sending a message:
Or you could just send an (ephemeral) message to the user with type 4.
```py
await interaction.respond(type=4, content="hi", ephemeral=False)
```

# How to get 2 buttons on 1 row?

`components=[[Button(), Button()]]`

# 2 buttons on 2 rows would be:

`components=[[Button(), Button()],[Button(), Button()]]`



# What is the Button Event?
- The event for button interactions is button_click. You could use them as a function like:

```py
@bot.event
async def on_button_click(interaction: Interaction):
    pass

or wait_for
res = await bot.wait_for("button_click", check = ..., timeout = ...)
```


# example code:

```py
@client.command()
async def buttons(ctx):

    b1 = Button(style=ButtonStyle.blue, label="Button1", emoji="💻")
    b2 = Button(style=ButtonStyle.green, label="Button2", emoji="💽") # not in use pls ignore
    b3 = Button(style=ButtonStyle.red, label="Button3", emoji="🔌")
    b4 = Button(style=ButtonStyle.grey, label="Button4", emoji="📻")
    b5 = Button(style=ButtonStyle.green, label="Button5",emoji="📻")
    embed = discord.Embed(color=0x4e4040, title=f"Click a Button!")
    embed.set_author(name=ctx.author.name, icon_url=ctx.author.avatar_url)
    embed.set_footer(text=ctx.guild.name, icon_url=ctx.guild.icon_url)
    msg = await ctx.send(embed=embed, components=[b1,b3, b4, b5])
    loop= True
    while loop:
        res = await client.wait_for("button_click")
        if res.component.label == "Setup":
            await res.respond(
                type=7,
                components = []
                )
            


        if res.component.label == "Button1":
            embed = Embed(title="Button1", description=f"You pressed Button1")
            await res.respond(
                type=7,
                components = []
                )
            await res.channel.send(embed=embed)

            
        if res.component.label == "Button2":
            await res.respond(
                type=7,
                components = []
                )
            
            
        if res.component.label == "Button3":
            await res.respond(
                type=7,
                components = []
            )
            await ctx.invoke(stop)
        if res.component.label == "Button4":
            await res.respond(
                type=7,
                components = []
            )
```



