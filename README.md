# Adding a Customized Czech Keyboard Layout to Ubuntu

This guide will help you add a new keyboard layout to your Ubuntu system. The new layout is a full-size keyboard where the first layer is the Czech layout and the second layer is the English layout with some changes and compromises.

![obrazek](https://github.com/user-attachments/assets/1d1bb237-2703-41c5-95cb-965946b63d6c)

## Step 1: Add `xkb_symbols` Layout

1. Open a terminal.
2. Edit the `cz` file located in the `/usr/share/X11/xkb/symbols/` directory with your preferred text editor (you may need root privileges to edit this file). For example, you can use `nano`:

   ```bash
   sudo nano /usr/share/X11/xkb/symbols/cz
   ```

3. Add your custom `xkb_symbols` layout at the end of the file. Here is an example snippet you might add:

   ```plaintext
   xkb_symbols "cz-prog" {
   
       // This layout is Czech layout with English special symbols.
       // Those are merged into each oether and there are some compromises.
       // 2023 by Tomas Nevoral <NevoralTomas@gmail.com>
   
       include "latin"
       name[Group1]= "Czech (prog)";
   
       key <TLDE>  {[  grave_accent,    asciitilde ] };
       key <AE01>  {[         equal,        exclam ] };
       key <AE02>  {[        ecaron,            at ] };
       key <AE03>  {[        scaron,    numbersign ] };
       key <AE04>  {[        ccaron,        dollar ] };
       key <AE05>  {[        rcaron,       percent ] };
       key <AE06>  {[        zcaron,   asciicircum ] };
       key <AE07>  {[        yacute,     ampersand ] };
       key <AE08>  {[        aacute,      asterisk ] };
       key <AE09>  {[        iacute,     parenleft ] };
       key <AE10>  {[        eacute,    parenright ] };
       key <AE11>  {[         minus,    underscore ] };
       key <AE12>  {[    dead_acute,    dead_caron ] };
   
       key <AD01>  {[             q,             Q ] };
       key <AD02>  {[             w,             W ] };
       key <AD03>  {[             e,             E ] };
       key <AD04>  {[             r,             R ] };
       key <AD05>  {[             t,             T ] };
       key <AD06>  {[             z,             Z ] };
       key <AD07>  {[             u,             U ] };
       key <AD08>  {[             i,             I ] };
       key <AD09>  {[             o,             O ] };
       key <AD10>  {[             p,             P ] };
       key <AD11>  {[   bracketleft,     braceleft ] };
       key <AD12>  {[  bracketright,    braceright ] };
   
       key <AC01>  {[             a,             A ] };
       key <AC02>  {[             s,             S ] };
       key <AC03>  {[             d,             D ] };
       key <AC04>  {[             f,             F ] };
       key <AC05>  {[             g,             G ] };
       key <AC06>  {[             h,             H ] };
       key <AC07>  {[             j,             J ] };
       key <AC08>  {[             k,             K ] };
       key <AC09>  {[             l,             L ] };
       key <AC10>  {[     semicolon,         colon ] };
       key <AC11>  {[    apostrophe,      quotedbl ] };
       key <BKSL>  {[dead_abovering,         uring ] };
   
       key <LSGT>  {[     backslash,           bar ] };
       key <AB01>  {[             y,             Y ] };
       key <AB02>  {[             x,             X ] };
       key <AB03>  {[             c,             C ] };
       key <AB04>  {[             v,             V ] };
       key <AB05>  {[             b,             B ] };
       key <AB06>  {[             n,             N ] };
       key <AB07>  {[             m,             M ] };
       key <AB08>  {[         comma,   	   less ] };    
       key <AB09>  {[        period,   	greater ] };
       key <AB10>  {[         slash,      question ] };
   
       key <SPCE>  {[         space,         space ] };
   
       include "level3(ralt_switch)"
   };
   ```

4. Save and close the file.

## Step 2: Update `evdev.lst`

1. In the terminal, edit the `evdev.lst` file located in the `/usr/share/X11/xkb/rules/` directory:

   ```bash
   sudo nano /usr/share/X11/xkb/rules/evdev.lst
   ```

2. Scroll to the section where keyboard layouts are listed and add the following line:

   ```plaintext
   cz-prog         cz: Czech (prog)
   ```

3. Save and close the file.

## Step 3: Update `evdev.xml`

1. In the same `/usr/share/X11/xkb/rules/` directory, edit the `evdev.xml` file:

   ```bash
   sudo nano /usr/share/X11/xkb/rules/evdev.xml
   ```

2. Find the `cz` layout section and add the following code snippet under it:

   ```xml
   <variant>
      <configItem>
         <name>cz-prog</name>
         <description>Czech (prog)</description>
      </configItem>
   </variant>
   ```

3. Save and close the file.

## Step 4: Reboot Your System

For the changes to take effect, you need to restart your computer. You can do this from the terminal by typing:

```bash
sudo reboot
```

After the system reboots, the new keyboard layout should be available in your keyboard settings.
