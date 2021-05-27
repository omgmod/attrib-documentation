
## Squad ability upgrades
Squads in the battlefile are assigned OMGUPG upgrades, which map via `omg_ability_upgrade_const.scar`
to an `upgrade`. 

Ex, a Grenadier squad has a medkit upgrade
* so it will have `OMGUPG.AXIS.MEDPACK` in the battle file, which maps to `upgrade/omg/axis/items/medpack.lua`.
* `upgrade/omg/axis/items/medpack.lua` has two actions, each is a reference to `[[action\upgrade_action\slot_item_add.lua]]`
with a slot_item of `[[slot_item\axis_medpack.rgd]]`, adding two medpack slot items to the squad.
* The slot item's contents aren't particularly important, but the Grenadier sbps has an ability
`squad_ability_ext` `abilities` `ability_05"` = `[[abilities\medical_kit.lua]]`.
* `abilities\medical_kit.lua` does several things
    * It has two requirements it checks:
        * The sbps has `[[requirements\required_squad_upgrade.lua]]` with `upgrade_name` = `[[upgrade\omg\axis\items\medpack.rgd]]`
        * The sbps has `[[requirements\required_slot_item.lua]]` with minimum 1 of `slot_item` = `[[slot_item\axis_medpack.rgd]]`
    * Then it has several actions in the `action_list`:
        * On starting the ability use in `start_target_actions`
            * It `[[action\ability_action\apply_modifiers_action.lua]]` applies the `[[modifiers\health_regeneration_modifier.lua]]` modifier
            to begin health regeneration at a value of `0.150000006` via `usage_type` of `[[addition]]`. As health regen ticks 8 times
            per second, this is a health regen rate of 1.2hp/s or 72hp/min
            * It has a requirement action `[[action\ability_action\requirement_action.lua]]` with requirement of
            `[[requirements\required_player_upgrade.lua]]` requiring `upgrade_name`=`[[upgrade\omg\axis\docmarkers\blitz\tr2\b2\t2.rgd]]`
            and `is_present` = `false`. 
                * If this upgrade is not present, then it applies the action's ability actions, which
                is an action  `[[action\ability_action\apply_modifiers_action.lua]]` of duration 18 and modifier
                `[[modifiers\posture_speed_modifier.lua]]` with value `-1`.
    * The ability has a `duration_time` of 60 and a `recharge_time` of 180.
    
Ex. a 57mm AT Gun has Infantry Doctrine HVAP AP rounds
* so it will have `OMGUPG.ALLY.AT_AP_ROUNDS` which is the same name as used by the regular AP round. This maps to
`upgrade/omg/allies/items/allies_apat.lua`. 
* `upgrade/omg/allies/items/allies_apat.lua` has an action applying the upgrade to entities in the squad. The 57mm AT gun squad
has nothing to do with this ability.
* The `ebps/races/allies/vehicles/m1_57mm_towed_at_gun.lua` has abilities including `[[abilities\allied_at_apc_shell.rgd]]` 
and `[[abilities\allied_at_apc_shell_T1.rgd]]`. These represent the two variations of the AP round ability. Each has different
action modifiers for damage and different duration times. 
    * They both have a requirement for `[[requirements\required_player_upgrade.lua]]` with the docmarker
    upgrade `[[upgrade\omg\allies\docmarkers\infantry\tr2\b2\t1.rgd]]` but the `[[abilities\allied_at_apc_shell.rgd]]` has `is_present`
    set to false so that it does not appear when that docmarker is present, while the stronger `[[abilities\allied_at_apc_shell_T1.rgd]]`
    does need that docmarker present. 
    
    

1. So from the battle file side, we know the set of all units and upgrades that are selectable in game.
2. We can get the CONSTNAMES for those units and upgrades
3. We can get the mapped attrib files:
    * sbps for units
    * upgrade for upgrades
4. Get the set of all ebps used by those sbps.
5. Units have abilities on their entities, so get all abilities on those ebps.

