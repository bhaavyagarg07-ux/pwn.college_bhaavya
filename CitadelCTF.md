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


