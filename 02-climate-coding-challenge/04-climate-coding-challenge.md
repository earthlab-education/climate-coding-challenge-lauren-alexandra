# Part 4: Plot your results

First things first – make sure to load the climate `DataFrame` you
stored in the previous notebooks using Jupyter cell magic:

You’ll also need some libraries later on. This is an extension to
`pandas` that will allow you to easily make beautiful, interactive
plots, and a related library that will let you save your plots:

## Plot the precipitation column (PRCP) vs time to explore the data

Plotting in Python is easy, but not quite this easy:




    <Axes: xlabel='DATE'>




    
![png](04-climate-coding-challenge_files/04-climate-coding-challenge_5_1.png)
    


Looks like we have *both* precipitation and temperature on the same
plot, and it’s hard to see what it is because it’s missing labels!

> ****Label your plot****
>
> <figure>
> <img src="https://imgs.xkcd.com/comics/convincing.png"
> alt="Source: https://xkcd.com/833" />
> <figcaption aria-hidden="true">Source: https://xkcd.com/833</figcaption>
> </figure>
>
> Make sure each plot has:
>
> -   A title that explains where and when the data are from
> -   x- and y- axis labels with **units** where appropriate
> -   A legend where appropriate

When plotting in Python, you’ll always need to add some instructions on
labels and how you want your plot to look.

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Plot your data</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Change <code>dataframe</code> to <strong>your</strong>
<code>DataFrame</code> name.</li>
<li>Change <code>y=</code> to the name of your <strong>observed
temperature</strong> column name.</li>
<li>Use the <code>title</code>, <code>ylabel</code>, and
<code>xlabel</code> parameters to add key text to your plot.</li>
<li>Adjust the size of your figure using <code>figsize=(x,y)</code>
where <code>x</code> is figure width and <code>y</code> is figure
height</li>
</ol>
<blockquote>
<p><strong>HINT:</strong> labels have to be a <em>type</em> in Python
called a <strong>string</strong>. You can make a string by putting
quotes around your label, just like the column names in the sample code
(eg <code>y='TOBS'</code>).</p>
</blockquote></div></div>




    <Axes: title={'center': 'Daily Precipitation (1893-2023)'}, xlabel='Date', ylabel='Inches'>




    
![png](04-climate-coding-challenge_files/04-climate-coding-challenge_7_1.png)
    


<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-extra"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Looking for an Extra Challenge?</div></div><div class="callout-body-container callout-body"><p>There are many other things you can do to customize your plot. Take a
look at the <a
href="https://pandas.pydata.org/docs/user_guide/visualization.html">pandas
plotting galleries</a> and the <a
href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.plot.html">documentation
of plot</a> to see if there’s other changes you want to make to your
plot. Some possibilities include:</p>
<ul>
<li>Remove the legend since there’s only one data series</li>
<li>Increase the figure size</li>
<li>Increase the font size</li>
<li>Change the colors</li>
<li>Use a bar graph instead (usually we use lines for time series, but
since this is annual it could go either way)</li>
<li>Add a trend line</li>
</ul>
<p>Not sure how to do any of these? Try searching the internet, or
asking an AI!</p></div></div>

## Clean up time series plots by resampling

You may notice that your plot looks a little “fuzzy”. This happens when
Python is trying to plot a value for every date, but the resolution of
the image is too low to actually do that. You can address this issue by
**resampling** the data, or summarizing it over a time period of your
choice. In this case, we will resample annually, giving us one data
point per year.

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Resample</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Set the frequency of your final data by replacing
<code>DT_OFFSET</code>with a <strong>Datetime Offset Code</strong>.
Check out the table in the <a
href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html#dateoffset-objects">pandas
datetime documentation</a> to find the one you want (we recommend the
start of the year).</li>
<li>Choose how to summarize each year of data by replacing
<code>agg_method_here</code> with a method that will calculate the
<strong>average annual value</strong>. Check out the <a
href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html#basics">pandas
resampling documentation</a> for a list of common built-in options.</li>
</ol></div></div>




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PRCP</th>
      <th>TOBS</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1893-01-01</th>
      <td>0.025543</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1894-01-01</th>
      <td>0.058841</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1895-01-01</th>
      <td>0.117090</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1896-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1897-01-01</th>
      <td>0.068922</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2019-01-01</th>
      <td>0.057644</td>
      <td>54.426997</td>
    </tr>
    <tr>
      <th>2020-01-01</th>
      <td>0.046721</td>
      <td>57.691460</td>
    </tr>
    <tr>
      <th>2021-01-01</th>
      <td>0.056658</td>
      <td>57.538462</td>
    </tr>
    <tr>
      <th>2022-01-01</th>
      <td>0.051479</td>
      <td>56.139726</td>
    </tr>
    <tr>
      <th>2023-01-01</th>
      <td>0.076740</td>
      <td>58.996337</td>
    </tr>
  </tbody>
