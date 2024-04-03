## Step 1:

Create a matrix:

```
static std::unordered_map<int, std::unordered_map<int, double>> Generate_nodal_matrix(const std::vector<Element>& elements) 
{
    int _matrixSize = 0;
    std::unordered_map<int, std::unordered_map<int, double>> _nodal_matrix;

    for (const auto& element : elements) 
    {
        if (element.node1 > _matrixSize)
            _matrixSize = element.node2;
    }

    for (int i = 0; i <= _matrixSize; i++) {
        _nodal_matrix[i] = {};
        for (int j = 0; j <= _matrixSize; j++) {
            _nodal_matrix[i][j] = 0.0;
        }
    }

    for (const auto& element : elements)
    {
        _nodal_matrix[element.node1][element.node1] += element.value;
        _nodal_matrix[element.node2][element.node2] += element.value;
        _nodal_matrix[element.node1][element.node2] -= element.value;
        _nodal_matrix[element.node2][element.node1] -= element.value;
    }

    return _nodal_matrix;
}
```
