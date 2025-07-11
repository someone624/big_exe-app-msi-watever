# ```big_exe-app-msi-watever``` - The platform/language
<!-- yes that is the name just The platform thats it -->
> A real enterprise-grade deployment toolchain. Features are
- You need to code in Python 2.6 (because why not)
- Auto-bloats the whole thing
- Uses pyinstaller with no compression
- Automatically puts useless comments
- Cant delete comments
## Bonus
- No version numbers (or anything similar)
- No uninstall script (for enterprise security)
- Extra enterprise features:
  - No imports
# The language
- Python 2.6
- Every script starts with the sacred line:
```python
from big_exe import *
```
You dont write that line. It's just there.
Then you write your normal code:
```python
print math.sqrt(16)
```
And boom you've just got a 300 MB executable that says `4.0`
## things
The second you run your script, we will do this command.
```shell
pyinstaller --onefile --noupx app.py
```
Which outputs:
- An exe bigger than your hopes and dreams
- 0 compression
- 10 hours loading maybe
- "ooh look at this cool program its doing litteraly doing **everything** at the same time"
- Confused reverse-engineers
# System (and more...) requirments
- Windows XP SP2 or newer
- 512 MB of VRAM
- A deep sense of regret
> [!WARNING]
> On machines with less than 2GB VRAM, the print statement might fail with a "Missing CUDA core sarcasm driver" error.
