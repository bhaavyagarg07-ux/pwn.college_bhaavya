# Citadel CTF

## Zahards welcome
flag was available in the discord server 

## The social network
instagram and twitter handles flags was available

## track 8
researched about pachinko album and it was vinegar it ressembles the decryption method vigenere 
using that got the flag

## Omniscient Flag's metadata
it striked my head that the picture is suspicious using llm i found out it had a png image hidden inside jpg image further useing steganographer seperator got the other image which had flag written

## Test of Sweetness
clciked on inspect and cookies changes the settings from user to admin and refreshed the website got the flag

## Rotten Apple 
in the hint the word rot was given hinting that rot 47 and rot 13 was used

## Randomly Accessed Memories
was going through the commits then some secret commits were there checked those and found out the flag was split into 3 parts and saved 

## Selected Ambient Work
after playing the wav file citadel with bracket and morse code was written. using online morse code reader read the flag and altered it according to the challenge

## Rotting in the Deep
using the hint the flag is converted into numbers and shifted 3 digits ahead. undoing this got the flag

## Coco Conjecture

```bash
import socket
import re

# Memoization cache for previously seen numbers
cache = {1: 0}

def collatz_steps(n):
    original = n
    steps = 0
    while n != 1:
        if n in cache:
            steps += cache[n]
            break
        if n % 2 == 0:
            while n % 2 == 0:
                n >>= 1  # fast division by 2
                steps += 1
        else:
            n = 3 * n + 1
            steps += 1
    cache[original] = steps
    return steps

HOST = "chall_citadel.cryptonitemit.in"
PORT = 61234

with socket.create_connection((HOST, PORT)) as s:
    f = s.makefile('rwb')
    while True:
        line = f.readline()
        if not line:
            break
        line_str = line.decode().strip()
        print(line_str)  # Optional: see server messages

        # Check for the flag
        flag = re.search(r'citadel\{.*?\}', line_str)
        if flag:
            print("\n🎯 FLAG:", flag.group(0))
            break

        # Extract round number
        m = re.search(r'Round \d+: (\d+)', line_str)
        if m:
            n = int(m.group(1))
            ans = collatz_steps(n)
            # Send answer immediately
            f.write(f"{ans}\n".encode())
            f.flush()
```
ran this in nano k.py and python3 k.py in wsl terminal


## schlagenhein
the wav file was corrupted and did not open. in the hint mid suggested midi file after using hex editor and playing in a online midi player the flag was displayed


