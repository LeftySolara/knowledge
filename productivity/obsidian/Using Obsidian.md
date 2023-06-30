---
aliases:
  - How to Use Obsidian
tags:
  - "#productivity/note-taking/obsidian"
  - "#tools/software"
---

# Using Obsidian

These are my notes on various ways to use Obsidian efficiently. They're a combination of ideas from personal experience as well as tips I've learned from others.

## Basics

### Vaults

Obsidian allows you to work directly with files on your device. When you open a folder in Obsidian, that folder becomes a **vault**. Basically, it's the root folder that you'll be working in. You can have as many vaults as you like, but only one can be open per window.

```ad-important
Each vault in Obsidian has its own separate set of settings and plugins. If you change any settings or install plugins, they will only apply to that vault.

To copy settings and plugins between vaults, simply copy around the `.obsidian` folder that exists inside the root directory of the vault.
```


## Metadata

Each note in Obsidian can have custom metadata attached to it. There are a few keys that are officially supported, but you can also create your own. The only difference between supported and non-supported keys is that the supported ones are shown under the "Metadata" section in reading mode.

To add metadata to a note, insert a YAML text block at the beginning of the file, wrapped in triple dashes.

## References

[Amy Li - Use YAML Front Matter Correctly in Obsidian](https://amyjuanli.medium.com/use-yaml-front-matter-correctly-in-obsidian-550e4fa46a4a)