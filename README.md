GOTO: [Base-Projects](https://github.com/DamianKJKujawski/Base-Projects) [Ideas-Projects](https://github.com/DamianKJKujawski/Ideas-Projects) [MicroOS](https://github.com/DamianKJKujawski/MicroOS) [Electronics](https://github.com/DamianKJKujawski/Electronics) [Design Patterns](https://github.com/DamianKJKujawski/DesignPatterns) [MulticorePLCUnit](https://github.com/DamianKJKujawski/MulticorePLCUnit) [PCB Design](https://github.com/DamianKJKujawski/PCB) [Antennas](https://github.com/DamianKJKujawski/Antennas)

## My Circuits Projects:

### Energy Harvester:

![EnergyHarvester](https://github.com/DamianKJKujawski/Electronics/assets/160174331/aa29518a-8e5e-439b-899c-26476b152e70)

### Measuring Key:

![MeasuringKey](https://github.com/DamianKJKujawski/Electronics/assets/160174331/4978b6a8-224e-4489-80c5-559ec65f97e9)

### RMS-DC:

![RMS-DC](https://github.com/DamianKJKujawski/Electronics/assets/160174331/c0625742-801d-42d7-80d7-0df6dd739875)

### Input Voltage Averaging:

![VoltageAveraging](https://github.com/DamianKJKujawski/Electronics/assets/160174331/552a2721-1150-4b00-b61a-6610dc3066ee)

### Power Supply:

![PowerSupply](https://github.com/DamianKJKujawski/Electronics/assets/160174331/da543c2d-a200-40cf-9839-0b0436748f29)

### Rogowski based Harvester:

![Rogowski](https://github.com/DamianKJKujawski/Electronics/assets/160174331/8c22512a-cfa2-4a7e-9bac-cfe5aa433dfb)

### Integrator:

![Integrator](https://github.com/DamianKJKujawski/Electronics/assets/160174331/9ed7bf47-b429-4078-994c-abbf4b02e418)
![image](https://github.com/DamianKJKujawski/Electronics/assets/160174331/5e479710-9908-405c-a618-61153919bc3e)

## Matrix Based Computations:

### Step 1:

Create a matrix:

![image](https://github.com/DamianKJKujawski/Electronics/assets/160174331/5878106e-fe2b-4291-a94b-4be1e37d0e6b)

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

// TODO:

![image](https://github.com/DamianKJKujawski/Electronics/assets/160174331/ab041ef9-1881-44cb-9b89-021ac249767e)
