<p align="center">
  <img alt="logo" src="https://github.com/echemdb/astropy-pandas/raw/main/logo.png" width="300px">
</p>


# astropy-pandas

Heavily inspired by pint-pandas, we are trying to bring astropy units into pandas data frames. As of this writing this is just a proof-of-concept, a lot of work is needed to make this work properly.

Minimal example:

```py
>>> import astropy_pandas
>>> import pandas as pd
>>> df = pd.DataFrame({
...      'x': pd.Series([13.], dtype="astropy[parsec]"),
...      'y': pd.Series([37.], dtype="astropy[angstrom]")})
>>> (df['x'] * df['y']).astropy.to('km2')
0    1484.210916697348
dtype: astropy[km2]
```

## Roadmap to 1.0

* [ ] What can we learn from physipandas (MIT license)
* [ ] Make underlying data types explicit, `astropy[parsec][float64]` probably as in https://github.com/hgrecco/pint-pandas/pull/247/files
* [ ] Easy conversion to a unit-free data frame
* [ ] Implement (or test that default works) everything mentioned in https://pandas.pydata.org/docs/reference/api/pandas.api.extensions.ExtensionArray.html
* [ ] Show benchmarks (compare to data frames made from astropy quantities, compare to pint-pandas, compare to physipandas)
* [ ] Decide on a license. Probably we should use GPL3+ again. We'll heavily pull from pint-pandas which is BSD-3-clause but there should be no problem as long as we retain their copyright notice * [ ] Announce at https://stackoverflow.com/questions/39419178/how-can-i-manage-units-in-pandas-data
* [ ] Mention at https://pint.readthedocs.io/en/0.10.1/pint-pandas.html
* [ ] Mention at https://pandas.pydata.org/community/ecosystem.html
somewhere. However, maybe it's better to stick to BSD-3-Clause so pint-pandas can pull things back from us. Also pandas and astropy are both BSD-3-clause.

## Potential Limitations

* [ ] Plotly doesn't like these data frames: https://github.com/hgrecco/pint-pandas/issues/249
* [ ] `set_index` might not work: https://github.com/hgrecco/pint-pandas/issues/231 and https://github.com/hgrecco/pint-pandas/issues/44
* [ ] Problems when comparing data frames with different units
* [ ] `allclose` might not work, see https://github.com/hgrecco/pint-pandas/issues/108
* [ ] `apply` might not work on DataFrame, see https://github.com/hgrecco/pint-pandas/issues/55
