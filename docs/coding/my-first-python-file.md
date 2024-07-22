# Pandas Styler Crash Course

Pandas Styler provides a way to style a pandas DataFrame to make it more visually appealing. Below is an example code that demonstrates key functionalities.

```python
import pandas as pd
import numpy as np
```

# Creating a sample DataFrame

```Python
data = {
    'A': [1, 2, np.nan, 4],
    'B': [5, np.nan, 7, 8],
    'C': [9, 10, 11, np.nan]
}
df = pd.DataFrame(data)
```


# Basic Usage

```python
styled_df = df.style
```
# Highlight Null Values

```python
styled_df = styled_df.highlight_null(null_color='red')
```
# Highlight Maximum and Minimum Values

```python
styled_df = styled_df.highlight_max(color='lightgreen').highlight_min(color='lightcoral')
```
# Format Numbers to Two Decimal Places

```python
styled_df = styled_df.format("{:.2f}")
```
# Conditional Formatting to Color Negative Numbers Red

```python
def color_negative_red(val):
    color = 'red' if val < 0 else 'black'
    return f'color: {color}'


styled_df = styled_df.applymap(color_negative_red)
```
# Add Bar Charts to Compare Values Visually

```python
styled_df = styled_df.bar(subset=['A', 'B'], color='lightblue')
```

# Customize Header Styles

```python
styled_df = styled_df.set_table_styles({
    'header': [{'selector': 'th', 'props': [('background-color', 'lightblue')]}]
})
```
# Add Custom CSS Styles

```python
styled_df = styled_df.set_table_styles([{
    'selector': 'tr:hover',
    'props': [('background-color', 'lightyellow')]
}, {
    'selector': 'th.col_heading',
    'props': [('background-color', 'lightgrey')]
}])
```
# Export the Styled DataFrame to an Excel File with Styles

```python
styled_df.to_excel('styled.xlsx', engine='openpyxl')
```
# Display the Styled DataFrame in Jupyter Notebooks

```python
styled_df.render()
```



