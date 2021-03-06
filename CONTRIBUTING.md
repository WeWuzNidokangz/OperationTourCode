# How Do I Submit a Request for Changes?

If you want to update banlists or submit a new tour, this is a good tutorial for making pull requests to GitHub without needing to use the command line:-

https://www.nexmo.com/legacy-blog/2020/10/01/how-to-create-a-pull-request-with-github-desktop

The clone button for [OperationTourCode](https://github.com/TheNumberMan/OperationTourCode) is here:-

![The clone button is here](https://i.imgur.com/JSnwfC5.png)

In contrast to the advice in this tutorial, you shouldn't need to write a description beyond a title for most simple changes like updating bans. Pull requests from Mashups staff will usually be accepted unless there is a technical issue that could cause problems for a tour code or Iolanthe, etc.

Although this is mentioned in the tutorial, it is worth emphasising that it is a good idea to create a new branch for each pull request so that a subsequent pull request can be accepted, even if there is a problem holding up a prior one.

When a pull request has been accepted, and tour code or other content has been updated, the changes can be reflected to Iolanthe using the ?refresh command.

# Preferred Tour Code Style

**Use correct formatting**

Please write the names of formats and bans of Pokemon, items, etc with proper spacing and capitalisation, in the same way that they are displayed in the "Banlist/Ruleset" of built-in formats when the !tier/!om command is used on Pokemon Showdown. E.g. write "-Gorilla Tactics" rather than "-gorillatactics".

  

Although lower-case parameters without alphanumeric characters ("IDs") are recognised by the tour code parser, the formatting used in tour codes is mostly preserved when it is shown to users in the "This tournament includes:" boxout. If the rules are formatted correctly, they will be easier for users to read, and maintain a sense of consistency and familiarity with how built-in format descriptions are displayed with the !tier/!om command.

  

Good example:-

  

> This tournament includes:
> 
> Added bans - Comatose, Contrary, Fluffy, Fur Coat, Gorilla Tactics,
> Huge Power, Ice Scales, Illusion, Imposter, Innards Out, Intrepid
> Sword, Libero, Neutralizing Gas, Parental Bond, Protean, Pure Power,
> Simple, Stakeout, Speed Boost, Water Bubble, Wonder Guard, Shedinja,
> Hypnosis, Sing, Sleep Powder, Keldeo, Terrakion, Zeraora, Chandelure,
> Melmetal, Electrify, Volcarona, Blacephalon, Tapu Koko, Thundurus,
> Archeops, Zygarde, Regigigas, Tinted Lens, Urshifu, Latios
> 
> Removed bans - Darmanitan, Darmanitan-Galar, Dracovish, Gengar,
> Porygon-Z, Zygarde-10%, Landorus-Base, Mamoswine, Urshifu-Rapid-Strike
> 
> Added restrictions - Transform, No Retreat, Glacial Lance, Oblivion
> Wing
> 
> Added rules - 2 Ability Clause
> 
> Removed rules - Obtainable Abilities

  

Bad example:-

  

> This tournament includes:
> 
> Added bans - ZYDOG
> 
> Removed bans - landot
> 
> Added rules - g e n 8 c a m O m O n s

  

**Do not use aliases inside tour codes**

E.g. write "[Gen 8] Random Battle" rather than "randbats".

  

In addition to the above reasoning, while the tour code parser can recognise aliases when creating a tour, if the tour code is converted to a challenge code, the challenge code parser cannot, meaning that the challenge will fail (tested on Showdown source 2021/03/30).

  

Bad example:-

  

> /challenge randbats @@@gen8shared
> power,inversemod,scalemonsmod,gen8camomons

  

If a user tries to challenge using this code, the following error will be shown:-

  

> Your selected format is invalid:
> 
>   
> 
> - Unrecognized format "gen8randbats"

  

Good example:-

  

> /challenge [Gen 8] Random Battle @@@[Gen 8] Shared Power,[Gen 8]
> Camomons,Inverse Mod,Scalemons Mod

  

(Challenges made using this code should succeed.)

  

In general, converting formatted text to IDs is a lossy operation. E.g. consider "Porygon-Z" => "porygonz": without context, we cannot easily determine from the latter string whether or where there were spaces, capitals or punctuation in the former. Because of this, even if we can envision Showdown making future improvements in this area, it will always be safer to start by supplying properly formatted text in the tour code, and then allow applications the option to convert it to IDs as appropriate, rather than beginning with IDs.

  

# Aliasing

  

Aliases are alternate names for mashup formats. They can be used by applications like Iolanthe to refer to tour codes using shorter or multiple strings without changing the name of the tour code file itself, which would break its URL and could make it too abbreviated to easily understand. For example, "stablc" is an alias for "gen8stabmonslittlecup".

  

OperationTourCode aliases are defined in the following file:-

  

https://github.com/TheNumberMan/OperationTourCode/blob/master/metadata/aliases.txt

  

An aliases for a format that doesn't have any yet can be added in a new line with the following form:-

  

[Name of tour file]: [New alias 1]

  

E.g. in the case of gen8staaabmons.tour, this might be:-

  

gen8staaabmons: staaab

  

※ It isn't necessary to include "gen8" as part of the aliases themselves, as Iolanthe will automatically try removing "gen8" from the beginning of a string when searching for aliases. In the above example, "gen8staaabmons", "gen8staaab", "staaabmons" and "staaab" will all refer to the gen8staaabmons tour code.

  

You can add multiple aliases by separating them with commas:-

  

[Name of tour file]: [Alias 1], [Alias 2]

  

E.g.

  

gen8randbatsmayhem: randbtasmayhem, randbtas