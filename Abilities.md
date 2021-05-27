# Abilities

`ability_bag`

* `action_list`
    * `start_self_actions` `action_0X` references **_[action]_**
        * If action is`[[action\ability_action\apply_modifiers_action.lua]]`
            * `modifiers` `modifiers_0X` References **_[modifiers]_**
                * `value`
                * `target_type_name` like `[[hardpoint_01]]
                * `usage_type`
        * If action is`[[action\ability_action\requirement_action.lua]]`
            * `action_table` `ability_actions` `action_0X` References **_[action]_**
                * `modifiers` `modifiers_0X` References **_[modifiers]_**
                    * `value`\
                    If the modifier is `[[modifiers\enable_weapon_modifier.lua]]`, a value of -1 disables the weapon
                    * `target_type_name` like `[[hardpoint_01]]
                    * `usage_type`
                * `amount`
                * `target_info` References **_[type_ability_target_type]_**
        * Ignore `[[action\ability_action\animator_set_state.lua]]`
    
    * `end_self_actions` skipping for now, seems to mostly be cooldowns or removing (consuming) an upgrade

* `activation`\
Possible values are `[[targeted]]`, `[[timed]]`, `[[toggle]]`

* `duration_time`

* `recharge_time`

* `requirements` 
    * `required_X` References **_[requirements]_**, commonly `[[requirements\required_entity_upgrade.lua]]` or `[[requirements\required_player_upgrade.lua]]`
        * `upgrade_name`
        * `is_present` default True, is False if we want the requirement to be fulfilled when the upgrade is not present
    

