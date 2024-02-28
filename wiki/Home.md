## Welcome to the Aurora Legacy XML Documentation Wiki!
This is the start of the documentation to document the code used for Aurora, XML. This uses the reference material based on the original developer’s [documentation](https://aurorabuilder.com/documentation/) in a more in-depth way. You can use any text editor when making an XML file for Aurora Builder. However, the recommended editor is [Visual Studio Code](https://code.visualstudio.com/), which most of the community uses and is familiar with. Additionally, VSCode has an [Aurora Legacy Snippets](https://marketplace.visualstudio.com/items?itemName=AuroraLegacy.auroralegacy-snippets) extension that can be useful in creating XML files by providing quick templates and grants to proficiencies.

### Fundamentals of an XML file
All files are encompassed by an `<elements>` tag. This is the parent of the code that follows. Without this, Aurora skips over reading the contents of the file.
The building blocks with Aurora XML are these elements, which are the parent part of a “tree.” Everything underneath is sub-elements, or child elements, that Aurora sees as part of the code. The order of the code is usually scripted as follows:
* Elements
    * Info element that is mainly used for online updating
    * Element that is the main subject of the file, ie. Class, Race
    * Elements underneath, such as class features, racial traits
    * Spell Appends if the class has a spell list.
    * Other miscellaneous code, such as backend building blocks for more complicated implementation.

#### Standard Format

For every "[type](https://github.com/MeriadarGoblin/legacy-repository/wiki/Types)," the standard code should follow this format:
```xml
<element name="(name of element)" type="(specific type)" source="(specific source, ie. Homebrew)" id="(unique ID(see Anatomy of the Element))">
    ...
</element>
```