## XOR slide
```bash
# Sliding XOR CTF Solver
# Ciphertext and known wrappers from challenge
import random

ct_hex = "b31113bd631c7207ec9587b32e686c8b6df255d66f4a987adacf6c283875ded5d1633b5f8823fa0b9bbbfab3195f1a51506afd54e03392ae338d872445c9025d88c8d4425a00a9b4478f86acadbd781df6a4194e376c09145a6f9afcbe02d36b5709f74d910edf94552dc4680041d6717fea824718c21385bdfd6176f722100548336d10ead87f01a95c5497dcb6c2"
ct = bytes.fromhex(ct_hex)

wrapper0 = b'bro i have a cRAzy story to tell you i went to ant4rctica and BOOM i saw a random '
wrapper1 = b' it was crazy like how did it get there??'

FLAG_LEN = 20
P_LEN = len(wrapper0) + FLAG_LEN + len(wrapper1)
KS_LEN = len(wrapper0) + len(wrapper1) + 9
ITER = P_LEN - KS_LEN + 1

# Helper index functions
def ks_bit(k, bit): return k * 8 + bit
def flag_bit(i, bit): return KS_LEN * 8 + i * 8 + bit

# Build XOR equations over GF(2)
rows, rhs = [], []
for p in range(P_LEN):
    if p < len(wrapper0):
        P = wrapper0[p]
        known = True
    elif p >= len(wrapper0) + FLAG_LEN:
        P = wrapper1[p - (len(wrapper0) + FLAG_LEN)]
        known = True
    else:
        P = 0
        known = False

    rhs_byte = ct[p] ^ P
    ks_range = [k for k in range(max(0, p - ITER + 1), min(KS_LEN - 1, p) + 1)]

    for bit in range(8):
        row = 0
        for k in ks_range:
            row |= 1 << ks_bit(k, bit)
        if not known:
            row |= 1 << flag_bit(p - len(wrapper0), bit)
        rows.append(row)
        rhs.append((rhs_byte >> bit) & 1)

# Enforce that the flag starts with 'flag{' and ends with '}'
flag_hint = b"flag{"
for i, ch in enumerate(flag_hint):
    for bit in range(8):
        rows.append(1 << flag_bit(i, bit))
        rhs.append((ch >> bit) & 1)

for bit in range(8):
    rows.append(1 << flag_bit(FLAG_LEN - 1, bit))
    rhs.append((ord('}') >> bit) & 1)

# Gaussian elimination
n = KS_LEN * 8 + FLAG_LEN * 8
m = len(rows)
rank = 0
pivot_cols = [-1] * m

for col in range(n):
    pivot = next((r for r in range(rank, m) if rows[r] >> col & 1), None)
    if pivot is None:
        continue
    rows[rank], rows[pivot] = rows[pivot], rows[rank]
    rhs[rank], rhs[pivot] = rhs[pivot], rhs[rank]
    for r in range(m):
        if r != rank and rows[r] >> col & 1:
            rows[r] ^= rows[rank]
            rhs[r] ^= rhs[rank]
    pivot_cols[rank] = col
    rank += 1
    if rank == m:
        break

# Extract solution
solution = [0] * n
for r in range(rank - 1, -1, -1):
    col = pivot_cols[r]
    val = rhs[r]
    mask = rows[r] & ~(1 << col)
    while mask:
        bit_idx = (mask & -mask).bit_length() - 1
        val ^= solution[bit_idx]
        mask &= mask - 1
    solution[col] = val

# Free variables
pivot_set = set(pivot_cols)
free_vars = [i for i in range(n) if i not in pivot_set and i != -1]

# Try random assignments until printable flag found
def solve_with_free(free_bits):
    sol = solution.copy()
    for i, bit in free_bits.items():
        sol[i] = bit
    # Back-solve pivot rows
    for r in range(rank):
        col = pivot_cols[r]
        if col == -1:
            continue
        s = rhs[r]
        mask = rows[r] & ~(1 << col)
        while mask:
            bit_idx = (mask & -mask).bit_length() - 1
            s ^= sol[bit_idx]
            mask &= mask - 1
        sol[col] = s
    flag = bytearray(FLAG_LEN)
    for i in range(FLAG_LEN):
        b = 0
        for bit in range(8):
            b |= sol[flag_bit(i, bit)] << bit
        flag[i] = b
    return flag

for _ in range(100000):
    free_assign = {v: random.getrandbits(1) for v in free_vars}
    flag = solve_with_free(free_assign)
    if all(32 <= c <= 126 for c in flag):
        print("Recovered flag:", flag.decode())
        break
```
Output
```bash 
Recovered flag: flag{L$#(!*l0l)u?Ab}
```


## The sound of music
Reading through the hints last hinted for last fm citadweller user i found one part of the flag then in rym another part and there was spotify link which gave the third part of the flag

## AetherCorp NetprobX
In order to try to find the loopholes in the website login database, we found SQL injecting could be one of the ways. But none of the usual commands worked , upon browsing we found %0A could be used before each command instead of ' and it worked. So we tried out the UNION SELECT attack along with injecting NULL.Until the no of NULL s exceeded the no of columns which were getting selected by the original SQL query, a particular error was showing error but the page changed when there were 3 Null. We got a list of employees but it didn't provide any useful clue. So then we used ls command to view all the files, we found potential files that could hold the key and then found blacksite_key.dat file and got the flag by reading it.

