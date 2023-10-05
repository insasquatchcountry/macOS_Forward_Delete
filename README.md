# macOS_Forward_Delete
A simple way to re-map an unused Caps-Lock key to a surprisingly useful forward-delete alternative.
---
# but like... why tho 🤨

This idea started forming when I first switched to an alternate keyboard layout.

After experimenting with [Dvorak](https://www.daskeyboard.com/blog/the-dvorak-keyboard-layout/) which an old roommate, now friend, of mine had used for years, I even skipped over [Colemak](https://colemak.com)  after buying in, briefly, to the arguments for [Workman](https://workmanlayout.org/#the-problem-with-colemak) in regards to lateral movement. As someone who has played piano and guitar for years, this sideways movement doesn't seem to bother me nearly as much as I was initially led to believe it would.

After having used Workman exclusivly for over a month. I tried [Colemak](https://colemak.com) and almost instantly preferred how roll-ey and overall comfortable it felt.

Pronounced /'ko:lmæk/ (Coal-Mac) named after its creator, [Shai Coleman](https://shaicoleman.com/shai-coleman.pdf).

### The fact that it comes pre-installed on both macOS and iOS gives it a certain amount of credibility in my eyes.

![layout](https://colemak.com/wiki/images/a/ad/Colemak_vs_qwerty.jpg)
 
 **QWERTY:** Hello, this is what it feels like to type this sentence in Colemak!

**Colemak:** Hkuu;, fhld ld whaf lf ekkud ulnk f; fork fhld dkjfkjck lj C;ukman!

[Give it a try](https://colemak.com/Converter)!

---
# get to the point guy 😤
Anyway, with the use of the Colemak Layout, it is standard to re-map the underutilized Caps Lock key to Backspace.

I've also heard of Vim users Mapping Esc to Caps Lock but that's neither here nor there.

The idea of minimizing the distance I have to reach for backspace was intriguing but I found that 
1. It was very difficult to remap that gesture.
2. As I got better at touch typing, I used backspace a lot less.
3. I hardly ever use Caps Lock.

This setup kinda reminds me of the western style of horseback riding, where you push the reins against the side of the face you wish the horse to turn towards.

Since regular Backspace is on the right pinkie, then it makes sense for its opposite to be on the left pinkie.

The only free-app I'm aware of that can first remap the caps lock key is [Karabiner-Elements.app](https://karabiner-elements.pqrs.org)

I think this can also be done with the paid-app [BetterTouchTool.app](https://folivora.ai)

To extend the same 'by word' and 'by line' functions that command and option add to normal backspace, I use [Hammerspoon.app](https://www.hammerspoon.org)

# Install with [Homebrew](https://brew.sh)

```
brew install karabiner-elements
brew install hammerspoon
```

# Setup

To get Caps Lock remapped to backspace including autorepeat:

System Preferences → Keyboard → Keyboard → Modifier Keys ... → set Caps Lock to 'No Action'


Karabiner-Elements.app → Settings → Simple Modifications

 +Add Item:  'caps_lock' -------> 'delete_forward'

---
Append these lines of code to your Hammerspoon config

located: ~/.hammerspoon/init.lua

```
-- forward delete by word

hs.hotkey.bind({'option'}, 'forwarddelete', function()

    hs.eventtap.keyStroke({'option' , 'shift'}, 'right')
    hs.eventtap.keyStroke({}, 'delete')

end)

-- forward delete by line

hs.hotkey.bind({'cmd'}, 'forwarddelete', function()

    hs.eventtap.keyStroke({'cmd' , 'shift'}, 'right')
    hs.eventtap.keyStroke({}, "delete")

end)

-- Vim esc (this is me hoping I start using Vim or Spacemacs)

hs.hotkey.bind({'shift'}, 'forwarddelete', function()

    hs.eventtap.keyStroke({},'escape')

end)
```


---

✅ be sure to reload you Hammerspoon config 👍 

---

# Test

delete this letter as normal - A

B - use C.L. to forward delete that letter

use option to delete this word - Cat

Dog - now forward delete that word

delete this entire line

forward delete this entire line

