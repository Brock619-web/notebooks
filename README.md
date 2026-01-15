# Map function
def mapper(A, B):
    return [((i, j), A[i][k] * B[k][j])
            for i in range(len(A))
            for j in range(len(B[0]))
            for k in range(len(B))]

# Reduce function
def reducer(pairs):
    result = {}
    for key, val in pairs:
        result[key] = result.get(key, 0) + val
    return result

# Convert to matrix
def to_matrix(res, r, c):
    M = [[0]*c for _ in range(r)]
    for (i,j), v in res.items():
        M[i][j] = v
    return M

# Example
A = [[1,2,3],[4,5,6]]
B = [[7,8],[9,10],[11,12]]

res = reducer(mapper(A, B))
print(to_matrix(res, len(A), len(B[0])))
