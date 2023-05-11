# Outlier Detection and Treatment with ODC

OilDataCleaner (ODC) is a Python module designed for detecting anomalies in time series data related to the oil industry. With its data cleaning techniques, ODC is an essential tool for anyone working with oil data. Whether you're a researcher, analyst, or engineer, ODC can help you identify unusual patterns and outliers in your data, enabling you to make more informed decisions.

## Installation
To use this module:

1. Clone or download this repository to your local machine.

2. Install the required packages by running the following command in your command prompt or terminal:

```bash
pip install -r requirements.txt
```
This will install all the necessary dependencies for using this module.

3. Import the necessary packages and the DetectOutliers class in your Python script:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from odc import DetectOutliers
```
4. Load your dataset using pandas and create an instance of the DetectOutliers class:

```python
df = pd.read_csv("F_14.csv", parse_dates=["DATEPRD"], index_col="DATEPRD")
clean = DetectOutliers(df)
```

5. Detect outliers in the desired variable:

```python
# Detecting outliers in the 'ON_STREAM_HRS' variable
ON_STREAM_HRS_outliers = clean.detect_outliers_in_time('ON_STREAM_HRS', 'BORE_OIL_VOL')
print("Outliers detected in ON_STREAM_HRS variable:\n", ON_STREAM_HRS_outliers)

```
Output:

    Outliers detected in ON_STREAM_HRS variable:
     DATEPRD
    2010-10-31    25.00000
    2012-09-15     0.95833
    2013-10-27    24.30833
    2014-10-26    25.00000
    Name: ON_STREAM_HRS, dtype: float64

6. Plot the outliers:

```python
clean.plot_outliers(ON_STREAM_HRS_outliers)
```
Output:

![test_4_0](https://user-images.githubusercontent.com/98224412/236640490-ae183998-86ec-4911-8df2-1c56d0892211.png)


7. Treat the outliers:

```python
df['ON_STREAM_HRS'] = clean.treat_outliers_in_time()
```
8. Check that the outliers were treated:

```python
outliers_after_treatment = clean.detect_outliers_in_time('ON_STREAM_HRS', 'BORE_OIL_VOL')
print("Outliers detected in ON_STREAM_HRS variable after treatment:\n", outliers_after_treatment)
```
Output:

    Outliers detected in ON_STREAM_HRS variable after treatment:
     No outliers detected.



For more examples of using this module, please refer to the `data_cleaning.ipynb` notebook in this repository.


## License

This project is licensed under the [MIT License](https://github.com/ashrafalaghbari/GA-TCN-LSTM/blob/main/license) - see the LICENSE file for details.


## Contributing

Contributions are always welcome!

See [contributing.md](https://github.com/ashrafalaghbari/GA-TCN-LSTM/blob/main/contributing.md) for ways to get started.

## Contact

If you have any questions or encounter any issues running `odc module`, please feel free to [open an issue](https://github.com/ashrafalaghbari/odc/issues) or contact me directly at [ashrafalaghbari@hotmail.com](mailto:ashrafalaghbari@hotmail.com). I'll be happy to help!



