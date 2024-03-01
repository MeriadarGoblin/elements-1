The explanations of hosting custom content online, setting up a development environment and all the [type](<{{
GITHUB_REPO }}/wiki/Types>) templates.

## Hosting

To host your custom content online you need to

### Providers

There are a lot of providers to choose from when it comes to hosting files online, such as:

- [GitHub](<https://github.com/>) (recommended)
- [GitLab](<https://about.gitlab.com/>)
- [Vercel](<https://vercel.com/>) (static site)
- And many more...

We generally recommended that you use GitHub as your hosting provider as it is straightforward and easy to do.
From now on, the Wiki assumes you have a GitHub account and repository setup and ready to be worked with, if you have
any trouble with using GitHub, please read the
following [Quickstart by GitHub](<https://docs.github.com/en/get-started/start-your-journey/hello-world>).

### File Tree Structure

The custom content you are going to host must have an `.index` file and a folder with the same file name (NOTE: don't
copy `.index` to the folder name!) and place the `.xml` files in there.
The file tree structure should look something like this:

```
{YOUR_PROJECT_NAME}/
├─ content.xml
├─ source.xml
{YOUR_PROJECT_NAME}.index
```

While this is a very simplified structure, it is still fundamental to have a structure based on the above one.

<i>NOTE: when using GitHub to host your custom content, make sure to share the link to the `.index` file
as `https://raw.githubusercontent.com/{GITHUB_USERNAME}/{GITHUB_REPO}/{BRANCH}/{YOUR_PROJECT_NAME}.index` and
not `https://github.com/{GITHUB_USERNAME}/{GITHUB_REPO}/blob/{BRANCH}/{YOUR_PROJECT_NAME}.index`!<i>

#### Index Files

...

## Source Definition

...

## Visual Studio Code

...

### Aurora Snippets

The following section will present each type with a template. These templates are obtained from a Visual Studio Code
snippet for [Aurora Legacy](<https://marketplace.visualstudio.com/items?itemName=AuroraLegacy.auroralegacy-snippets>).

#### Class

The class type for classes like Barbarians, Clerics, and so on.
<details>

<summary>Template</summary>

```xml
<element name="name" type="Class" source="source" id="ID_author_source_CLASS_name">
    <description>
        <p></p>
        <h4>_______________</h4>
        <p></p>
        <p class="indent"></p>
        <h4>_______________</h4>
        <p></p>
        <p class="indent"></p>
        <h4>CREATING A lowercaseclassname</h4>
        <p></p>
        <h5 class="caption">QUICK BUILD</h5>
        <p></p>
        <h2>CLASS FEATURES</h2>
        <p>As an lowercaseclassname, you gain the following class features.</p>
        <h5 class="caption">HIT POINTS</h5>
        <ul class="unstyled">
            <li>
                <strong>Hit Dice:</strong>
                1d8 per lowercaseclassname level
            </li>
            <li>
                <strong>Hit Points at 1st Level:</strong>
                8 + your Constitution modifier
            </li>
            <li>
                <strong>Hit Points at Higher Levels:</strong>
                1d8 (or 5) + your Constitution modifier per lowercaseclassname level after 1st
            </li>
        </ul>
        <h5 class="caption">PROFICIENCIES</h5>
        <ul class="unstyled mb">
            <li>
                <strong>Armor:</strong>
            </li>
            <li>
                <strong>Weapons:</strong>
            </li>
            <li>
                <strong>Tools:</strong>
            </li>
        </ul>
        <ul class="unstyled">
            <li>
                <strong>Saving Throws:</strong>
            </li>
            <li>
                <strong>Skills:</strong>
            </li>
        </ul>
        <h5 class="caption">EQUIPMENT</h5>
        <p>You start with the following equipment, in addition to the equipment granted by your background:</p>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
        <!-- class table here -->
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
        <div element="ID____"/>
    </description>
    <setters>
        <set name="hd">d4</set>
    </setters>
    <sheet display="false"/>
    <rules>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
        <grant type="Class Feature" id="ID____" level="level"/>
    </rules>
</element>
```

</details>

#### Race

...
