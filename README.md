# TrackMania DS Documentation
(if you want me to add anything to the documentation, please message me on Discord or Telegram)

# Rom Information
   - Most content of the rom is contained in a zip (named "vfs.zip") (the application likely contains an anti-tampering since you cannot load the game with the content of the zip being edited)

# Content Information (present in "vfs.zip")
   - Script are in compiled LUA, you can check the <a href="https://github.com/miso-xyz/TrackManiaDS-Reversed">TrackManiaDS-Reversed</a> github repository where the decompiled scripts are available
   - The rest of the content are basic Nitro file

# Global Information about save files
   - File is split into sections, indicated by "D:" which are present every 0x100 (up to the custom maps)

# Replay Data
Byte Range | Information | Data Type
------------- | ------------- | -------------
0x00 - 0x04 | Header (always is "04 00 00 00") | UInt32
0x04 - 0x08 | Unknown | UInt32
0x08 - 0x10 | Unknown | UInt16
0x10 - 0x14 | Always ends in "00 00" | UInt32
0x14 - 0x18 | Always is "01 00 00 00" | UInt32
0x18 - 0x22 | Unknown | UInt32

# Custom Map Data
   - Maps (InGame) are 20x20x20 blocks, they're 506 bytes in the save file (Custom maps starts at 0xD00)

(for the following example, the starting offset is 0xD00)

Byte Range | Information | Data Type
------------- | ------------- | -------------
0xD02 - 0xD18 | Map Name | Unicode, but it has other characters in between, i do not know what they're used for
0xD1B - 0xD1F | Time Stamp | UInt32 (Seconds from January 1st 1935)
0xD21 - 0xD30 | Seperator | Seperate Map Metadata to Map Data
0xD31 - 0xD33 | "üÿÿ" | Unknown use, always present
0xD33 - (Map Size - 4) | Map Data
Last 4 bytes | Signature/Checksum | Algorithm Used is unknown

Map Data

Byte Range | Information | Data Type
------------- | ------------- | -------------
0x00 | Block Type | UInt8
0x01 | Rotation (Unsure) | UInt8, (00 = ↑, 06 = →, 02 = ←, 04 = ↑)
0x02 | X Position (Unsure) | UInt8 (Increases/Decreases by 2 depending on position)
0x03 | Y Position (Unsure) | UInt8 (Increases/Decreases by 2 depending on height)
0x04 | Z Position (Unsure) | UInt8 (Increases/Decreases by 2 depending on position)
