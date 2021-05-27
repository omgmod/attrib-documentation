# Sbps

Types of squads we care about

* ### Infantry

    `squad_ability_ext` `abilities` `ability_0X` References **_[abilities]_**

    `squad_action_apply_ext` `actions` `ability_actions` `action_0X` References **_[action]_** most likely:
    
    * Apply modifiers `[[action\ability_action\apply_modifiers_action.lua]]`
        * `modifiers` `modifier_01` References **_[modifiers]_**
            * `value`
            * `application_type` (optional)
            * `usage_type` (optional)
        
    * Action with requirements `[[action\ability_action\requirement_action.lua]]`
        * `action_table` 
            * `ability_actions` `action_01` References **_[action]_** most likely `[[action\ability_action\apply_modifiers_action.lua]]`
            * `upgrade_actions` `action_01` References **_[action]_** most likely `[[action\ability_action\apply_modifiers_action.lua]]`
                * `modifiers` `modifier_01` References **_[modifiers]_**
                    * `application_type`
                    * `usage_type`
                    * `value`
        * `requirement_table` `required_1` References **_[requirements]_**
            * `operation` if requirement is a logical operator like `[[requirements\required_unary_expr.lua]]`, this could be `[[not]]`
            * `requirement_table` `required_1` References **_[requirements]_**
                * `min_owned`
                * `max_owned`
                * `slot_item` References **_[slot_item]_**
            
    `squad_combat_behaviour_ext` 
    * `suppression`
        * `cover_info` `tp_heavy` `recover_multiplier` Same for other cover types
        * `noncombat_delay`
        * `noncombat_recover_multiplier`
        
        * `recover_rate`
        * `suppressed_activate_threshold`
        * `pin_down_activate_threshold`
        * `suppressed_recover_threshold`
    
        * `pin_down_activate_actions` Skip this for now
    
    `squad_loadout_ext` `unit_list` `unit_0X`
    * `type` `type` References **_[ebps]_**
    * `num`
    
    `squad_veterancy_ext` `veterancy_rank_info`
    * `veterancy_rank_01`
        * `experience_value`
        * `squad_actions` `actions_0X` References **_[action]_** most likely `[[action\upgrade_action\apply_modifiers_action.lua]]`
            * `modifiers` `modifier_01` References **_[modifiers]_**
                * `value`
    * `veterancy_rank_02`
    * `veterancy_rank_03`
    * `veterancy_rank_04`
    * `veterancy_rank_05`

* ### Vehicles

    `squad_ability_ext` `abilities` `ability_0X` References **_[abilities]_**

    `squad_action_apply_ext` `actions` `ability_actions` `action_0X` References **_[action]_** most likely:
    
    * Apply modifiers `[[action\ability_action\apply_modifiers_action.lua]]`
        * `modifiers` `modifier_01` References **_[modifiers]_**
            * `value`
            * `application_type` (optional)
            * `usage_type` (optional)
        
    * Action with requirements `[[action\ability_action\requirement_action.lua]]`
        * `action_table` 
            * `ability_actions` `action_01` References **_[action]_** most likely `[[action\ability_action\apply_modifiers_action.lua]]`
            * `upgrade_actions` `action_01` References **_[action]_** most likely `[[action\ability_action\apply_modifiers_action.lua]]`
                * `modifiers` `modifier_01` References **_[modifiers]_**
                    * `application_type`
                    * `usage_type`
                    * `value`
        * `requirement_table` `required_1` References **_[requirements]_**
            * `operation` if requirement is a logical operator like `[[requirements\required_unary_expr.lua]]`, this could be `[[not]]`
            * `requirement_table` `required_1` References **_[requirements]_**
                * `min_owned`
                * `max_owned`
                * `slot_item` References **_[slot_item]_**
                
    `squad_loadout_ext` `unit_list` `unit_01`
    * `type` `type` References **_[ebps]_**
    
    `squad_veterancy_ext` `veterancy_rank_info`
    * `veterancy_rank_01`
        * `experience_value`
        * `squad_actions` `actions_0X` References **_[action]_** most likely `[[action\upgrade_action\apply_modifiers_action.lua]]`
            * `modifiers` `modifier_01` References **_[modifiers]_**
                * `value`
                * `application_type` (optional)
                * `usage_type` (optional)
    * `veterancy_rank_02`
    * `veterancy_rank_03`
    * `veterancy_rank_04`
    * `veterancy_rank_05`
