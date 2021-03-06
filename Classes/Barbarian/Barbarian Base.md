## Brutal Critical
```GN
!servalias brutal embed
{{set("lvl", int(BarbarianLevel))}}
{{set('die', 'd10' if "%1"+"%"=="%1%" else 'd%1%' if '%1%'[0] != 'd' else '%1%')}}
{{set('numDice', 3 if lvl>=17 else 2 if lvl>=13 else 1)}}
-title "<name> scores a brutal critical!"
-desc "You can roll {{numDice}} additional weapon damage die when determining the extra damage for a critical hit with a melee attack."
-f "Damage|{{vroll(str(numDice) + die)}}"
-footer "Barbarian | PHB 48" -color <color> -thumb <image>
```

## Rage Alias
```GN
!servalias rage embed
{{set("lvl", int(BarbarianLevel))}}
{{set("counter", "Rage")}}
{{set("bonus", 4 if lvl>15 else 3 if lvl>8 else 2)}}
{{mod_cc(counter, -1, True) if lvl<20 else 0}}
-title "<name> goes into a Rage!"
-desc "In battle, you fight with primal ferocity. On your turn, you can enter a rage as a bonus action.
While raging, you gain the following benefits if you aren't wearing heavy armor:
* You have advantage on Strength checks and Strength saving throws.
* When you make a melee weapon attack using Strength, you gain a bonus to the damage roll.
* You have resistance to bludgeoning, piercing, and slashing damage.
If you are able to cast spells, you can't cast them or concentrate on them while raging.
Your rage lasts for 1 minute. It ends early if you are knocked unconscious or if your turn ends and you haven't attacked a hostile creature since your last turn or taken damage since then. You can also end your rage on your turn as a bonus action.
Once you have raged the maximum number of times for your barbarian level, you must finish a long rest before you can rage again."
-f "Rage Damage|{{bonus}}"
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Barbarian | PHB 48" -color <color> -thumb <image>
```

## Rage Snippet
```GN
!servsnippet rage -d "{{2 if int(BarbarianLevel)<8 else (3 if int(BarbarianLevel)<15 else 4)}} [Rage]"
```