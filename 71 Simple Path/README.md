
# 71. Simplify Path

You are given an absolute path for a Unix-style file system, which always begins with a slash '/'. Your task is to transform this absolute path into its simplified canonical path.

The rules of a Unix-style file system are as follows:

    A single period '.' represents the current directory.
    A double period '..' represents the previous/parent directory.
    Multiple consecutive slashes such as '//' and '///' are treated as a single slash '/'.
    Any sequence of periods that does not match the rules above should be treated as a valid directory or file name. For example, '...' and '....' are valid directory or file names.

The simplified canonical path should follow these rules:

    The path must start with a single slash '/'.
    Directories within the path must be separated by exactly one slash '/'.
    The path must not end with a slash '/', unless it is the root directory.
    The path must not have any single or double periods ('.' and '..') used to denote current or parent directories.

Return the simplified canonical path.

## Answer

```python
class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []
        for gp in path.split('/'):
            if gp == '..':
                if stack:
                    stack.pop()
            elif not gp or gp == '.':
                continue
            else:
                stack.append(gp)

        return '/' + '/'.join(stack)
```

## Notes

Instead of iterating through the path (string), establish groups between the '/' by using str.split('/'). From there, perform stack manipulations listed in the problem description.

