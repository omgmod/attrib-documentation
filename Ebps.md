# Ebps

Should expose `type_target_weapon` at top level for ease of querying.

Types of entities we care about:

### Infantry

`ability_ext` `abilities` `ability_01` References **_[abilities]_** 

`camouflage_ext`
* `attack_priority`
* `detection_radius`
* `first_strike_actions` `ability_actions` `action_01`
    * `duration`
    * `modifiers`
        * `modifier_01`
            * `reference` References **_[modifiers]_**
            * `value`
        * `modifier_02`
* `reveal_number_shots`

`combat_ext` `hardpoints` `hardpoint_01` `weapon_table` `weapon_01` `weapon` References **_[weapon]_**\
 infantry should have 1 hardpoint 

`cover_ext`
Speed multipliers for different cover types

`health_ext`
* `hitpoints`
* `regeneration_disabled`
Can the entity regenerate health?

`moving_ext` `speed_max`

`paradrop_ext`\
TODO, complicated

`population_ext` `personnel_pop`

`sight_ext`
* `detect_camouflage` `tp_global`
* `sight_package` `outer_radius`

`type_ext`
* `type_target_weapon` References **_[type_target_weapon]_**
* `type_target_critical` References **_[type_target_critical]_**

`veterancy_ext` `experience_value`
    
### Vehicles

`ability_ext` `abilities` `ability_01` References **_[abilities]_**

`action_apply_ext` `actions` `ability_actions` `action_01` \
Used to upgrade the unit when requirements are met. Complex schema
* For upgrades with requirements, the `action_0X` has a reference to `[[action\ability_action\requirement_action.lua]]`.\
    `action_table` `upgrade_actions`  `action_0X`
    * If action has reference to `[[action\upgrade_action\add_weapon.lua]]`, look at
    `hardpoint`\
    `weapon` `weapon` Reference to **_[weapon]_**
    * If action has reference to `[[action\upgrade_action\change_weapon.lua]]`, look at
    `hardpoint`\
    `weapon` Reference to **_[weapon]_**
    * If action has reference to `[[action\upgrade_action\apply_modifiers_action.lua]]`, look at
    `modifiers` `modifier_0X` Reference to **_[modifiers]_**
    `modifiers` `modifiers_0X` `value`

    * For requirements, look at `requirement_table`\
    `required_X` References **_[requirements]_**\
    Typically `[[requirements\required_player_upgrade.lua]]`
        * `upgrade_name` References **_[upgrade]_**

`camouflage_ext` `detection_radius` What is this???

