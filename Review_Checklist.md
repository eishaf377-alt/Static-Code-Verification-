# Review Checklist

## Static Code Verification

| Category | Result (Issue/OK) | Defect |
|---|---|---|
| Initialization | Issue | `double sum` in `averageAttack()` is not initialized before use. |
| Pointers | Issue | Raw pointers are used without proper null checking, and a pointer is accessed after deletion. |
| Arrays / Buffers | Issue | The array can store 5 monsters, but 6 monsters are added. The boss-name buffer also has a fixed size. |
| Loops | Issue | The loop in `totalMonsterHealth()` uses `<=`, which can access an invalid array position. |
| Arithmetic | Issue | `damage` is converted to `unsigned int`, and the uninitialized `sum` is used in a calculation. |
| Control Flow | Issue | `playerRank()` does not return a value when `score <= 100`. |
| Function Calls | Issue | `attackMonster()` is called with an invalid monster ID and the returned pointer is not safely checked. |
| Classes | Issue | The `Game` class uses dynamic memory but does not provide proper copy handling for its raw pointers. |

## Overall Result

**Result: Issues Found**

All required categories were reviewed, and defects were identified in the source code.