</table>
<p>131 rows × 2 columns</p>
</div>



<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Plot Annual Data</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Try plotting your new DataFrame in the cell below. Can you see what
is going on more clearly now? Don’t forget to adjust your labels!</li>
</ol></div></div>




    <Axes: title={'center': 'Annual Average Precipitation (1893-2023)'}, xlabel='Year', ylabel='Inches'>




    
![png](04-climate-coding-challenge_files/04-climate-coding-challenge_11_1.png)
    


<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-respond"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Reflect and Respond: Interpret your plot</div></div><div class="callout-body-container callout-body"><ol type="1">
<li><p>Create a new Markdown cell below this one.</p></li>
<li><p>In the new cell, answer the following questions using a
<strong>bulleted list</strong> in Markdown – what are 2 things you
notice about this data? What physical phenomena or data anomaly could be
causing each one?</p></li>
</ol>
<div data-__quarto_custom="true"
data-__quarto_custom_type="ConditionalBlock"
data-__quarto_custom_context="Block" data-__quarto_custom_id="6">
<div data-__quarto_custom_scaffold="true">
<div>

</div>
</div>
</div></div></div>

- The data does not reach 0.00 inches. This is due to taking the average across all values in a given year.
- There are two outliers above 0.10 inches prior to 1930 which may indicate extreme weather patterns or recording error.

## Check specific values with an interactive plot

You can use the `.hvplot()` method with similar arguments to create an
interactive plot.

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Interactive Plot</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Copy your plotting code into the cell below.</li>
<li>Replace <code>.plot</code> in your code with
<code>.hvplot</code></li>
</ol>
<p>Now, you should be able to hover over data points and see their
values!</p></div></div>

    WARNING:param.main: hvPlot does not have the concept of a figure, and the figsize keyword will be ignored. The size of each subplot in a layout is set individually using the width and height options.
    /opt/conda/lib/python3.10/site-packages/holoviews/core/data/pandas.py:39: FutureWarning: Series.__getitem__ treating keys as positions is deprecated. In a future version, integer keys will always be treated as labels (consistent with DataFrame behavior). To access a value by position, use `ser.iloc[pos]`
      return dataset.data.dtypes[idx].type
    /opt/conda/lib/python3.10/site-packages/holoviews/core/data/pandas.py:39: FutureWarning: Series.__getitem__ treating keys as positions is deprecated. In a future version, integer keys will always be treated as labels (consistent with DataFrame behavior). To access a value by position, use `ser.iloc[pos]`
      return dataset.data.dtypes[idx].type







<div id='p1481'>
  <div id="f4fb69f4-11a2-41dc-adf0-eaee4cd70605" data-root-id="p1481" style="display: contents;"></div>