## Feels like we only go backwards
using https://dogbolt.org/?id=2d45bdb9-e245-4ac3-bff3-71fe224d8bfa#Ghidra=438 converted the file to code

```bash
#include "out.h"



void _DT_INIT(void)

{
  __gmon_start__();
  return;
}



void FUN_00101020(void)

{
  (*(code *)(undefined *)0x0)();
  return;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int puts(char *__s)

{
  int iVar1;
  
  iVar1 = puts(__s);
  return iVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

size_t strlen(char *__s)

{
  size_t sVar1;
  
  sVar1 = strlen(__s);
  return sVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int printf(char *__format,...)

{
  int iVar1;
  
  iVar1 = printf(__format);
  return iVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

size_t strcspn(char *__s,char *__reject)

{
  size_t sVar1;
  
  sVar1 = strcspn(__s,__reject);
  return sVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

char * fgets(char *__s,int __n,FILE *__stream)

{
  char *pcVar1;
  
  pcVar1 = fgets(__s,__n,__stream);
  return pcVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int setvbuf(FILE *__stream,char *__buf,int __modes,size_t __n)

{
  int iVar1;
  
  iVar1 = setvbuf(__stream,__buf,__modes,__n);
  return iVar1;
}



void __isoc99_scanf(void)

{
  __isoc99_scanf();
  return;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

void exit(int __status)

{
                    // WARNING: Subroutine does not return
  exit(__status);
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int getc(FILE *__stream)

{
  int iVar1;
  
  iVar1 = getc(__stream);
  return iVar1;
}



void __cxa_finalize(void)

{
  __cxa_finalize();
  return;
}



undefined8 FUN_00101100(void)

{
  setvbuf(stdout,(char *)0x0,2,0);
  setvbuf(stdin,(char *)0x0,2,0);
  puts(&DAT_00104080);
  FUN_001014c0();
  return 0;
}



void processEntry entry(undefined8 param_1,undefined8 param_2)

{
  undefined1 auStack_8 [8];
  
  __libc_start_main(FUN_00101100,param_2,&stack0x00000008,0,0,param_1,auStack_8);
  do {
                    // WARNING: Do nothing block with infinite loop
  } while( true );
}



// WARNING: Removing unreachable block (ram,0x00101193)
// WARNING: Removing unreachable block (ram,0x0010119f)

void FUN_00101180(void)

{
  return;
}



// WARNING: Removing unreachable block (ram,0x001011d4)
// WARNING: Removing unreachable block (ram,0x001011e0)

void FUN_001011b0(void)

{
  return;
}



void _FINI_0(void)

{
  if (DAT_0010e4a8 != '\0') {
    return;
  }
  __cxa_finalize(PTR_LOOP_00104068);
  FUN_00101180();
  DAT_0010e4a8 = 1;
  return;
}



void _INIT_0(void)

{
  FUN_001011b0();
  return;
}



undefined8 FUN_00101240(char *param_1)

{
  size_t sVar1;
  long lVar2;
  byte local_88 [48];
  short local_58 [40];
  
  local_88[0] = 3;
  local_88[1] = 7;
  local_88[2] = 0xb;
  local_88[3] = 0xf;
  local_88[4] = 0xb;
  local_88[5] = 7;
  local_88[6] = 3;
  local_88[7] = 7;
  local_88[8] = 0xb;
  local_88[9] = 0xf;
  local_88[10] = 0xb;
  local_88[0xb] = 7;
  local_88[0xc] = 3;
  local_88[0xd] = 7;
  local_88[0xe] = 0xb;
  local_88[0xf] = 0xf;
  local_88[0x10] = 0xb;
  local_88[0x11] = 7;
  local_88[0x12] = 3;
  local_88[0x13] = 7;
  local_88[0x14] = 0xb;
  local_88[0x15] = 0xf;
  local_88[0x16] = 0xb;
  local_88[0x17] = 7;
  local_88[0x18] = 3;
  local_88[0x19] = 7;
  local_88[0x1a] = 0xb;
  local_88[0x1b] = 0xf;
  local_88[0x1c] = 0xb;
  local_88[0x1d] = 7;
  local_88[0x1e] = 3;
  local_88[0x1f] = 7;
  local_88[0x20] = 0xb;
  local_88[0x21] = 0xf;
  local_88[0x22] = 0xb;
  local_88[0x23] = 7;
  local_88[0x24] = 3;
  local_58[0] = 0xc9;
  local_58[1] = 0xde;
  local_58[2] = 0xfd;
  local_58[3] = 0xe0;
  local_58[4] = 0xe7;
  local_58[5] = 0xea;
  local_58[6] = 0xf9;
  local_58[7] = 0x120;
  local_58[0x20] = 399;
  local_58[0x21] = 0x11c;
  local_58[0x22] = 0x183;
  local_58[0x23] = 0x11c;
  local_58[8] = 0xff;
  local_58[9] = 0x9c;
  local_58[10] = 0x121;
  local_58[0xb] = 0xfc;
  local_58[0xc] = 0x9f;
  local_58[0xd] = 0x124;
  local_58[0xe] = 0xb7;
  local_58[0xf] = 0x118;
  local_58[0x24] = 0x1b1;
  local_58[0x10] = 0x135;
  local_58[0x11] = 0xbc;
  local_58[0x12] = 0x141;
  local_58[0x13] = 0xcc;
  local_58[0x14] = 0x12d;
  local_58[0x15] = 0x148;
  local_58[0x16] = 0xd9;
  local_58[0x17] = 0x164;
  local_58[0x18] = 0x15f;
  local_58[0x19] = 0x142;
  local_58[0x1a] = 0xef;
  local_58[0x1b] = 0x154;
  local_58[0x1c] = 0x15d;
  local_58[0x1d] = 0x100;
  local_58[0x1e] = 0x175;
  local_58[0x1f] = 0x160;
  sVar1 = strlen(param_1);
  if (sVar1 == 0x25) {
    lVar2 = 0;
    while (local_58[lVar2] ==
           (ushort)((ushort)local_88[lVar2] + ((ushort)lVar2 & 0xff) * 5 +
                   (ushort)(byte)param_1[lVar2] * 2)) {
      lVar2 = lVar2 + 1;
      if (lVar2 == 0x25) {
        return 1;
      }
    }
  }
  return 0;
}



void FUN_00101340(void)

{
  int iVar1;
  char *pcVar2;
  size_t sVar3;
  long local_90;
  char local_88 [128];
  
  puts("\n=== LEVEL 2 ===");
  puts("it\'s time for some mind mischief! ");
  puts("what number is kevin parker thinking of right now: ");
  iVar1 = __isoc99_scanf(&DAT_00102015,&local_90);
  if (iVar1 != 1) {
    puts("Bad input.");
                    // WARNING: Subroutine does not return
    exit(0);
  }
  if (4 < local_90 - 0x1e6d9e9c7U) {
    puts("why won\'t you make up your mind? the number he\'s thinking of is way cooler");
    return;
  }
  puts("see! all you had to do was let it happen. ");
  puts("but let\'s hope it wasn\'t just instant destiny. ");
  puts("\n=== LEVEL 3 ===");
  puts(
      "don\'t make kevin wait for one more year. give him the flag and set your reality in motion! "
      );
  printf("Flag: ");
  do {
    iVar1 = getc(stdin);
    if (iVar1 == -1) break;
  } while (iVar1 != 10);
  pcVar2 = fgets(local_88,0x80,stdin);
  if (pcVar2 == (char *)0x0) {
    puts("Input error.");
                    // WARNING: Subroutine does not return
    exit(0);
  }
  sVar3 = strcspn(local_88,"\n");
  local_88[sVar3] = '\0';
  iVar1 = FUN_00101240(local_88);
  if (iVar1 != 0) {
    puts(
        "RIGHT YOU ARE ! ! ! maybe you can also predict the release date of his next album, but that\'s for another challenge..."
        );
    return;
  }
  puts("new attempt, same old mistakes");
  return;
}



undefined8 FUN_001014c0(void)

{
  char *pcVar1;
  size_t sVar2;
  ulong uVar3;
  uint uVar4;
  ulong uVar5;
  char *__s;
  long lVar7;
  undefined8 *puVar8;
  undefined8 local_218 [2];
  char local_208 [512];
  ulong uVar6;
  
  puVar8 = local_218;
  puts("=== LEVEL 1 ===");
  __s = local_208;
  printf("kevin wants you to sing your heart out, it could be some music to walk home by: ");
  pcVar1 = fgets(__s,0x200,stdin);
  if (pcVar1 == (char *)0x0) {
    puts("Input error.");
  }
  else {
    sVar2 = strcspn(__s,"\n");
    uVar3 = 0x10;
    if (sVar2 < 0x11) {
      uVar3 = sVar2;
    }
    if (7 < (uint)uVar3) {
      uVar5 = 0;
      do {
        uVar4 = (int)uVar5 + 8;
        uVar6 = (ulong)uVar4;
        *(undefined8 *)((long)local_218 + uVar5) = *(undefined8 *)(__s + uVar5);
        uVar5 = uVar6;
      } while (uVar4 < ((uint)uVar3 & 0xfffffff8));
      puVar8 = (undefined8 *)((long)local_218 + uVar6);
      __s = __s + uVar6;
    }
    lVar7 = 0;
    if ((uVar3 & 4) != 0) {
      *(undefined4 *)puVar8 = *(undefined4 *)__s;
      lVar7 = 4;
    }
    if ((uVar3 & 2) != 0) {
      *(undefined2 *)((long)puVar8 + lVar7) = *(undefined2 *)(__s + lVar7);
      lVar7 = lVar7 + 2;
    }
    if ((uVar3 & 1) != 0) {
      *(char *)((long)puVar8 + lVar7) = __s[lVar7];
    }
    if (0xf < sVar2) {
      puts("okay okay maybe the sun\'s coming up.");
      FUN_00101340();
      return 1;
    }
    puts("maybe your song needs to be a full length song rather than a snippet");
  }
  return 0;
}



void _DT_FINI(void)

{
  return;
}
```
running this got the flag 
```bash
Level 1: The Song (Input Length Check)
The code reads your input string and checks its length. The function FUN_001014c0 proceeds to the next level only if the length of the string (before removing the newline) is greater than 15.

Condition: Input string length ≥16 characters.

Solution: Any string of 16 or more characters will work.

kevin wants you to sing your heart out, it could be some music to walk home by:
This is my very long song of sixteen chars.
Level 2: The Number (Math Check)
The function FUN_00101340 reads a large integer into the variable local_90 and performs a comparison using an unsigned difference.

The success condition is:

local_90−0x1e6d9e9c7U≤4
This requires the input number to be within 4 units of the constant 0x1e6d9e9c7.

Constant value (Hex): 0x1e6d9e9c7

Constant value (Decimal): 81923050887

Solution: Any number in the range 81923050887 to 81923050891 will pass.

what number is kevin parker thinking of right now:
81923050888
Level 3: The Flag (Verification Algorithm)
The function FUN_00101240 checks the flag. It requires the flag to be exactly 37 characters long and then iterates through each character, verifying it against two pre-defined constant arrays (local_88 and local_58).

The check for each character at index i is:

E[i]=A[i]+(i×5)+(Flag[i]×2)
Where:

E[i] is the expected value from local_58.

A[i] is the byte constant from local_88.

i is the index (0 to 36).

By solving for Flag[i] in a loop for all 37 indices, we can recover the correct flag.

Solution:

Flag:
citadel{f0r_0n3_m0r3_h0ur_1_c4n_r4g3}
```


