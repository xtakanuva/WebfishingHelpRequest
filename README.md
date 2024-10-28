# WebfishingHelpRequest

Issues dealt with right now.

# Description

Currently trying to update a vanilla shop with a new file of it. I already have the assets for the new items, I am having issues creating the new shop, placing said items inside, and showing said shop.

# New Files

Brew_vending_shop.tscn # To replace the current vending_shop.tscn

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

### Since I've been wanting to update the vending_shop, I open it, which gives me the scene of buttons that the vending machine has.
![image](https://github.com/user-attachments/assets/45df53c0-abdf-47ee-98f4-a7c4c327678d)

### I duplicate this file and place it in my mod folder, renaming it brew_vending_shop, adding four new buttons for the new items:
![image](https://github.com/user-attachments/assets/92393bde-1c39-4fa1-a2d0-3c21187a4b18)

### While looking at the shop buttons (also duplicated), I feel as though the only variable that changes is the item_id in the script variables.
### This causes me to scroll down to the node and look at the script attached to it, button_item (res://Scenes/HUD/Shop/ShopButtons/button_item.gd)






