</div>
<script type="application/javascript">(function(root) {
  var docs_json = {"f6ab0e9e-b13e-42f1-a890-21b9e0972b37":{"version":"3.2.2","title":"Bokeh Application","roots":[{"type":"object","name":"Row","id":"p1481","attributes":{"name":"Row01314","tags":["embedded"],"stylesheets":["\n:host(.pn-loading.pn-arc):before, .pn-loading.pn-arc:before {\n  background-image: url(\"data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHN0eWxlPSJtYXJnaW46IGF1dG87IGJhY2tncm91bmQ6IG5vbmU7IGRpc3BsYXk6IGJsb2NrOyBzaGFwZS1yZW5kZXJpbmc6IGF1dG87IiB2aWV3Qm94PSIwIDAgMTAwIDEwMCIgcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQiPiAgPGNpcmNsZSBjeD0iNTAiIGN5PSI1MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjYzNjM2MzIiBzdHJva2Utd2lkdGg9IjEwIiByPSIzNSIgc3Ryb2tlLWRhc2hhcnJheT0iMTY0LjkzMzYxNDMxMzQ2NDE1IDU2Ljk3Nzg3MTQzNzgyMTM4Ij4gICAgPGFuaW1hdGVUcmFuc2Zvcm0gYXR0cmlidXRlTmFtZT0idHJhbnNmb3JtIiB0eXBlPSJyb3RhdGUiIHJlcGVhdENvdW50PSJpbmRlZmluaXRlIiBkdXI9IjFzIiB2YWx1ZXM9IjAgNTAgNTA7MzYwIDUwIDUwIiBrZXlUaW1lcz0iMDsxIj48L2FuaW1hdGVUcmFuc2Zvcm0+ICA8L2NpcmNsZT48L3N2Zz4=\");\n  background-size: auto calc(min(50%, 400px));\n}",{"type":"object","name":"ImportedStyleSheet","id":"p1484","attributes":{"url":"https://cdn.holoviz.org/panel/1.2.1/dist/css/loading.css"}},{"type":"object","name":"ImportedStyleSheet","id":"p1548","attributes":{"url":"https://cdn.holoviz.org/panel/1.2.1/dist/css/listpanel.css"}},{"type":"object","name":"ImportedStyleSheet","id":"p1482","attributes":{"url":"https://cdn.holoviz.org/panel/1.2.1/dist/bundled/theme/default.css"}},{"type":"object","name":"ImportedStyleSheet","id":"p1483","attributes":{"url":"https://cdn.holoviz.org/panel/1.2.1/dist/bundled/theme/native.css"}}],"min_width":700,"margin":0,"sizing_mode":"stretch_width","align":"start","children":[{"type":"object","name":"Spacer","id":"p1485","attributes":{"name":"HSpacer01325","stylesheets":["\n:host(.pn-loading.pn-arc):before, .pn-loading.pn-arc:before {\n  background-image: url(\"data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHN0eWxlPSJtYXJnaW46IGF1dG87IGJhY2tncm91bmQ6IG5vbmU7IGRpc3BsYXk6IGJsb2NrOyBzaGFwZS1yZW5kZXJpbmc6IGF1dG87IiB2aWV3Qm94PSIwIDAgMTAwIDEwMCIgcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQiPiAgPGNpcmNsZSBjeD0iNTAiIGN5PSI1MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjYzNjM2MzIiBzdHJva2Utd2lkdGg9IjEwIiByPSIzNSIgc3Ryb2tlLWRhc2hhcnJheT0iMTY0LjkzMzYxNDMxMzQ2NDE1IDU2Ljk3Nzg3MTQzNzgyMTM4Ij4gICAgPGFuaW1hdGVUcmFuc2Zvcm0gYXR0cmlidXRlTmFtZT0idHJhbnNmb3JtIiB0eXBlPSJyb3RhdGUiIHJlcGVhdENvdW50PSJpbmRlZmluaXRlIiBkdXI9IjFzIiB2YWx1ZXM9IjAgNTAgNTA7MzYwIDUwIDUwIiBrZXlUaW1lcz0iMDsxIj48L2FuaW1hdGVUcmFuc2Zvcm0+ICA8L2NpcmNsZT48L3N2Zz4=\");\n  background-size: auto calc(min(50%, 400px));\n}",{"id":"p1484"},{"id":"p1482"},{"id":"p1483"}],"margin":0,"sizing_mode":"stretch_width","align":"start"}},{"type":"object","name":"Figure","id":"p1493","attributes":{"width":700,"height":300,"margin":[5,10],"sizing_mode":"fixed","align":"start","x_range":{"type":"object","name":"Range1d","id":"p1486","attributes":{"tags":[[["DATE","DATE",null]],[]],"start":-2429827200000.0,"end":1672531200000.0,"reset_start":-2429827200000.0,"reset_end":1672531200000.0}},"y_range":{"type":"object","name":"Range1d","id":"p1487","attributes":{"tags":[[["PRCP","PRCP",null]],{"type":"map","entries":[["invert_yaxis",false],["autorange",false]]}],"start":0.014166007905138342,"end":0.15069565217391304,"reset_start":0.014166007905138342,"reset_end":0.15069565217391304}},"x_scale":{"type":"object","name":"LinearScale","id":"p1503"},"y_scale":{"type":"object","name":"LinearScale","id":"p1504"},"title":{"type":"object","name":"Title","id":"p1496","attributes":{"text":"Annual Average Precipitation (1893-2023)","text_color":"black","text_font_size":"12pt"}},"renderers":[{"type":"object","name":"GlyphRenderer","id":"p1541","attributes":{"data_source":{"type":"object","name":"ColumnDataSource","id":"p1532","attributes":{"selected":{"type":"object","name":"Selection","id":"p1533","attributes":{"indices":[],"line_indices":[]}},"selection_policy":{"type":"object","name":"UnionRenderers","id":"p1534"},"data":{"type":"map","entries":[["DATE",{"type":"ndarray","array":{"type":"bytes","data":"AACg5eetgcIAAEBcKnOBwgAA4NJsOIHCAACASa/9gMIAAECNyMKAwgAA4AMLiIDCAACAek1NgMIAACDxjxKAwgAAgM+kr3/CAADAvCk6f8IAAACqrsR+wgAAQJczT37CAADAHmbZfcIAAAAM62N9wgAAQPlv7nzCAACA5vR4fMIAAABuJwN8wgAAQFusjXvCAACASDEYe8IAAMA1tqJ6wgAAQL3oLHrCAACAqm23ecIAAMCX8kF5wgAAAIV3zHjCAACADKpWeMIAAMD5LuF3wgAAAOeza3fCAABA1Dj2dsIAAMBba4B2wgAAAEnwCnbCAABANnWVdcIAAIAj+h91wgAAAKssqnTCAABAmLE0dMIAAICFNr9zwgAAwHK7SXPCAABA+u3TcsIAAIDncl5ywgAAwNT36HHCAAAAwnxzccIAAIBJr/1wwgAAwDY0iHDCAAAAJLkScMIAAIAifDpvwgAAgDHhTm7CAAAADOtjbcIAAIDm9HhswgAAAMH+jWvCAAAA0GOiasIAAICqbbdpwgAAAIV3zGjCAACAX4HhZ8IAAIBu5vVmwgAAAEnwCmbCAACAI/ofZcIAAAD+AzVkwgAAAA1pSWPCAACA53JeYsIAAADCfHNhwgAAgJyGiGDCAAAAV9c5X8IAAAAM62NdwgAAAMH+jVvCAAAAdhK4WcIAAACU3OBXwgAAAEnwClbCAAAA/gM1VMIAAACzF19SwgAAANHhh1DCAAAADOtjTcIAAAB2ErhJwgAAAOA5DEbCAAAAHM5dQsIAAAAM62M9wgAAAOA5DDbCAAAAaBFpLcIAAACwxF4dwgAAAAAAAAAAAAAAsMReHUIAAACwxF4tQgAAAOA5DDZCAAAADOtjPUIAAAAczl1CQgAAALKmCUZCAAAAdhK4SUIAAAAM62NNQgAAANHhh1BCAAAAHM5dUkIAAAD+AzVUQgAAAEnwClZCAAAAlNzgV0IAAADfyLZZQgAAAMH+jVtCAAAADOtjXUIAAABX1zlfQgAAANHhh2BCAAAAwnxzYUIAAIDncl5iQgAAAA1pSWNCAACAMl80ZEIAAIAj+h9lQgAAAEnwCmZCAACAbub1ZkIAAACU3OBnQgAAAIV3zGhCAACAqm23aUIAAADQY6JqQgAAgPVZjWtCAACA5vR4bEIAAAAM62NtQgAAgDHhTm5CAAAAV9c5b0IAAAAkuRJwQgAAwDY0iHBCAACASa/9cEIAAEBcKnNxQgAAwNT36HFCAACA53JeckIAAED67dNyQgAAAA1pSXNCAACAhTa/c0IAAECYsTR0QgAAAKssqnRCAADAvacfdUIAAEA2dZV1QgAAAEnwCnZCAADAW2uAdkIAAIBu5vV2QgAAAOeza3dCAADA+S7hd0IAAIAMqlZ4Qg=="},"shape":[131],"dtype":"float64","order":"little"}],["PRCP",{"type":"ndarray","array":{"type":"bytes","data":"o60GzxEomj8hfgfidyCuPwynkbWU+b0/AAAAAAAA+H/95zM55qSxP2vYBhxlfKY/oibzgcixoz9mM/jdOLGnP6YDJtGNbaM/lrxmStTdqT+EGkBh8aqoP45f7gMML6w/HJ2jBCbgrj8ENxerbtS0P/29r49HJag/WBmElUFYqT+MUFVzXXmyP+Ai8/DsOp8/iPFTKUJnpD92WoypP0m1PzEyh+nMGKw/cHL9/lO2qT/hYC3w7SKyP2s5uj0iq7E/HL+UAtSfoz/XkSaXasyrP0ln96MX/a4/HMVtFr9nsD/V2VKdLdXBP8sEOxooZ7E/Y/Buh/cEtj8mz7ZjNkyiP+jT4JCvkao/Gtd9zqQQqz8I08Y97kSrP2s/6WDkN64/nmu0jSHErT86v69qwMinP6emnQ0NBKQ/GrG9frmToD8VFRUVFRWlP6ry5waR5aQ/s4+mY6APpz+e53me53muP7c0taHM2qU/rR9+yaAgtz8zxiCDK0qhP1NaQjNGBq4/xs8qwmvTsD95q6BNnWWyP35hKbnYF6Y/kfnsK/EWqj8R0QYRbRCxP3aBIuT0Dqs/LwH9cB7Rsj9YGYSVQVipP55rtI0hxK0/4+sIGuDcoz+iCmH5ezmzP0le9QHD/ac/NeKtgjZ1pj9w16AZh9yePzVXczVXc6U/usKYalHPqT+9hQ1GEz2zP1wh/3J5C6s/3nMGkg9xqj/bIHSo7UClP9euiJhHaK8/XhRieLnpoT8GFgOqxManPx18ao+jC6A/V0TMI7RPqz97bsazmDmfP3lzfDwEdbE/eL36Yfelpj+1rxUfPE2zP+OozK0JW6c/MsI+x5o3qj8LikPXJ8ipPxLap01wWaw/z5oKjgUypT+AHu1MApapPypNA9sKgqQ/47PkCEfsoj9lHwCi8gWxP7JJ5ldoDKo/zGdfibfQoj+bKVF3Z7inP1j+dLQvKrA/cTa7fPSOsT/OQZiBjO+pPySmBle6dqg/+qt2ctDyrT/Vz9Cp/xuyP3MnoUAjtqc/ZH2zO9f+rT8EsGtcSomrPxkEVg4tsq0/JmpJICFQqD9XrXsxV+6vP1pkO99Pjac/LpxtOS2ktD8mBdzcC1SuP0YCwyVm+7M/y9/LmV5Erz9sVgCfiTOyP50wcGn9PKY/FDI7GqWHqT/1dCu3U3ijP/njmoNp464/aqbeKxABsz/vr629i2+oP6uSBFk/Fqs/84zgDFErqD/XbUvENM+nP9XHK+pbS60/HalkTFl9rD/L38uZXkSvPwLD/deU5KU/1Bhv6Kfztz+VtgR4AoiwP5NC3yKB4bI/tHmf4pIhqD+W/riZO4yvPwuw+YyzAKs/vcOTKX6DrT+UUKAR2+unP/pzUmE3Aq0/PZH7xYNbqj9TOqVTOqWzPw=="},"shape":[131],"dtype":"float64","order":"little"}]]}}},"view":{"type":"object","name":"CDSView","id":"p1542","attributes":{"filter":{"type":"object","name":"AllIndices","id":"p1543"}}},"glyph":{"type":"object","name":"Line","id":"p1538","attributes":{"tags":["apply_ranges"],"x":{"type":"field","field":"DATE"},"y":{"type":"field","field":"PRCP"},"line_color":"DarkBlue","line_width":2}},"selection_glyph":{"type":"object","name":"Line","id":"p1544","attributes":{"tags":["apply_ranges"],"x":{"type":"field","field":"DATE"},"y":{"type":"field","field":"PRCP"},"line_color":"DarkBlue","line_width":2}},"nonselection_glyph":{"type":"object","name":"Line","id":"p1539","attributes":{"tags":["apply_ranges"],"x":{"type":"field","field":"DATE"},"y":{"type":"field","field":"PRCP"},"line_color":"DarkBlue","line_alpha":0.1,"line_width":2}},"muted_glyph":{"type":"object","name":"Line","id":"p1540","attributes":{"tags":["apply_ranges"],"x":{"type":"field","field":"DATE"},"y":{"type":"field","field":"PRCP"},"line_color":"DarkBlue","line_alpha":0.2,"line_width":2}}}}],"toolbar":{"type":"object","name":"Toolbar","id":"p1502","attributes":{"tools":[{"type":"object","name":"WheelZoomTool","id":"p1491","attributes":{"tags":["hv_created"],"zoom_together":"none"}},{"type":"object","name":"HoverTool","id":"p1492","attributes":{"tags":["hv_created"],"renderers":[{"id":"p1541"}],"tooltips":[["DATE","@{DATE}{%F %T}"],["PRCP","@{PRCP}"]],"formatters":{"type":"map","entries":[["@{DATE}","datetime"]]}}},{"type":"object","name":"SaveTool","id":"p1527"},{"type":"object","name":"PanTool","id":"p1528"},{"type":"object","name":"BoxZoomTool","id":"p1529","attributes":{"overlay":{"type":"object","name":"BoxAnnotation","id":"p1530","attributes":{"syncable":false,"level":"overlay","visible":false,"left_units":"canvas","right_units":"canvas","bottom_units":"canvas","top_units":"canvas","line_color":"black","line_alpha":1.0,"line_width":2,"line_dash":[4,4],"fill_color":"lightgrey","fill_alpha":0.5}}}},{"type":"object","name":"ResetTool","id":"p1531"}],"active_drag":{"id":"p1528"},"active_scroll":{"id":"p1491"}}},"left":[{"type":"object","name":"LinearAxis","id":"p1522","attributes":{"ticker":{"type":"object","name":"BasicTicker","id":"p1523","attributes":{"mantissas":[1,2,5]}},"formatter":{"type":"object","name":"BasicTickFormatter","id":"p1524"},"axis_label":"Inches","major_label_policy":{"type":"object","name":"AllLabels","id":"p1525"}}}],"below":[{"type":"object","name":"DatetimeAxis","id":"p1505","attributes":{"ticker":{"type":"object","name":"DatetimeTicker","id":"p1506","attributes":{"num_minor_ticks":5,"tickers":[{"type":"object","name":"AdaptiveTicker","id":"p1507","attributes":{"num_minor_ticks":0,"mantissas":[1,2,5],"max_interval":500.0}},{"type":"object","name":"AdaptiveTicker","id":"p1508","attributes":{"num_minor_ticks":0,"base":60,"mantissas":[1,2,5,10,15,20,30],"min_interval":1000.0,"max_interval":1800000.0}},{"type":"object","name":"AdaptiveTicker","id":"p1509","attributes":{"num_minor_ticks":0,"base":24,"mantissas":[1,2,4,6,8,12],"min_interval":3600000.0,"max_interval":43200000.0}},{"type":"object","name":"DaysTicker","id":"p1510","attributes":{"days":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]}},{"type":"object","name":"DaysTicker","id":"p1511","attributes":{"days":[1,4,7,10,13,16,19,22,25,28]}},{"type":"object","name":"DaysTicker","id":"p1512","attributes":{"days":[1,8,15,22]}},{"type":"object","name":"DaysTicker","id":"p1513","attributes":{"days":[1,15]}},{"type":"object","name":"MonthsTicker","id":"p1514","attributes":{"months":[0,1,2,3,4,5,6,7,8,9,10,11]}},{"type":"object","name":"MonthsTicker","id":"p1515","attributes":{"months":[0,2,4,6,8,10]}},{"type":"object","name":"MonthsTicker","id":"p1516","attributes":{"months":[0,4,8]}},{"type":"object","name":"MonthsTicker","id":"p1517","attributes":{"months":[0,6]}},{"type":"object","name":"YearsTicker","id":"p1518"}]}},"formatter":{"type":"object","name":"DatetimeTickFormatter","id":"p1519"},"axis_label":"Year","major_label_policy":{"type":"object","name":"AllLabels","id":"p1520"}}}],"center":[{"type":"object","name":"Grid","id":"p1521","attributes":{"axis":{"id":"p1505"},"grid_line_color":null}},{"type":"object","name":"Grid","id":"p1526","attributes":{"dimension":1,"axis":{"id":"p1522"},"grid_line_color":null}}],"min_border_top":10,"min_border_bottom":10,"min_border_left":10,"min_border_right":10,"output_backend":"webgl"}},{"type":"object","name":"Spacer","id":"p1546","attributes":{"name":"HSpacer01328","stylesheets":["\n:host(.pn-loading.pn-arc):before, .pn-loading.pn-arc:before {\n  background-image: url(\"data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHN0eWxlPSJtYXJnaW46IGF1dG87IGJhY2tncm91bmQ6IG5vbmU7IGRpc3BsYXk6IGJsb2NrOyBzaGFwZS1yZW5kZXJpbmc6IGF1dG87IiB2aWV3Qm94PSIwIDAgMTAwIDEwMCIgcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQiPiAgPGNpcmNsZSBjeD0iNTAiIGN5PSI1MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjYzNjM2MzIiBzdHJva2Utd2lkdGg9IjEwIiByPSIzNSIgc3Ryb2tlLWRhc2hhcnJheT0iMTY0LjkzMzYxNDMxMzQ2NDE1IDU2Ljk3Nzg3MTQzNzgyMTM4Ij4gICAgPGFuaW1hdGVUcmFuc2Zvcm0gYXR0cmlidXRlTmFtZT0idHJhbnNmb3JtIiB0eXBlPSJyb3RhdGUiIHJlcGVhdENvdW50PSJpbmRlZmluaXRlIiBkdXI9IjFzIiB2YWx1ZXM9IjAgNTAgNTA7MzYwIDUwIDUwIiBrZXlUaW1lcz0iMDsxIj48L2FuaW1hdGVUcmFuc2Zvcm0+ICA8L2NpcmNsZT48L3N2Zz4=\");\n  background-size: auto calc(min(50%, 400px));\n}",{"id":"p1484"},{"id":"p1482"},{"id":"p1483"}],"margin":0,"sizing_mode":"stretch_width","align":"start"}}]}}],"defs":[{"type":"model","name":"ReactiveHTML1"},{"type":"model","name":"FlexBox1","properties":[{"name":"align_content","kind":"Any","default":"flex-start"},{"name":"align_items","kind":"Any","default":"flex-start"},{"name":"flex_direction","kind":"Any","default":"row"},{"name":"flex_wrap","kind":"Any","default":"wrap"},{"name":"justify_content","kind":"Any","default":"flex-start"}]},{"type":"model","name":"FloatPanel1","properties":[{"name":"config","kind":"Any","default":{"type":"map"}},{"name":"contained","kind":"Any","default":true},{"name":"position","kind":"Any","default":"right-top"},{"name":"offsetx","kind":"Any","default":null},{"name":"offsety","kind":"Any","default":null},{"name":"theme","kind":"Any","default":"primary"},{"name":"status","kind":"Any","default":"normalized"}]},{"type":"model","name":"GridStack1","properties":[{"name":"mode","kind":"Any","default":"warn"},{"name":"ncols","kind":"Any","default":null},{"name":"nrows","kind":"Any","default":null},{"name":"allow_resize","kind":"Any","default":true},{"name":"allow_drag","kind":"Any","default":true},{"name":"state","kind":"Any","default":[]}]},{"type":"model","name":"drag1","properties":[{"name":"slider_width","kind":"Any","default":5},{"name":"slider_color","kind":"Any","default":"black"},{"name":"value","kind":"Any","default":50}]},{"type":"model","name":"click1","properties":[{"name":"terminal_output","kind":"Any","default":""},{"name":"debug_name","kind":"Any","default":""},{"name":"clears","kind":"Any","default":0}]},{"type":"model","name":"FastWrapper1","properties":[{"name":"object","kind":"Any","default":null},{"name":"style","kind":"Any","default":null}]},{"type":"model","name":"NotificationAreaBase1","properties":[{"name":"js_events","kind":"Any","default":{"type":"map"}},{"name":"position","kind":"Any","default":"bottom-right"},{"name":"_clear","kind":"Any","default":0}]},{"type":"model","name":"NotificationArea1","properties":[{"name":"js_events","kind":"Any","default":{"type":"map"}},{"name":"notifications","kind":"Any","default":[]},{"name":"position","kind":"Any","default":"bottom-right"},{"name":"_clear","kind":"Any","default":0},{"name":"types","kind":"Any","default":[{"type":"map","entries":[["type","warning"],["background","#ffc107"],["icon",{"type":"map","entries":[["className","fas fa-exclamation-triangle"],["tagName","i"],["color","white"]]}]]},{"type":"map","entries":[["type","info"],["background","#007bff"],["icon",{"type":"map","entries":[["className","fas fa-info-circle"],["tagName","i"],["color","white"]]}]]}]}]},{"type":"model","name":"Notification","properties":[{"name":"background","kind":"Any","default":null},{"name":"duration","kind":"Any","default":3000},{"name":"icon","kind":"Any","default":null},{"name":"message","kind":"Any","default":""},{"name":"notification_type","kind":"Any","default":null},{"name":"_destroyed","kind":"Any","default":false}]},{"type":"model","name":"TemplateActions1","properties":[{"name":"open_modal","kind":"Any","default":0},{"name":"close_modal","kind":"Any","default":0}]},{"type":"model","name":"BootstrapTemplateActions1","properties":[{"name":"open_modal","kind":"Any","default":0},{"name":"close_modal","kind":"Any","default":0}]},{"type":"model","name":"MaterialTemplateActions1","properties":[{"name":"open_modal","kind":"Any","default":0},{"name":"close_modal","kind":"Any","default":0}]}]}};
  var render_items = [{"docid":"f6ab0e9e-b13e-42f1-a890-21b9e0972b37","roots":{"p1481":"f4fb69f4-11a2-41dc-adf0-eaee4cd70605"},"root_ids":["p1481"]}];
  var docs = Object.values(docs_json)
  if (!docs) {
    return
  }
  const py_version = docs[0].version.replace('rc', '-rc.').replace('.dev', '-dev.')
  const is_dev = py_version.indexOf("+") !== -1 || py_version.indexOf("-") !== -1
  function embed_document(root) {
    var Bokeh = get_bokeh(root)
    Bokeh.embed.embed_items_notebook(docs_json, render_items);
    for (const render_item of render_items) {
      for (const root_id of render_item.root_ids) {
	const id_el = document.getElementById(root_id)
	if (id_el.children.length && (id_el.children[0].className === 'bk-root')) {
	  const root_el = id_el.children[0]
	  root_el.id = root_el.id + '-rendered'
	}
      }
    }
  }
  function get_bokeh(root) {
    if (root.Bokeh === undefined) {
      return null
    } else if (root.Bokeh.version !== py_version && !is_dev) {
      if (root.Bokeh.versions === undefined || !root.Bokeh.versions.has(py_version)) {
	return null
      }
      return root.Bokeh.versions.get(py_version);
    } else if (root.Bokeh.version === py_version) {
      return root.Bokeh
    }
    return null
  }
  function is_loaded(root) {
    var Bokeh = get_bokeh(root)
    return (Bokeh != null && Bokeh.Panel !== undefined)
  }
  if (is_loaded(root)) {
    embed_document(root);
  } else {
    var attempts = 0;
    var timer = setInterval(function(root) {
      if (is_loaded(root)) {
        clearInterval(timer);
        embed_document(root);
      } else if (document.readyState == "complete") {
        attempts++;
        if (attempts > 200) {
          clearInterval(timer);
	  var Bokeh = get_bokeh(root)
	  if (Bokeh == null || Bokeh.Panel == null) {
            console.warn("Panel: ERROR: Unable to run Panel code because Bokeh or Panel library is missing");
	  } else {
	    console.warn("Panel: WARNING: Attempting to render but not all required libraries could be resolved.")
	    embed_document(root)
	  }
        }
      }
    }, 25, root)
  }
})(window);</script>



