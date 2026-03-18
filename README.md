# GrandiEdit - A save game editor for Grandia on the Playstation 1
GrandiEdit is a utility to view and modify values within a memory card image containing save
data for Grandia on the PS1/PSX. 

## Currently in progress
The project is a work in progress, with an intent to pivot to a different language (Golang). Python
made the prototype and foundational logic quick and easy, but the tool requires some extra care.

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
- Rebuild in Go
- Frontend, the tool needs a UI form to both display and submit changes

### Nice to haves:
- API for potential web app use
- Command line interface
