...

## Hosting

...

### Providers

...

### File Tree Structure

...

## Source Definition

...

## Visual Studio Cod

...

### Aurora Snippets

The following section will present each type with a template. These templates are obtained from a Visual Studio Code snippet for [Aurora Legacy](https://marketplace.visualstudio.com/items?itemName=AuroraLegacy.auroralegacy-snippets).

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
				<li><strong>Hit Dice:</strong> 1d8 per lowercaseclassname level</li>
				<li><strong>Hit Points at 1st Level:</strong> 8 + your Constitution modifier</li>
				<li><strong>Hit Points at Higher Levels:</strong> 1d8 (or 5) + your Constitution modifier per lowercaseclassname level after 1st</li>
			</ul>
			<h5 class="caption">PROFICIENCIES</h5>
			<ul class="unstyled mb">
				<li><strong>Armor:</strong> </li>
				<li><strong>Weapons:</strong> </li>
				<li><strong>Tools:</strong> </li>
			</ul>
			<ul class="unstyled">
				<li><strong>Saving Throws:</strong> </li>
				<li><strong>Skills:</strong> </li>
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
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
			<div element="ID____" />
		</description>
		<setters>
			<set name="hd">d4</set>
		</setters>
		<sheet display="false" />
		<rules>
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
			<grant type="Class Feature" id="ID____" level="level" />
		</rules>
	</element>
```

</details>

#### Race

...