`combat_ext` `hardpoints` Vehicles can have multiple hardpoints
* `hardpoint_01`
    * `weapon_table `weapon_0X` `weapon` References **_[weapon]_**
    * `parent_hardpoint` reference to parent hardpoint number if there is one
* `hardpoint_02`    
* `hardpoint_03`
* `hardpoint_04`

`cover_ext` \
Speed multipliers for different cover types

`crush_ext` 
* `default_crush_mode` \
Crush type. I think this defaults to `crush_medium`
* `crushes_humans` \
Can the entity crush humans?

`health_ext`
* `can_repair`
Can this entity be repaired
* `hitpoints`
* `rear_damage_critical_type`\
References **_[type_target_critical]_**
* `rear_damage_enabled`\
Is rear damage possible to this entity?

`hit_object_ext` `projectile_pass_through` Is this actually useful?\

`hold_ext` Used when the entity can hold other entities
* `num_slots`
* `num_squad_slots`
* `percent_unload_on_death`

`moving_ext`
* `acceleration`
* `deceleration`
* `rotation_rate`
* `speed_max`
* `pass_type` Don't need reference. Is this useful?
* `turn_plan` Don't need reference. Is this useful?

`population_ext` `personnel_pop`

`sight_ext` 
* `detect_camouflage` `tp_global` number
* `sight_package` `outer_radius`

`type_ext`
* `type_target_weapon` References **_[type_target_weapon]_**
* `type_target_critical` References **_[type_target_critical]_**

`veterancy_ext` `experience_value`   
    

### Buildings

`action_apply_ext` `actions`
* `ability_actions` `action_0X`
    * `action_table` `upgrade_actions` `action_0X` References **_[action]_** most likely `[[action\upgrade_action\apply_modifiers_action.lua]]`
        * `modifiers` `modifier_01` References **_[modifiers]_**
            * `application_type`
            * `usage_type`
            * `value`
    * `requirement_table` `required_1` References **_[requirements]_** most likely `[[requirements\required_player_upgrade.lua]]`
        * `upgrade_name` References **_[upgrade]_**
* `upgrade_actions` `action_01` References `[[action\upgrade_action\upgrade_remove.lua]]`
    * `upgrade` References **_[upgrade]_**    

`aide_station_ext`
* `casualty_search_radius`
* `number_of_medics`

`combat_ext`
* `hardpoints` `hardpoints_01` `weapon_table` `weapon_01` `weapon` References **_[weapon]_**

`construction_ext` `on_construction_actions` 
* `ability_actions` for healing, debuffs
    * `action_0X` References **_[action]_**
        * `area_info` `radius` If the ability has a radius
        * `target_info` who the action targets
        * `unit_type` type of unit the ability acts on
        * `subactions` `action_0X` References **_[action]_** but really just care about `[[action\critical_action\apply_modifiers_action.lua]]`
            * `modifiers` `modifiers_0X` References References **_[modifiers]_**
                * `value`
                * `exclusive`
                * `modifier_id`
* `upgrade_actions` References `[[action\upgrade_action\change_weapon_target_type.lua]])` for change in target type weapon after construction is finished
    *  `action_01`
        * `new_type` References **_[type_target_weapon]_**
        * `original_type` References **_[type_target_weapon]_**  

`cost_ext` `time_cost` `time_seconds`

`garrison_ext` `max_units`

`health_ext` `hitpoints`

`population_ext` `personnel_pop`

`requirement_ext` the required upgrade for this to be built
* `requirement_table` `required_1` References **_[requirements]_** most likely `[[requirements\required_player_upgrade.lua]]`
    * `upgrade_name` References **_[upgrade]_**

`sight_ext`
* `detect_camouflage` `tp_global` number
* `sight_package` `outer_radius`

`type_ext`
* `type_target_weapon` References **_[type_target_weapon]_**
* `type_target_critical` References **_[type_target_critical]_**

`veterancy_ext` `experience_value`
    
### Emplacements

#### Trucks

`crush_ext` `default_crush_mode`

`engineer_ext` `construction_menus` `construction_menu_01` `construction_type`
Name will match that of the corresponding gun's `construction_ext` `construction_menus` `construction_menu_entry_01` `construction_type`
* The OMG unit CONSTNAME for the gun actually maps to the emplacement builder truck sbps, which has a emplacement builder truck ebps in the squad.

`health_ext` `hitpoints`

`moving_ext`
* `acceleration`
* `deceleration`
* `rotation_rate`
* `speed_max`
* `pass_type` Don't need reference. Is this useful?
* `turn_plan` Don't need reference. Is this useful?

`population_ext` No personnel_pop??

`sight_ext`
* `sight_package` `outer_radius`

`type_ext`
* `type_target_weapon` References **_[type_target_weapon]_**
* `type_target_critical` References **_[type_target_critical]_**

`veterancy_ext` `experience_value`

#### Guns

`ability_ext` `abilities` `ability_0X` References **_[abilities]_**

`action_apply_ext` `actions` `ability_actions` `action_01`
    * `action_table` `ability_actions` `action_01` References **_[action]_** most likely `[[action\ability_action\apply_modifiers_action.lua]]`
        * `modifiers` `modifier_01` References **_[modifiers]_**
            * `application_type`
            * `usage_type`
            * `value`
    * `requirement_table` `required_1` References **_[requirements]_** most likely `[[requirements\required_player_upgrade.lua]]`
        * `upgrade_name` References **_[upgrade]_**

`combat_ext` `hardpoints` `hardpoint_01` `weapon_table` `weapon_01` `weapon` references **_[weapon]_**

`construction_ext` `construction_menus` `construction_menu_entry_01` `construction_type`

`health_ext` `hitpoints`

`population_ext` No personnel_pop??

`sight_ext`
    * `sight_package` `outer_radius`

`type_ext`
* `type_target_weapon` References **_[type_target_weapon]_**
* `type_target_critical` References **_[type_target_critical]_**

`veterancy_ext` `experience_value`  
    
### Projectiles

`explosion_ext` `terrain_hit` `radius_min`/`radius_max`

`projectile_ext` `acceleration`/`speed`


