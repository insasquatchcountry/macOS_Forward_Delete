# macOS_Forward_Delete
How I use my Caps Lock key as a forward delete.
---

The only free app I'm aware of that can first remap the caps lock key is [Karabiner-Elements.app](https://karabiner-elements.pqrs.org)

I think this can also be done with the paid app [BetterTouchTool.app](https://folivora.ai)

To extend the same 'by word' and 'by line' functions that command and option add to normal backspace, I use [Hammerspoon.app](https://www.hammerspoon.org)

# Install with [Homebrew](https://brew.sh)

```
brew install karabiner-elements
brew install hammerspoon
```

# Setup

Karabiner-Elements.app → Settings → Simple Modifications

 +Add Item:  'caps_uock' --> 'delete_forward'

---
Append these lines of code to your Hammerspoon config

located: ~/.hammerspoon/init.lua

```
-- forward delete by word

hs.hotkey.bind({'option'}, 'forwarddelete', function()

    hs.eventtap.keyStroke({'option' , 'shift'}, 'right')
    hs.eventtap.keyStroke({}, "delete")

end)

-- forward delete by line

hs.hotkey.bind({'cmd'}, 'forwarddelete', function()

    hs.eventtap.keyStroke({'cmd' , 'shift'}, 'right')
    hs.eventtap.keyStroke({}, "delete")

end)
```


---

✅ reload config 👍 

---

# Test



delete this letter as normal - A

B - use C.L. to forward delete that letter

use option to delete this word - Cat

Dog - now forward delete that word

delete this entire line

forward delete this entire line

