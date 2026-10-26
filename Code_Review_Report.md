# Code Review Report

## Static Code Verification

| Line Number | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
|---:|---|---|---|---|
| 41 | Array Boundary | The array is accessed without checking whether it is full. | Check `monsterCount < MAX_MONSTERS` before adding a monster. | High |
| 47 | Assignment Instead of Comparison | `=` assigns the ID instead of comparing it, causing incorrect monster identification. | Replace `=` with `==`. | High |
| 54–56 | Null Pointer | `findMonster()` can return `nullptr`, but the pointer is used without checking. | Check `m == nullptr` before using `m`. | High |
| 55 | Type / Arithmetic Issue | Converting `damage` to `unsigned int` can cause unexpected results for negative values. | Validate the value and use a suitable numeric type. | Medium |
| 64 | Loop Boundary Error | `i <= monsterCount` can access one position outside the valid range. | Change `<=` to `<`. | High |
| 72–73 | Dangling Reference | A reference to the local `label` variable is returned after it goes out of scope. | Return `std::string` by value. | High |
| 77 | Uninitialized Variable | `sum` is used before being initialized. | Use `double sum = 0.0;`. | Medium |
| 80 | Division by Zero | If `monsterCount` is zero, the average calculation divides by zero. | Check `monsterCount > 0` before division. | Medium |
| 85–86 | Use After Delete | The monster is deleted and then its name is accessed. | Print the name before `delete m`. | High |
| 95–98 | Missing Return | No value is returned when `score <= 100`. | Add a return statement for this condition. | Medium |
| 102–105 | Buffer Overflow Risk | The 10-character buffer may not be large enough for the entered name. | Use `std::string` or safely limit input. | High |
| 109 | Incorrect Memory Deallocation | Memory allocated with `new[]` is released using `delete`. | Use `delete[] name` or use `std::string`. | High |
| 119 | Array Capacity Violation | Six monsters are added although the maximum is 5. | Increase capacity or prevent additional monsters. | High |
| 121 | Memory Leak | `bonus` is dynamically allocated but never deleted. | Delete it when it is no longer needed. | Medium |
| 123 | Invalid Function Input | Monster ID `99` does not exist, which can lead to a null-pointer problem. | Check whether the monster exists before attacking. | High |
| 133 | Shallow Copy / Double Delete Risk | Copying `Game` copies raw pointers, so both objects may delete the same monsters. | Implement proper copy handling or prevent copying. | High |

## Overall Review Result

The code contains issues related to memory management, pointers, arrays, loops, arithmetic, control flow, function calls, and class design.
