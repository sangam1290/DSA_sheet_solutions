🚀 Stack Templates for NGR / NGL / NSR / NSL (Python)
🎯 Core Pattern

We traverse from one side and maintain a stack to find the first greater/smaller element on the other side in O(N).

def stack_problem(arr, reverse, compare):
    n = len(arr)
    stack = []       # holds candidates to compare
    res = []         # stores answers

    # Right → Left traversal for Right-side queries (NGR, NSR)
    # Left → Right traversal for Left-side queries (NGL, NSL)
    it = range(n-1, -1, -1) if reverse else range(n)

    for i in it:

        # Pop until we find a valid element based on condition
        while stack and compare(stack[-1], arr[i]):
            stack.pop()

        # If stack empty → No valid element found
        res.append(stack[-1] if stack else -1)

        # Push current element as a future candidate
        stack.append(arr[i])

    # reverse result when scanning from right
    if reverse:
        res.reverse()

    return res

arr = [4, 5, 2, 10, 8]

print("NGR:", NGR(arr))
print("NGL:", NGL(arr))
print("NSR:", NSR(arr))
print("NSL:", NSL(arr))

| Problem | Direction | Condition      | Common Use              |
| ------- | --------- | -------------- | ----------------------- |
| NGR     | Right     | next > current | Stock span, daily temps |
| NGL     | Left      | prev > current | Building visibility     |
| NSR     | Right     | next < current | Histogram area          |
| NSL     | Left      | prev < current | Span calculations       |

