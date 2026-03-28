# Cornix Layout Plan

This is the planned direction for porting the Corne-inspired layout onto the 50-key Cornix while keeping Cornix-specific structure.

## Physical Cornix Shape

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| 0,0  | 0,1  | 0,2  | 0,3  | 0,4  | 0,5  |        | 0,8  | 0,9  | 0,10 | 0,11 | 0,12 | 0,13 |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| 1,0  | 1,1  | 1,2  | 1,3  | 1,4  | 1,5  |        | 1,8  | 1,9  | 1,10 | 1,11 | 1,12 | 1,13 |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| 2,0  | 2,1  | 2,2  | 2,3  | 2,4  | 2,5  | 2,6 | 2,7 | 2,8  | 2,9  | 2,10 | 2,11 | 2,12 | 2,13 |
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| 3,0  | 3,1  | 3,2  | 3,3  | 3,4  | 3,5  |        | 3,8  | 3,9  | 3,10 | 3,11 | 3,12 | 3,13 |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```

## Planned Base Layer

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| TAB  | Q    | W    | E    | R    | T    |        | Y    | U    | I    | O    | P    | BSPC |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| CTL/ | A    | S    | D    | F    | G    |        | H    | J    | K    | L    | ;    | '    |
| ESC  |      |      |      |      |      |        |      |      |      |      |      |      |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| SHFT | Z    | X    | C    | V    | B    | MUTE | ???  | N    | M    | ,    | .    | /    | LOWER |
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| LCTL | LGUI | LALT | LOWER | LGUI | SPACE|        | ENTER| ALT | RAISE | RALT | RGUI | RCTL |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```

## Binding Intent

- Keep dedicated `Ctrl` hold / `Esc` tap on the left home-row outer key.
- Keep the Cornix-specific bottom row instead of forcing the Corne thumb arrangement.
- Left bottom row should imitate a standard keyboard modifier cluster: `LCTRL`, `LGUI`, `LALT`.
- Keep the right-bottom modifier cluster in standard order: `RALT`, `RGUI`, `RCTRL`.
- Preserve `LOWER`, `RAISE`, and conditional `ADJUST/HYPER`.
- `ADJUST/HYPER` should include mouse movement and Bluetooth controls.
- Keep `&trans` on upper layers unless a key is intentionally overridden.

## Open Slots To Decide

```text
2,7   : extra center-right key on row 3
3,3   : left inner bottom key
3,8   : right inner bottom key
```

Most likely use:

- `3,3` for a dedicated base-layer utility such as `LGUI` passthrough, `LOWER`, or `ESC`
- `3,8` for `RAISE` or `BACKSPACE`
- `2,7` for a Cornix-only extra such as `BACKSPACE`, `DEL`, or `TAB`

## Planned Layer Set

- `BASE`: Corne-like typing layout adapted to Cornix
- `LOWER`: numbers, media, navigation
- `RAISE`: symbols
- `ADJUST/HYPER`: mouse and Bluetooth

## Planned Base

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| TAB  | Q    | W    | E    | R    | T    |        | Y    | U    | I    | O    | P    | BSPC |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
|CTL/ES| A    | S    | D    | F    | G    |        | H    | J    | K    | L    | ;    | '    |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| SHFT | Z    | X    | C    | V    | B    | MUTE | ???  | N    | M    | ,    | .    | /    | LOWER|
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| LCTL | LGUI | LALT | LOWER| LGUI | SPC  |        | ENT  | ALT  | RAISE| RALT | RGUI | RCTRL|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```

## Planned Lower

Corne-inspired number and navigation layer, with transparency kept by default.

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| TAB  | 1    | 2    | 3    | 4    | 5    |        | 6    | 7    | 8    | 9    | 0    | BSPC |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| &trns| VOL- | VOL+ | MUTE | &trns| &trns|        | LEFT | DOWN | UP   | RIGHT| &trns| &trns|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| SHFT | &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns|
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| LCTL | LGUI | LALT | &trns| &trns| SPC  |        | LA(ENT)| &trns| &trns| RALT | RGUI | RCTRL|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```

## Planned Raise

Corne-inspired symbols layer, with most non-symbol keys transparent.

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| TAB  | 1    | 2    | 3    | 4    | 5    |        | 6    | 7    | 8    | 9    | 0    | BSPC |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| LCTRL| &trns| &trns| &trns| &trns| &trns|        | -    | =    | [    | ]    | \    | `    |
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| SHFT | &trns| &trns| &trns| &trns| &trns| &trns| &trns| _    | +    | {    | }    | |    | ~    |
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| LCTL | LGUI | LALT | &trns| &trns| SPC  |        | ENT  | &trns| &trns| RALT | RGUI | RCTRL|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```

## Planned Adjust / Hyper

Conditional layer entered from `LOWER + RAISE`. This keeps mouse and Bluetooth controls from the Corne.

```text
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| &trns| &trns| &trns| &trns| &trns| &trns|        | &trns| &trns| &trns| &trns| &trns| &trns|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
| &trns| &trns| MB3  | MB2  | MB1  | &trns|        | M←   | M↓   | M↑   | M→   | &trns| &trns|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
|BTCLR | BT1  | BT2  | BT3  | &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns| &trns|
+------+------+------+------+------+------+------+------+------+------+------+------+------+------+
| &trns| &trns| &trns| &trns| &trns| &trns|        | &trns| &trns| &trns| &trns| &trns| &trns|
+------+------+------+------+------+------+        +------+------+------+------+------+------+
```
