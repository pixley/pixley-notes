[Scribe](https://scribe.pf2.tools), while immensely useful, has the limitation of being a webtool, and a free one at that.  Its recent instability (as of 29 Nov 2023) has prompted me to desire a locally-run replacement.  Since Obsidian already parses and renders Markdown, it seemed like a natural platform on which to pursue the idea.

There does already exist an Obsidian plugin, Fantasy Statblocks, that allows a user to create Pathfinder 2e statblocks.  However, its YAML-based syntax and rigid parsing (including just breaking an entire statblock when an error is encountered with no feedback readily available) make it unwieldy, and its aesthetic does not conform to standards.

Additionally, there is an Obsidian theme called ITS, and it has a PF2e subtheme.  However, it is merely a cosmetic change, and it is not flexible enough to create statblocks within, only standard types of text already supported by Markdown.  As far is the maintainer is concerned, the existence of Fantasy Statblocks is sufficient.

So how do we build this?  Obsidian has a plugin API.  It's TypeScript, though.  Yay.

Obsidian has documentation for its API, and a convenient thing it has built-in is [Markdown post-processing](https://docs.obsidian.md/Plugins/Editor/Markdown+post+processing).  This allows a plugin to manipulate the HTML elements that result from Obsidian parsing the input Markdown.  It seems like the convention for replacement is to wrap the content to replace inside a code block.

Issue with code block replacement convention: the interior of a code block is not itself parsed, which means that I would have to do the parsing myself.  This can be accomplished via static method `MarkdownRenderer.Render()`.  Might need to guard against infinite recursion if that calls post-processors.

HTML elements can also have custom CSS applied on creation, so this would allow for proper styling without affecting the document as a whole.

### Fonts
- Major Titles: [Taroka](https://fontsgeek.com/fonts/Taroca-Regular)
- Minor Titles: [Gin (Adobe)](https://fonts.adobe.com/fonts/gin)
- Stat Block Titles: [FF-Good (Adobe)](https://fonts.adobe.com/fonts/ff-good)
- Stat Block Text: [Roboto (Google)](https://fonts.google.com/specimen/Roboto)
- Body Text and Header Flavor: [Sabon (Abobe)](https://fonts.adobe.com/fonts/sabon)

Given that many of these fonts are proprietary, it's not worth the trouble.