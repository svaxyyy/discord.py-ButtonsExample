# discord.py-ButtonsExample
For guys which want to operate with Buttons in Python but dont know how to.

You should respond to an interaction, or defer it.
Defering allows you to not respond for the next 15 minutes but you will have to respond later.
But almost nobody will stare at the buttons for 15 minutes so you could just defer the interaction by type 6.

Editing the message:
Responding with type 7 edits the original message!
# Change
  await msg.edit(SOMETHING)
  await interaction.respond(type=6)
  # to
  await interaction.respond(type=7, SOMETHING)


Sending a message:
Or you could just send an (ephemeral) message to the user with type 4.
  await interaction.respond(type=4, content="hi", ephemeral=False)
