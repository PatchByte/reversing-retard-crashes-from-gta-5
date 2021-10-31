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


## Host Crash
As above i will not go into detail how it works
But it crashes here: GTA5 + 0x1092692

```c++

/* WARNING: Removing unreachable block (ram,0x7ff7800d244d) */
/* WARNING: Could not reconcile some variable overlaps */

void FUN_7ff7800d23c4(void)

{
  byte bVar1;
  uint uVar2;
  bool bVar3;
  char cVar4;
  longlong *plVar5;
  void *pvVar6;
  uint uVar7;
  uint uVar8;
  ulonglong uVar9;
  void *pvVar10;
  char *pcVar11;
  byte *pbVar12;
  byte bVar13;
  ulonglong uVar14;
  uint uVar15;
  uint uVar16;
  byte bVar18;
  ulonglong uVar19;
  uint uVar20;
  float fVar21;
  float fVar22;
  float fVar23;
  float fVar24;
  undefined8 local_68;
  ulonglong uVar17;
  
  pvVar10 = (void *)0x0;
  if (((is_in_session != false) &&
      (plVar5 = (longlong *)FUN_7ff7806b26b4(DAT_7ff78194cbc8,6), plVar5 != (longlong *)0x0)) &&
     (cVar4 = (**(code **)(*plVar5 + 0x100))(), cVar4 != '\0')) {
    if (DAT_7ff78194cbaa < 0x20) {
      pvVar10 = *(void **)(PTR_DAT_7ff780e15a90 + (ulonglong)DAT_7ff78194cbaa * 8 + 0x180);
    }
    DAT_7ff78194cbaa = DAT_7ff78194cbaa + 1 & 0x1f;
    if (((pvVar10 != (void *)0x0) && (bVar1 = *(byte *)((longlong)pvVar10 + 0x21), bVar1 != 0xff))
       && (pvVar6 = GetPedInfo(pvVar10), pvVar6 != (void *)0x0)) {
      uVar16 = ((uint)bVar1 + (uint)bVar1 * 8) * 4;
      uVar17 = (ulonglong)uVar16;
      uVar20 = uVar16 + 0x24;
      if ((uVar16 < 0x480) && (uVar20 < 0x481)) {
        if ((*(longlong *)((longlong)pvVar6 + 0xd0) == 0) ||
           (*(char *)(*(longlong *)((longlong)pvVar6 + 0xd0) + 0x469) == '\x06')) {
          thunk_FUN_7ff77fcfca85(&local_68,pvVar10,0,0,0);
          fVar24 = ((float)local_68 - 149.0) - -8192.0;
          if (fVar24 <= 0.0) {
            fVar24 = 0.0;
          }
          fVar22 = (local_68._4_4_ - 149.0) - -8192.0;
          if (fVar22 <= 0.0) {
            fVar22 = 0.0;
          }
          fVar23 = ((float)local_68 + 149.0) - -8192.0;
          if (fVar23 <= 0.0) {
            fVar23 = 0.0;
          }
          fVar21 = (local_68._4_4_ + 149.0) - -8192.0;
          if (fVar21 <= 0.0) {
            fVar21 = 0.0;
          }
          uVar19 = (ulonglong)(fVar24 * 0.01333333);
          uVar9 = (ulonglong)(fVar22 * 0.01333333);
          if (((byte)uVar19 <= (byte)(longlong)(fVar23 * 0.01333333)) &&
             ((byte)uVar9 <= (byte)(longlong)(fVar21 * 0.01333333))) {
            uVar7 = (uint)(longlong)(fVar23 * 0.01333333);
            uVar2 = (uint)(longlong)(fVar21 * 0.01333333);
            local_68 = uVar9;
            if (uVar16 < uVar20) {
              pbVar12 = (byte *)((longlong)&DAT_7ff78194cd10 + uVar17 * 3 + 1);
              uVar14 = uVar17;
              do {
                if ((pbVar12[1] != 0xff) &&
                   (((((int)(uint)pbVar12[-1] < (int)(((uint)uVar19 & 0xff) - 1) ||
                      ((uVar7 & 0xff) + 1 <= (uint)pbVar12[-1])) ||
                     ((int)(uint)*pbVar12 < (int)(((uint)uVar9 & 0xff) - 1))) ||
                    ((uVar2 & 0xff) + 1 <= (uint)*pbVar12)))) {
                  *(undefined2 *)(pbVar12 + -1) = 0;
                  pbVar12[1] = 0xff;
                  FUN_7ff7800c72c4();
                  uVar9 = local_68;
                }
                uVar15 = (int)uVar14 + 1;
                uVar14 = (ulonglong)uVar15;
                pbVar12 = pbVar12 + 3;
              } while (uVar15 < uVar20);
            }
            uVar7 = uVar7 & 0xff;
            if (((uint)uVar19 & 0xff) <= uVar7) {
              uVar15 = (uint)uVar9;
              do {
                uVar14 = uVar9 & 0xff;
                bVar18 = (byte)uVar19;
                uVar8 = uVar15 & 0xff;
                while (uVar8 <= (uVar2 & 0xff)) {
                  bVar3 = false;
                  pbVar12 = (byte *)((longlong)&DAT_7ff78194cd10 + 1);
                  uVar8 = 0;
                  do {
                    bVar13 = (byte)uVar14;
                    if (bVar3) goto LAB_7ff7800d271a;
                    if (((pbVar12[-1] == bVar18) && (*pbVar12 == bVar13)) && (pbVar12[1] != 0xff)) {
                      bVar3 = true;
                    }
                    uVar8 = uVar8 + 1;
                    pbVar12 = pbVar12 + 3;
                  } while (uVar8 < 0x480);
                  if ((!bVar3) && (bVar3 = false, uVar16 < uVar20)) {
                    pbVar12 = &DAT_7ff78194cd12 + (ulonglong)uVar16 * 3;
                    uVar9 = uVar17;
                    do {
                      if (bVar3) break;
                      if (*pbVar12 == 0xff) {
                        pbVar12[-2] = bVar18;
                        pbVar12[-1] = bVar13;
                        *pbVar12 = bVar1;
                        bVar3 = true;
                        FUN_7ff7800c72c4();
                      }
                      uVar8 = (int)uVar9 + 1;
                      uVar9 = (ulonglong)uVar8;
                      pbVar12 = pbVar12 + 3;
                    } while (uVar8 < uVar20);
                  }
LAB_7ff7800d271a:
                  uVar14 = (ulonglong)(byte)(bVar13 + 1);
                  uVar9 = local_68;
                  uVar8 = (uint)(byte)(bVar13 + 1);
                }
                uVar19 = (ulonglong)(byte)(bVar18 + 1);
              } while ((byte)(bVar18 + 1) <= uVar7);
            }
          }
        }
        else {
          if (uVar16 < uVar20) {
            pcVar11 = &DAT_7ff78194cd12 + uVar17 * 3;
            do {
              if (*pcVar11 != -1) {
                *(undefined2 *)(pcVar11 + -2) = 0;
                *pcVar11 = -1;
                FUN_7ff7800c72c4(uVar17);
              }
              uVar16 = (int)uVar17 + 1;
              uVar17 = (ulonglong)uVar16;
              pcVar11 = pcVar11 + 3;
            } while (uVar16 < uVar20);
          }
        }
      }
    }
  }
  return;
}

```

AND WOW! NICE WORK GTA! AGAIN SELF CALLING FUNCTION! NICE
FK YOU R* GAMES!

