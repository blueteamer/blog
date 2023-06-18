---
title: "Improve VSCode as Editor for Hugo Blog"
date: 2023-05-10T22:16:19+02:00
draft: true
---


{{ raw }}
```json
{
	// Place your snippets for markdown here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	// "Print to console": {
	// 	"prefix": "log",
	// 	"body": [
	// 		"console.log('$1');",
	// 		"$2"
	// 	],
	// 	"description": "Log output to console"
	// }
	"More section": {
		"prefix": ".more",
		"body": [
			"<!--more-->",
			"$1"
		],
		"description": "Adds the 'more' delimiter to your Hugo post."
	},
	"Mermaid section": {
		"prefix": ".mermaid", 
		"body": [
			"{{< mermaid >}}",
			"$1",
			"{{< /mermaid >}}"
		],
		"description": "Adds a block for Mermaid Chart Syntax to your Hugo post."
	},
	"Code block section": {
		"prefix": ".code", 
		"body": [
			"```$1",
			"$2",
			"```"
		],
		"description": "Adds a code block to your Hugo post."
	}, 
	"Add image": {
		"prefix": ".image",
		"body": "![$1]($2)",
		"description": "Adds an image. First note the alternative text, second the path to the image (imagename, only, if the image is in the same folder)"
	}, 
	"Alert section": {
		"prefix": ".alert",
		"body": [
			"{{< alert >}}",
			"$1",
			"{{< /alert >}}",
			"$2"
		],
		"description": "Adds a special alert section in your Hugo post."
	},
	"Badge": {
		"prefix": ".badge",
		"body": [
			"{{ badge }}",
			"$1",
			"{{ /badge }}",
			"$2"
		],
		"description": "Adds a badge button to your Hugo post."
	}
}

```
{{ /raw }}
