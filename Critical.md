# Critical

`critical_bag`

* `actions` `action_0X` References **_[action]_**
    * `delay`
    * `delayed_actions` `action_0X` References **_[action]_**
        * If action is `[[action\critical_action\apply_modifiers_action.lua]]`
            * `modifiers` `modifiers_0X` References **_[modifiers]_**
                * `value`
                * `exclusive`
        * If action is `[[action\critical_action\slot_item_remove.lua]]`
            * `slot_item` this slot item is removed
        * If action is `[[action\critical_action\remove_crew_action.lua]]`
            * `crew_name`
            * `kill` probably true
        * If action is `[[action\critical_action\apply_crew_action.lua]]`
            * `apply_removal`
            * `crew_name`
            * `kill` probably true
        * If action is `[[action\critical_action\make_wreck_action.lua]]`
            Nothing else
        * If action is `[[action\critical_action\out_of_control_action.lua]]`
            Nothing else
        * If action is `[[action\critical_action\make_dead.lua]]`
            Nothing else
