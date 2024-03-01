The first line of code is what the files recognize to be XML, so this line is 100% necessary at all times at the start
of the code. Line 1 should always read:  
`<?xml version="1.0" encoding="utf-8" ?>`  
The following line should be the **<elements>** tag. This indicates to Aurora Builder that everything in this file is a
tree of elements that it should parse.

&nbsp;&nbsp;&nbsp;&nbsp; The following section is the `<info>` tag that allows the file to be updated online if it
detects a file version, which will be delved into later. This is only necessary if you intend
to [host your custom content online](<{{ GITHUB_REPO }}/wiki/Setting-Up#hosting>); if you intend to send the file to
people or keep the file on your PC, this tag is **unnecessary** and can be removed.  
&nbsp;&nbsp;&nbsp;&nbsp; The line after this is the first `<element>`, which is mainly the purpose of the file, such as
a class, subclass, race, and so on for what the file intends to add. We must look at each sub-element and its different
attributes and tags to understand the element.

## Attributes

Attributes are used as key-value pairs with the patterns key= “value” that defines certain things Aurora reads.

| Key    | Constraint                                                                                                   |
|:-------|:-------------------------------------------------------------------------------------------------------------|
| name   | Any String                                                                                                   |
| type   | Any valid type                                                                                               |
| source | The name of any source                                                                                       |
| id     | Any String that uniquely identifies this element. A pattern of **ID_AUTHOR_SOURCE_TYPE_NAME** is recommended |

For example:

```xml

<element name="Blade Of Disaster" type="Spell" source="Tasha’s Cauldron of Everything"
         id="ID_WOTC_TCOE_SPELL_BLADE_OF_DISASTER">
```

### Name

The name attribute contains a string, a series of letters that makes a word, that Aurora reads. This is viewed in
several ways, from the selection name of a feature on a sheet to a spell name.

### Type

The “type" is what defines the element. Each type has specific and required child elements to function correctly. “type”
is often used when granting other elements or giving the user a selection from a particular type of group. Check the
list of types [here](<{{ GITHUB_REPO }}/wiki/Types>).

### Source

The source is meant for the source of the material, which is just a string, as previously mentioned. Aurora Builder
takes the source's name and tries to match it with another pre-existing source that can later be filtered in the Sources
tab under Start. Source is essential when you want to group multiple elements under one source that the program can
later filter of the user’s choice. If you want to input extra information regarding the source, you may create
a [source.xml](<{{ GITHUB_REPO }}/wiki/Setting-Up#source-definition>) file that contains an element with the Source
type.

### ID

While a name and type are what aid Aurora in reading the element, it is the ID that makes it unique; start your ID with
**ID_** and only use letters, numbers and underscores (if you don’t put “ID” at the start, Aurora will not read it as an
ID). An element with an id that already exists will override the existing element completely. To avoid duplicate
elements, the best practice is to make your ID in the following format: `ID_{AUTHOR}_{SOURCE}_{TYPE}_{NAME}` Using
acronyms is the best way to avoid making long IDs.

1. IDs must start with ID_
2. ID format should be one line containing only A-Z, 0-9, and _
3. IDs need to be in all caps
    1. Note: the app will attempt to fix this, but it may cause other errors
4. For things to appear in the correct Additional section of equipment
    1. Feat IDs must include `_FEAT_`
    2. Language IDs must include `_LANGUAGE_`
    3. Proficiency IDs must include `_PROFICIENCY_`
    4. Spell IDs must include `_SPELL_`

## Child Tags

Many child elements, subelements, or tags belong to various element(s) that affect how the element is used and
presented.

| Child Tag                                                                    | Brief Description                                                                                                                                                                                       | Data Type |
|:-----------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------:|
| [compendium](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#compendium>)     | This hides the element from compendium search results.                                                                                                                                                  |  Boolean  |
| [supports](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#supports>)         | A collection that filters elements when creating a selection rule, such as archetypes, skill proficiencies, fighting styles, etc.                                                                       |  String   |
| [requirements](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#requirements>) | An element can have various requirements, such as a race or a minimum ability score, to allow the element to be selected from a list.                                                                   |  String   |
| [prerequisite](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#prerequisite>) | This is a small description that displays only during selects that details why the element is available.                                                                                                |  String   |
| [description](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#description>)   | The description appears in the panel on the right side of the builder. This is made using basic HTML/XML.                                                                                               |  String   |
| [sheet](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#sheet>)               | The plain text description will be displayed on the sheet instead of inside the builder. You can set attributes that hide the element in the character sheet or change the name displayed on the sheet. |  String   |
| [setters](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#setters>)           | A set of setters specific to certain elements, such as a school for spells or names (male/female) for a race.                                                                                           |  Various  |
| [spellcasting](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#spellcasting>) | A simple node to indicate that this element is a spellcasting class or archetype. This will create a base for the spellcasting class, including a tab and a spellcasting page.                          |  String   |
| [multiclass](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#multiclass>)     | A node on a class to indicate you can multiclass with the class.                                                                                                                                        |  String   |
| [rules](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#rules>)               | A collection of rules that this element has, such as statistic increases, granting additional elements, allowing a selection of a collection of elements and so on.                                     |  String   |

### Compendium

The compendium is commonly used to disallow content to be found in the compendium tab in Aurora Builder. In this example
we disallow the element called "Blade Of Disaster" from being found in the compendium.

```xml

<element name="Blade Of Disaster" type="Spell" source="Tasha’s Cauldron of Everything"
         id="ID_WOTC_TCOE_SPELL_BLADE_OF_DISASTER">
    <compendium display="false"/>
    ...
</element>
```

### Supports

A support is a way of grouping elements to be later used in Selects or the Compendium. For this example, this is the
Hill Dwarf from the race-dwarf.xml file.

```xml

<element name="Hill Dwarf" type="Sub Race" source="Player’s Handbook" id="ID_SUB_RACE_HILL_DWARF">
    <supports>Dwarf</supports>
    ...
</element>
```

Aurora would then read that this element is part of a group called “Dwarf” that can be retrieved by a select tag in the
“rules” tag. This allows Aurora to understand that there is a needed selection to present a list from the group called
“Dwarf.” An example of selecting a subrace specifically for dwarfs would be as follows:

```xml

<rules>
    <select type="Sub Race" name="Dwarven Subrace" supports="Dwarf"/>
</rules>
```

As long as you follow the same format, you should be able to select a specific element depending on the supports. The
name section can be named whatever. You can see more
in [select](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#select>) rules.

### Requirements

As mentioned, there are elements chosen from a list with restrictions. This can be used for various examples, such as
feats requiring spellcasting, feats requiring X minimum ability score, invocation-like class features requiring other
elements, etc.

1. Requirements Inputs
    1. Ability Score Stats
    2. Other element IDs
    3. Spellcasting IDs

### Prerequisite

An optional feature that shows up during instances of selects. This allows for text to display between the name of an
element and its source, for example, when selecting a feat:  
[[images/MODERATELY ARMORED.png]]

**NOTE: ELEMENTS WITH REQUIREMENTS AS PART OF A GROUP (SUPPORTS) WILL NOT BE SEEN UNTIL THE REQUIREMENT IS MET.** Using
the feat above, if the character has no proficiency with light armor, the feat would not be available to be selected.

### Description

The description tag outlines what must be displayed when selecting a feature. This is different from the sheet
description.

| Field                     | Notes                                                                             |
|:--------------------------|:----------------------------------------------------------------------------------|
| `<p>`                     | Regular sentence                                                                  |
| `<p class="indent">`      | Sentence with indent                                                              |
| `<h4>`/`<h5>` etc.        | Different size headers                                                            |
| `<ul>`                    | Start of a list                                                                   |
| `<li>`                    | Individual points on a list                                                       |
| `<div element=”ID”>`      | Displays blocks of elements (Class Features, Spells, etc.)                        |
| `<div class=”sidebar”>`   | Creates a square that text can be put under this tag with another description tag |
| `<div class=“reference”>` | Same as div element but under individual class/archetype features                 |

### Setters

The setters are where unique values depending on the element type can be set with a combination of a key and a value. A
race element, for example, might have names, while a spell element has material components. Depending on the type,
specific names populate these values in the builder.

The format for these setters is `<set name="{name}">{value}</set>`. Some setters with the same name have additional
attributes besides the name attribute to ensure the builder can use the difference. Think of a price setter with an
additional currency attribute to determine the type of coin used or a name setter with a gender attribute to generate a
random name based on the character's gender.

#### Required Setters (Race)

```xml

<setters>
    <set name="names" type="male">Adrik, Alberich, Baern, Barendd, Brottor</set>
    <set name="names" type="female">Amber, Artin, Audhild, Bardryn, Dagnal</set>
    <set name="names" type="clan">Balderk, Battlehammer, Brawnanvil, Dankil, Fireforge</set>
    <set name="names-format">{{name}} {{clan}}</set>
</setters>
```

#### Required Setters (Class)

```xml

<setters>
    <set name="hd">d8</set>
</setters>
```

Optionally, you can add `<set name="short">Short description here.</set>`. When selecting a class or archetype from many
others, this adds a small description to be viewed briefly describing the class.

#### Required Setters (Spell)

```xml

<setters>
    <set name="level">3</set>
    <set name="school">Evocation</set>
    <set name="time">1 action</set>
    <set name="duration">Instantaneous</set>
    <set name="range">150 feet</set>
    <set name="hasVerbalComponent">true</set>
    <set name="hasSomaticComponent">true</set>
    <set name="hasMaterialComponent">true</set>
    <set name="materialComponent">a tiny ball of bat guana and sulfur</set>
    <set name="isConcentration">false</set>
    <set name="isRitual">false</set>
</setters>
```

### Sheet

The sheet child tag allows Aurora to be unique by displaying what is required on the generated PDF. This is mainly used
to display Feats, class features, archetype features, and racial traits.

| Field   | Value     | Required | Notes                                                                                                                                                                                                     |
|:--------|:----------|:---------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| display | (boolean) | No       | This is mainly used to hide features that would not need to be displayed, such as gaining proficiencies.                                                                                                  |
| action  | (string)  | No       | This displays whether the feature can be used as an Action, Bonus Action, or Reaction. It can also be anything else, including stat values.                                                               |
| usage   | (string)  | No       | As above for usages.                                                                                                                                                                                      |
| alt     | (string)  | No       | Short for alternate; this displays an alternative name to be displayed on the sheet. For example, if the class feature is named “Test” and sheet alt is named “Exam,” then the sheet will display “Exam.” |

The description can be a child tag under the Sheet; however, this does not use HTML formatting and is just plain text.
You may insert a string without `<p>`, unlike the regular sheet tag. Additionally, stats can be used to display their
value if referenced by their stat name between {{**STAT**}}. For example, monk Ki DC is added separately and displayed
on the sheet as values.

```xml

<sheet>
    <description>You have {{ki:points}} Ki Points and your Ki DC is {{ki:dc}}</description>
</sheet>
```

This code becomes (for a level 3 monk): ***Ki.*** You have 3 Ki Points, and your Ki DC is 13.  
When used with a sheet, the display option creates the option to disable it to be displayed on the PDF. With the limited
space of the sheet, this is commonly used for features that don't add any particular actions or passives.

```xml

<sheet display="false">
    <description>You gain proficiency in Acrobatics.</description>
</sheet>
```

The level attribute can also change the description at certain levels. For example, tieflings and their cantrips:

```xml

<sheet>
    <description>You know the thaumaturgy cantrip. Charisma is your spellcasting ability for these spells.</description>
    <description level="3">You know the thaumaturgy cantrip. You can cast the hellish rebuke spell as a 2nd-level spell
        once per rest. Charisma is your spellcasting ability for these spells.
    </description>
    <description level="5">You know the thaumaturgy cantrip. You can cast the hellish rebuke spell as a 2nd-level spell,
        and the darkness spell once per rest. Charisma is your spellcasting ability for these spells.
    </description>
</sheet>
```

### Spellcasting

A simple node indicates that this element is a spellcasting class or archetype. This will create a base for the
spellcasting class, including a tab and a spellcasting page, the name coming from the `name` attribute and being
case-sensitive. Use the ability attribute to assign one of the `abilities` as the spellcasting ability. Include a `list`
with the class name that should function as the spell list.

```xml

<spellcasting name="Wizard" ability="Intelligence">
    <list>Wizard</list>
</spellcasting>
```

#### Extending Spellcasting

You can extend an existing spelllist of a class by including a spellcasting node in another element. Use the name of the
original spellcasting node and include the `extend` attribute with the value of `true`.

```xml

<spellcasting name="Wizard" extend="true">
    <extend>Cleric</extend>
</spellcasting>
```

This makes it so the Wizard class gets Cleric spells to select from. This can also be done with spell IDs.

### Multiclass

Instead of creating a complete element for the multiclass class, the builder clones the class element and modifies some
parts, starting with the `id`. Include the requirements to multiclass with or into this class.

The `ID_INTERNAL_GRANT_MULTICLASS` element that is granted here is a requirement.

```xml

<grant type="Grants" id="ID_INTERNAL_GRANT_MULTICLASS"/>
```

```xml

<multiclass id="ID_WOTC_PHB_MULTICLASS_PALADIN">
    <prerequisite>Strength 13 and Charisma 13</prerequisite>
    <requirements>([str:13],[cha:13])</requirements>
    <setters>
        <set name="multiclass proficiencies">Light armor, medium armor, shields, simple weapons, martial weapons</set>
    </setters>
    <rules>
        <grant type="Grants" id="ID_INTERNAL_GRANT_MULTICLASS"/>
        <grant type="Proficiency" name="ID_PROFICIENCY_ARMOR_PROFICIENCY_LIGHT_ARMOR"/>
        <grant type="Proficiency" name="ID_PROFICIENCY_ARMOR_PROFICIENCY_MEDIUM_ARMOR"/>
        <grant type="Proficiency" name="ID_PROFICIENCY_ARMOR_PROFICIENCY_SHIELDS"/>
        <grant type="Proficiency" name="ID_PROFICIENCY_WEAPON_PROFICIENCY_SIMPLE_WEAPONS"/>
        <grant type="Proficiency" name="ID_PROFICIENCY_WEAPON_PROFICIENCY_MARTIAL_WEAPONS"/>
    </rules>
</multiclass>
```

### Rules

A rule is a collection of grants, selects, and stats the Element provides. This example is from the class-monk.xml file.

```xml

<rules>
    <grant type="Proficiency" id="ID_PROFICIENCY_WEAPON_PROFICIENCY_SIMPLE_WEAPONS"
           requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <grant type="Proficiency" id="ID_PROFICIENCY_WEAPON_PROFICIENCY_SHORTSWORD"
           requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <select type="Proficiency" name="Tool Proficiency (Monk)" supports="Musical Instrument||Artisan tools"
            requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <grant type="Proficiency" id="ID_PROFICIENCY_SAVINGTHROW_STRENGTH" requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <grant type="Proficiency" id="ID_PROFICIENCY_SAVINGTHROW_DEXTERITY" requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <select type="Proficiency" name="Skill Proficiency (Monk)" supports="Skill,Monk" number="2"
            requirements="!ID_WOTC_PHB_MULTICLASS_MONK"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_UNARMORED_DEFENSE" level="1"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_MARTIAL_ARTS" level="1"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_KI" level="2"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_UNARMORED_MOVEMENT" level="2"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_MONASTIC_TRADITION" level="3"/>
    <grant type="Class Feature" id="ID_WOTC_PHB_CLASS_FEATURE_MONK_DEFLECT_MISSILES" level="3"/>
    ...
</rules>
```

Child tags specific to rules are grant, select, and stat.

#### Grant

A grant is used when only one option is given to the user automatically. This will not appear as a Select would on the
application. Most common examples are proficiencies, spells, and skills.

| Field        |   Value   | Required | Notes                                                                                                                                                             |
|:-------------|:---------:|:--------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| type         | (string)  |   Yes    | See [Types](<{{ GITHUB_REPO }}/wiki/Types>)                                                                                                                       |
| requirements | (string)  |    No    | See [Requirements](<{{ GITHUB_REPO }}/wiki/Anotomy-of-the-Element#requirements>)                                                                                  |
| id           | (string)  |   Yes    | Only used for IDs for the specific type                                                                                                                           |
| level        | (integer) |    No    | Only used if a feature is gained at a certain level. Assumes character total level. See [Level Notes](<{{ GITHUB_REPO }}/wiki/Anotomy-of-the-Element#level-note>) |

An example of a grant would be:

```xml

<grant type=“Spell” id=“ID_PHB_SPELL_FIREBALL” requirements=“ID_PHB_RACE_TIEFLING” />
```

[List of Proficiencies.](<{{ GITHUB_REPO }}/wiki/Proficiencies-IDs>)

#### Select

A select is used when there are multiple options that the user can choose from.

|    Field     |       Value       |      Require      | Notes                                                                                                                              |
|:------------:|:-----------------:|:-----------------:|:-----------------------------------------------------------------------------------------------------------------------------------|
|     type     |     (string)      |        Yes        | See [Types](<{{ GITHUB_REPO }}/wiki/Types>)                                                                                        |
|     name     |     (string)      |        Yes        | The name appearing on the selection field.                                                                                         |
|   supports   |     (string)      |        Yes        | See Support Logic                                                                                                                  |
|   optional   | "True" or "False" |        No         | See Requirement Logic                                                                                                              |
| requirements |     (string)      |        No         | See Requirement Logic                                                                                                              |
|    number    | (int) as (string) | No (assumes as 1) | Number of selects to be provided to the user with the same options                                                                 |
|   default    |     (string)      |        No         | The value that will be automatically selected. Please be cautious as these commonly revert changed values to the default.          |
|    level     |     (integer)     |        No         | Only used if a feature is gained at a certain level. See [Level Notes](<{{ GITHUB_REPO }}/wiki/Anotomy-of-the-Element#level-note>) |

#### Stat

Stats play an essential piece in files. It allows the most manipulation of values that can be altered and/or created.

|    Field     |   Value   | Require | Notes                                                                                                                                                                                                  |
|:------------:|:---------:|:-------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     name     | (string)  |   Yes   | The name will be a container for the value.                                                                                                                                                            |
|    value     |  integer  |   Yes   | An integer value is given to the stat's name.                                                                                                                                                          |
|    bonus     | (string)  |   No    | See [Bonus Note](<{{ GITHUB_REPO }}/wiki/Anotomy-of-the-Element#bonus-note>).                                                                                                                          |
|    inline    | (boolean) |   No    | Allows Value to become a string if "true."                                                                                                                                                             |
|    level     | (string)  |   No    | Only used if a stat is affected or gained at a certain level. Assumes character total level.                                                                                                           |
|   equipped   | (string)  |   No    | Like requirements, the value displays if a particular thing is equipped; see Unarmored Defense (Monk & Barbarian.) Also, see [Level Note](<{{ GITHUB_REPO }}/wiki/Anotomy-of-the-Element#level-note>). |
| requirements | (string)  |   No    | This makes the stat available if the requirements are met.                                                                                                                                             |

Since the name is the container of the value, the name can be referenced in other stats, such as value or the sheet
description. An example from Hill Dwarf’s Dwarven Toughness:

```xml

<stat name="hp" value="level"/>
```

The stat name, hp, is used to give hit points by each level the class has (3 hit points if the class is a level 3
fighter, barbarian, etc.) This is the total level regardless of multiclass. Codes added this way are automatically added
to a character’s data, such as a race gaining a +2 to an ability score.  
The values of stats can be added by repeating the code multiple times. For example, if you want to use the code above to
gain hp for three times the level, the stat must be repeated twice. You can add a negative number to subtract from the
total.

```xml

<stat name="hp" value="level"/>
<stat name="hp" value="level"/>
<stat name="hp" value="level"/>
```

Also, values displayed can be cut in half, nothing lower, with `:half` that automatically rounds down as per 5e rules.

When `inline="True"`, a stat can have the value as a string. Please take a look at the Dragonborn code for a good
example.

```xml

<sheet alt="Black">
    <description>Your draconic ancestry is {{draconic-ancestry}}. Your damage type is {{draconic-ancestry:damage type}}.
        Your breath weapon is {{draconic-ancestry:breath}}.
    </description>
</sheet>
<rules>
<stat inline="true" name="draconic-ancestry" value="Black"/>
...
</rules>
```

[List of stats.]()

##### Bonus Note

Bonus is used when you have multiple sources for a stat, but you only take the highest number. There are a few
standardized values for `bonus=""` that are used throughout the repo (shown below), but you can use your own.

- `bonus="base"` - This is used when something has text like “gains a bonus to damage equal to the Charisma modifier (
  minimum of +1)”. In this example, if the `charisma:modifier` stat is less than 1, then the bonus="base" will take the
  higher value of the flat 1

```xml

<stat name="aura of hate:damage" value="1" bonus="base"/>
<stat name="aura of hate:damage" value="charisma:modifier" bonus="base"/>
```

- `bonus="ability"` - This is used when something takes the higher of 2+ ability modifiers like in “Maneuver save DC =
  8 + your proficiency bonus + your Strength or Dexterity modifier”. In this example, `bonus="ability"` will take the
  higher of the strength or dexterity modifier.

```xml

<stat name="superiority dice:dc:ability" value="strength:modifier" bonus="ability"/>
<stat name="superiority dice:dc:ability" value="dexterity:modifier" bonus="ability"/>
```

- Bonuses are used when stats can’t stack with each other; for example, let's say you get an Armor that gives you a +3
  morale bonus to your AC. If you have, let's say, Gloves that give you a +2 morale bonus to your AC, those two don't
  stack. Instead, you choose the higher one to apply to your AC. So, following that logic, if you would want to recreate
  that in Aurora, those stats would look something like this:

```xml

<stat name="ac:misc" value="3" bonus="morale"/>
<stat name="ac:misc" value="2" bonus="morale"/>
```

- The app would see that different stats have the same name and bonus and select whichever has the highest value to
  apply to the calculation. This is helpful in 5e primarily for abilities that say, "You can use this feature number of
  times equal to your [ability] modifier (minimum of 1)", so the app could select whichever is higher between the two.

##### Inline Note

The inline values are strings, appearing as characters when referenced.

```xml

<rules>
    <stat inline="true" name="bite damage" value="1d6" bonus="base"/>
</rules>
```

When using `{{bite damage}}` in the sheet, it will appear 1d6. This does not stack with any other values. Using another
inline for a stat overrides prior value regardless of bonus, requirements, or levels, so grant it under certain
conditions.

##### Level Note

The level is used with grants, selects, and stats at certain levels. The level is defaulted to total character levels.
They can be used in requirement logic, stat values, and sheet descriptions (see Sheet.)  
Examples:

```xml

<requirements>[level:2]</requirements>
```

For requirements of specific elements.
See [requirements](<{{ GITHUB_REPO }}/wiki/Anatomy-of-the-Element#requirements>).

```xml

<stat name="hp" value="level"/>
```

For stats that are gained at specific levels. This also goes for class and archetype features gained at levels.
