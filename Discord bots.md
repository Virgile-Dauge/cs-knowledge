---
tags: [python, disnake]
---

# Setup 
https://discord.com/developers/applications/

# Base 

```python
from disnake.ext import commands

bot = commands.InteractionBot()

@bot.event
async def on_ready():

    print(f'We have logged in as {bot.user}')
```

# Example de slash command

```python
@bot.slash_command()
async def hello(inter: ApplicationCommandInteraction,
					msg: str=commands.Param(default=None),):
	"""Réponds avec un embed
       Parameters

        ----------
        msg: Texte à afficher
    """
    # Indique à l'utilisateur que le bot va répondre
    await inter.response.defer()

    embed = Embed(title='Coucou')
    
	if msg:
	    embed.description += f' 📍 {msg}\n'
	    
    # Édite le message avec la réponse finale
    await inter.edit_original_message(embed=embed)
```

# Interfaces interactives
[[discord bot views]]