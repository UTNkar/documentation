---
title: "Themes"
weight: 10
---

Themes allow you to customize the appearance of the system to reflect the identity of different groups, such as Klubbverket and Forsränningen. When a user logs in, the theme changes to match their group. Here's where you can find and adjust theme settings:

1. **Theme Names and Colors:** Edit the file `./frontend/src/utils/themes.json` to define new theme names and their associated color codes. Use hexadecimal color codes (e.g., `#FF5733`).
2. **Theme Selection:** Use the *ThemesEnum* class in the Organisation model at `./backend/models.py` for selecting themes. If you modify this, remember you'll need to update the database with a migration.
3. **Logos:** Place theme logos in `./frontend/public/assets/images/`. Make sure each logo matches the theme's `logo` value that it is in .png format.

In essence, the theme controls the logo displayed on the top-left of all pages, as well as the colors of headers, buttons, and text. A typical theme entry in `./frontend/src/utils/themes.json` looks like this:

```json
"utn": { // Theme variable name
        "buttonColor": "#004c98", // Colour of regular buttons
        "buttonActiveColor": "#207c98", // Colour of buttons when pressed
        "buttonHoverColor": "#023b75", // Colour of buttons when hovered over
        "darkTextColor": "#000000", // Colour of text that is rendered on bright backgrounds
        "lightTextColor": "#ffffff" // Colour of text that is rendered on dark background
    }
```

The UTN theme uses the logo located at `./frontend/public/assets/images/utn.png`.

### Adding a New Theme

To add a new theme, you need to perform a database migration and merge a commit into the master branch of the GitHub repository. Administrator access to the system or communication with the digitalization committee is required.

#### 1. Add Colors to `themes.json`

Insert a new theme object into the `themes.json` file. Assign the desired colours to this theme. The name you choose will be its variable name.

#### 2. Add a Logotype

Place a PNG file with the desired logotype in the static images folder. The logotype will be resized to fit, so strict size requirements do not apply. The logotype's file name should match the theme's name. For example, if the theme is "bas", the logotype file should be named "bas.png".

#### 3. Add an Enumerator Choice

To make the new theme selectable in the Django admin interface, add it to the ThemesEnum class within the models.py file. Include a new line with the theme's variable name and its verbose name, which will be displayed in the admin interface.

{{% details "ThemesEnum as of July 2021"%}}

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

{{% /details %}}

#### 4. Deploy to Production

After the theme is added to the repository, and the changes are committed, pushed, and merged into the UTNkar/OrdSys repository, execute the database migrations as described in the repository's README file to complete the process.
