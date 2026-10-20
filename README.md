# GrandiEdit - A save game editor for Grandia on the Playstation 1

## Currently Abandoned
This repo stays for posterity, but is ultimately abandoned. As of 20/10/26, this project has been back on my radar with an intent to rewrite it in Haskell as a native application. I have learned a lot since starting this, and my affections lie elsewhere.

## Fully mapped memory locations
Every bit in the save file is appropriately mapped after being reverse-engineered with [ImHex](https://github.com/WerWolv/ImHex)
and is calculated instead as an offset from the start of the save file.

As there are up to 5 save files in one memory card image, each save's starting bit is mapped
into an appropriate struct, with each mapping being relative to bit 00. This ensures all
mappings remain applicable regardless of the save file being modified.

Additionally, two pairs of getter/setter functions are available to access or modify these values;
 - get_savefile_value()
 - set_savefile_value()
 - get_character_value()
 - set_character_value()

These functions take specific parameters to guide their usage. When a save file structure calls them,
they can access their internal data in a human-readable way, using constants (as defined in data_mappings.py)
to handle the hard work of calculating memory offsets.

## To Do:
- Rewrite in Haskell
- GUI
- Handle different memory card formats (currently only handles retroarch .srm files)
