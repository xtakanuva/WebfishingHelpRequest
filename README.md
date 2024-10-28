# WebfishingHelpRequest

Issues dealt with right now.

# Description

Currently trying to update a vanilla shop with a new file of it. I already have the assets for the new items, I am having issues creating the new shop, placing said items inside, and showing said shop.

# New Files

Brew_vending_shop.tscn # To replace the current vending_shop.tscn
mod_button_item.gd # Replacement of original item
mod_shop.gd

# Walkthrough my thought process:

### In res://Scenes/HUD/Shop/, there are a few main folders and files

/ShopButtons/
- shop_button.gd
- shop_button.tscn
- shop_button_old.gd

/ShopSetups/
- bait_shop.tscn  // not what i'm looking for
- boat_shop.tscn  // not what i'm looking for
- general_shop.tscn  // not what i'm looking for
- progression_shop.tscn  // not what i'm looking for
- sell_shop.tscn  // not what i'm looking for
- shop_category.gd 
- shop_setup.gd
- spectral_shop.tscn  // not what i'm looking for
- test_shop.tscn  // not what i'm looking for
- vending_shop.tscn

shop.gd
shop.tscn

### Updating the vending_shop file
Since I've been wanting to update the vending_shop, I open it, which gives me the scene of buttons that the vending machine has.
![image](https://github.com/user-attachments/assets/45df53c0-abdf-47ee-98f4-a7c4c327678d)

I duplicate this file and place it in my mod folder, renaming it brew_vending_shop, adding four new buttons for the new items:
![image](https://github.com/user-attachments/assets/92393bde-1c39-4fa1-a2d0-3c21187a4b18)

While looking at the shop buttons (also duplicated), I feel as though the only variable that changes is the item_id in the script variables.
This causes me to scroll down to the node and look at the script attached to it, button_item (res://Scenes/HUD/Shop/ShopButtons/button_item.gd)

button_item extends the ShopButton (A folder?). 
![image](https://github.com/user-attachments/assets/83eed27d-ad0d-49c9-8108-a200f021213d)

### Creating a new button_item

I duplicated button_item and placed it into my mod folder, renaming it mod_button_item.
This was to add the custom items as the original file pulls item data from the game's global item data (Globals.item_data). Duplicating the button_item and changing it would allow me to extend the original button_item and add a mod directory myself (ItemData.gd:res://mods/BodyBrew/ItemData.gd), which enables the ability to retrieve the information for mod-specific items. 

I'm not trying to hard patch the main data, as I want it to be compatible with other things in the future, so hopefully doing this would allow that. Aka data independence, easier mod management.

mod_button_item.gd
![image](https://github.com/user-attachments/assets/7dd54058-dd0a-48bc-998c-03685ae8d960)

ItemData.gd
![image](https://github.com/user-attachments/assets/4b3da518-75a5-433a-9842-0c33e142b412)

While I looked at the shop buttons in brew_vending_shop earlier, in the Node property there was a .gd file in the Script category, so I changed it from the original button_item.gd > mod_button_item.gd.

I don't think there is any consequence to this as the new mod_button_item is an extension of the original button, so it should still be playing through the entire file.

### shop.gd

shop.gd (res://Scenes/HUD/Shop/shop.gd) plays a central role in the shop functionality, dealing with item display, interaction, shop layout, everything.

Something that caught my eye was the const SETUPS, preloading the original vending_shop.
![image](https://github.com/user-attachments/assets/301e6f30-fa83-4d36-95d9-ee9207f06b9d)

As this was not what I wanted, I created a new file, mod_shop.gd and extended the original file. This aimed to change the preloading entry to the new brew_vending_shop.tscn I created earlier.
![image](https://github.com/user-attachments/assets/e73193c1-3fa6-449d-a7ec-98c869d51c17)

This is a part that I felt as though I had a lot of struggle with. Because while it seemed like shop.gd had a lot of structure to uphold, using Ctrl + Shift + F revealed that it was only referenced through this new mod_shop.gd and nowhere else. Which probably means it's more than likely in the signals, right?

## So my next step that I'm asking for help on is how to update any existing paths with shop.gd with mod_shop.gd to make sure the new vending shop is being preloaded.

That is, if I'm even doing this correctly.



















# Outstanding issues

Can't find a way to replace the original vending_shop with brew_vending_shop to appear in game.
