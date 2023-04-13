# Editor Syntax Highlight Obsidian Plugin

A plugin for [Obsidian](https://obsidian.md/) which allows syntax highlighting for code blocks in the editor.

![Screenshot](https://github.com/deathau/cm-editor-syntax-highlight-obsidian/raw/main/screenshot.png)

Imports code from [CodeMirror](https://github.com/codemirror/CodeMirror/)

### Compatibility

Custom plugins are only available for Obsidian v0.9.7+.

The current API of this repo targets Obsidian **v0.9.7**.

### Notes

This is all very expermental at the moment, so parts might not work, etc.

This imports a bunch of [syntax highlighting modes from CodeMirror](https://github.com/codemirror/CodeMirror/tree/5.58.2/mode), as well as the [yonce](https://github.com/codemirror/CodeMirror/blob/5.58.2/theme/yonce.css) theme for dark mode.

```js
test 
function  findnew 
```

```css
header 
```


```xml 
<this is the new world>
```

```verilog 
wire hey  
reg  hello 

```

Usage