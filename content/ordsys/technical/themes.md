+++
title = "Creating and editing themes"
menutitle = "Themes"
date =  2021-06-08T11:44:12+02:00
weight = 10
+++

Themes are used to give the system a more personal flair depending on who uses it. Groups like Klubbverket and Forsränningen have different themes, which changes whenever a user logs in. There are three key file locations for themes:
1. `./frontend/src/utils/themes.json`, where the theme names and color codes are defined.
2. The *ThemesEnum* enumerator class located under the Organisation model in `./backend/models.py`, which allows organisations to select the theme. Changing this requires making a database migration.
3. `./frontend/public/assets/images/`, where the theme logotypes are located. These must be named the same as the theme variable name and be in png format.

In short, the theme dictates which logotype is displayed in the top-left corner of all views, the header and button background color as well as text colors. These different colours are defined in `./frontend/src/utils/themes.json`, where a theme looks as follows:

```json
"utn": { // Theme variable name
        "buttonColor": "#004c98", // Colour of regular buttons
        "buttonActiveColor": "#207c98", // Colour of buttons when pressed
        "buttonHoverColor": "#023b75", // Colour of buttons when hovered over
        "darkTextColor": "#000000", // Colour of text that is rendered on bright backgrounds
        "lightTextColor": "#ffffff" // Colour of text that is rendered on dark background
    }
```
The *utn* theme has the logotype `./frontend/public/assets/images/utn.png`.

---

### Adding a new theme

{{% notice info %}}

Adding a new theme is fairly straight forward, but requires both a database migration and a commit to be merged into the master branch of the GitHub repo. This means creating a new theme requires administrator access to the system (or at least communication with the digitalization committee).

{{% /notice %}}

##### 1. Add colours to themes.json
First, add a new theme object to the themes.json file and assign it the colours you want. The name you give it here is its variable name.

##### 2. Add a logotype
In the static images folder mentioned above, save a png file with the logotype you want to use. There are no strict size requirements as the logotype will be resized to a correct height. Make sure the name of the logotype matches the name of the theme - meaning if you're making a theme called "bas", then your logotype should be named "bas.png".

##### 3. Add an enumerator choice
To enable organisations to select this theme in the Django admin interface, it must be added to the ThemesEnum enumerator class in the models.py field. Simply add a new line with the theme's variable name followed by the verbose name (what you'll see in the admin interface).

{{% expand "ThemesEnum as of July 2021"%}}
```python
class ThemesEnum(models.TextChoices):
        UTN = 'utn', 'UTN'
        UTNARM = 'utnarm', 'Utnarm'
        TEKNOLOG_DATAVETARMOTTAGNINGEN = \
            'td', 'Teknolog- och datavetarmottagningen'
        KLUBBVERKET = 'klubbverket', 'Klubbverket'
        FORSRANNINGEN = 'forsranningen', 'Forsränningen'
        REBUSRALLYT = 'rebusrallyt', 'Rebusrallyt'
```
{{% /expand %}}

##### 4. Put to production
Once the theme has been added, committed, pushed and merged through the UTNkar/OrdSys-repo, make the new migrations to the database following the repo readme instructions and you should be done.