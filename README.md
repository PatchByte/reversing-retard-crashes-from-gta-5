# reversing-retard-crashes-from-gta-5

## Bro Hug Crash
Well i will not leak how it works.
But where it crashes.

Base + 0x53D80B = crash

i really don't know what those variables are but i already reversed it a little bit
it basically crashes because it loops it self over and over

```c++

int FUN_7ff77f57d804(void *param_1)

{
  longlong lVar1;
  longlong *plVar2;
  void **next_obj_ptr;
  int totalCountLoops;
  longlong current_object;
  
  totalCountLoops = 0;
  while( true ) {
    current_object = *(longlong *)((longlong)param_1 + 0x50);
    if (current_object == 0) {
      plVar2 = (longlong *)0x0;
    }
    else {
      plVar2 = *(longlong **)(current_object + 0x48);
    }
    if ((plVar2 == (longlong *)0x0) || (((byte)*(undefined4 *)((longlong)plVar2 + 0x5c) & 0xf) < 2))
    {
      lVar1 = 0;
    }
    else {
      lVar1 = *plVar2;
    }
    if (lVar1 == 0) break;
    totalCountLoops = totalCountLoops + 1;
    if (current_object == 0) {
      next_obj_ptr = (void **)0x0;
    }
    else {
      next_obj_ptr = *(void ***)(current_object + 0x48);
    }
    if ((next_obj_ptr == (void **)0x0) ||
       (((byte)*(undefined4 *)((longlong)next_obj_ptr + 0x5c) & 0xf) < 2)) {
      param_1 = (void *)0x0;
    }
    else {
      param_1 = *next_obj_ptr;
    }
  }
  return totalCountLoops;
}

```
