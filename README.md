# discord.py-ButtonsExample
For guys which want to operate with Buttons in Python but dont know how to.

# responding:
You should respond to an interaction, or defer it.
Defering allows you to not respond for the next 15 minutes but you will have to respond later.
But almost nobody will stare at the buttons for 15 minutes so you could just defer the interaction by type 6.

Editing the message:
Responding with type 7 edits the original message!
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