<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Explore the data</div></div><div class="callout-body-container callout-body"><ol type="1">
<li><p>Create a new Markdown cell below this one.</p></li>
<li><p>Hover over the lowest point on your plot. What is the overall
minimum annual average temperature?</p></li>
</ol></div></div>

The overall annual minimum is 0.02554.

## BONUS: Save your work

You will need to save your analyses and plots to tell others about what
you find.

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Save Your Plot</div></div><div class="callout-body-container callout-body"><p>Just like with any other type of object in Python, if you want to
reuse your work, you need to give it a name.</p>
<ol type="1">
<li>Go back to your <code>hvplot</code> code, and give your plot a name
by assigning it to a variable. HINT: if you still want your plot to
display in your notebook, make sure to <strong>call</strong> its name at
the end of the cell.</li>
<li>Replace <code>my_plot</code> with the name you gave to your
plot.</li>
<li>Replace <code>'my_plot.html'</code> with the name you want for your
plot. If you change the file extension, <code>.html</code>, to
<code>.png</code>, you will get an image instead of an interactive
webpage, provided you have the necessary libraries installed.</li>
</ol>
<p>Once you run the code, you should see your saved plot in your files –
go ahead and open it up.</p>
<div data-__quarto_custom="true" data-__quarto_custom_type="Callout"
data-__quarto_custom_context="Block" data-__quarto_custom_id="8">
<div data-__quarto_custom_scaffold="true">

</div>
<div data-__quarto_custom_scaffold="true">
<p>You may need to right-click on your file and download it to be able
to view it.</p>
</div>
</div></div></div>

    /opt/conda/lib/python3.10/site-packages/holoviews/core/data/pandas.py:39: FutureWarning: Series.__getitem__ treating keys as positions is deprecated. In a future version, integer keys will always be treated as labels (consistent with DataFrame behavior). To access a value by position, use `ser.iloc[pos]`
      return dataset.data.dtypes[idx].type
    /opt/conda/lib/python3.10/site-packages/holoviews/core/data/pandas.py:39: FutureWarning: Series.__getitem__ treating keys as positions is deprecated. In a future version, integer keys will always be treated as labels (consistent with DataFrame behavior). To access a value by position, use `ser.iloc[pos]`
      return dataset.data.dtypes[idx].type


    Stored 'ann_climate_df' (DataFrame)

