# Upgrade

Base `upgrade_bag`

Types of upgrades:
    
* ### Unit upgrades
    Mapping in `omg_ability_upgrade_const.scar`

    `actions` `action_0X` References **_[action]_**
    * If requirement action `[[action\ability_action\requirement_action.lua]]`
        * `action_table` `upgrade_actions` `action_0X` References **_[action]_** most likely `[[action\upgrade_action\slot_item_add.lua]]`
            * `slot_item` References **_[slot_item]_**
        * `requirement_table` `required_X` References **_[requirements]_** most likely `[[requirements\required_player_upgrade.lua]]`
            * `upgrade_name` References **_[upgrade]_** like a docmarker
            * `is_present` (optional) default True, if False prevents the associated action if this requirement is met
    * If change target type `[[action\upgrade_action\change_weapon_target_type.lua]]`
        * `new_type` References **_[type_target_weapon]_**
        * `original_type` References **_[type_target_weapon]_**
    * If add slot item without requirement `[[action\upgrade_action\slot_item_add.lua]]`
        * `slot_item` References **_[slot_item]_**
        
        
* ### Docmarkers
    Mapping in `omg_doc_const.scar`
    
    Properties aren't important, just use as a type.

