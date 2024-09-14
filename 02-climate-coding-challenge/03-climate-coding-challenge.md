# Part 3: Convert units

It’s important to keep track of the units of all your data. You don’t
want to be like the [NASA team who crashed a probe into Mars because
different teams used different
units](https://www.latimes.com/archives/la-xpm-1999-oct-01-mn-17288-story.html))!

## Use labels to keep track of units for you and your collaborators

One way to keep track of your data’s units is to include the unit in
data **labels**. In the case of a `DataFrame`, that usually means the
column names.

Before we get started, make sure to load the climate `DataFrame` you
stored in the previous notebooks using Jupyter cell magic:

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Add units to your column name</div></div><div class="callout-body-container callout-body"><p>A big part of writing <strong>expressive</strong> code is descriptive
labels. Let’s rename the columns of your dataframe to include units.
Complete the following steps:</p>
<ol type="1">
<li>Replace <code>dataframe</code> with the name of
<strong>your</strong> <code>DataFrame</code>, and
<code>dataframe_units</code> with an expressive new name.</li>
<li>Check out the <a
href="https://www.ncei.noaa.gov/data/global-historical-climatology-network-daily/doc/GHCND_documentation.pdf">documentation
for GCHNd data</a>. We downloaded data with “standard” units; find out
what that means for both temperature and precipitation.</li>
<li>Replace <code>'TOBS_UNIT'</code> and <code>'PRCP_UNIT'</code> with
column names that reference the correct unit for each.</li>
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
      <th>INCHES</th>
      <th>FAHRENHEIT</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1893-10-01</th>
      <td>0.94</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-02</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-03</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-04</th>
      <td>0.04</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-05</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-09-26</th>
      <td>0.00</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>2023-09-27</th>
      <td>0.00</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>2023-09-28</th>
      <td>0.00</td>
      <td>73.0</td>
    </tr>
    <tr>
      <th>2023-09-29</th>
      <td>0.00</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>2023-09-30</th>
      <td>0.00</td>
      <td>78.0</td>
    </tr>
  </tbody>
</table>
<p>45971 rows × 2 columns</p>
</div>



## For scientific applications, it is often useful to have values in metric units

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Convert units</div></div><div class="callout-body-container callout-body"><p>The code below attempts to convert the data to Celcius, using Python
mathematical <strong>operators</strong>, like <code>+</code>,
<code>-</code>, <code>*</code>, and <code>/</code>. Mathematical
operators in Python work just like a calculator, and that includes using
parentheses to designat the <strong>order of operations</strong>. The
equation for converting Fahrenheit temperature to Celcius is:

$$
T_C = (T_F - 32) * \frac{5}{9}
$$

<p>This code is not well documented and doesn’t follow <a
href="https://peps.python.org/pep-0008/#other-recommendations">PEP-8
guidelines</a>, which has caused the author to miss an <strong>important
error</strong>!</p>
<p>Complete the following steps:</p>
<ol type="1">
<li>Replace <code>dataframe</code> with the name of
<strong>your</strong> <code>DataFrame</code>.</li>
<li>Replace <code>'old_temperature'</code> with the column name
<strong>you</strong> used; Replace <code>'new_temperature'</code> with
an <strong>expressive</strong> column name.</li>
<li><strong>THERE IS AN ERROR IN THE CONVERSION MATH - Fix
it!</strong></li>
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
      <th>INCHES</th>
      <th>FAHRENHEIT</th>
      <th>CELSIUS</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1893-10-01</th>
      <td>0.94</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-02</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-03</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-04</th>
      <td>0.04</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-05</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-09-26</th>
      <td>0.00</td>
      <td>74.0</td>
      <td>23.333333</td>
    </tr>
    <tr>
      <th>2023-09-27</th>
      <td>0.00</td>
      <td>69.0</td>
      <td>20.555556</td>
    </tr>
    <tr>
      <th>2023-09-28</th>
      <td>0.00</td>
      <td>73.0</td>
      <td>22.777778</td>
    </tr>
    <tr>
      <th>2023-09-29</th>
      <td>0.00</td>
      <td>66.0</td>
      <td>18.888889</td>
    </tr>
    <tr>
      <th>2023-09-30</th>
      <td>0.00</td>
      <td>78.0</td>
      <td>25.555556</td>
    </tr>
  </tbody>
</table>
<p>45971 rows × 3 columns</p>
</div>



<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-extra"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Looking for an Extra Challenge?</div></div><div class="callout-body-container callout-body"><p>Using the code below as a framework, write and apply a
<strong>function</strong> that converts to Celcius. You should also
rewrite this function name to be more expressive.</p>
<div class="sourceCode" id="cb1"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="kw">def</span> convert(temperature):</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a>    <span class="co">&quot;&quot;&quot;Convert temperature to Celcius&quot;&quot;&quot;</span></span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a>    <span class="cf">return</span> temperature <span class="co"># Put your equation in here</span></span>
<span id="cb1-4"><a href="#cb1-4" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb1-5"><a href="#cb1-5" aria-hidden="true" tabindex="-1"></a>dataframe[<span class="st">&#39;TOBS_C&#39;</span>] <span class="op">=</span> dataframe[<span class="st">&#39;TOBS&#39;</span>].<span class="bu">apply</span>(convert)</span></code></pre></div></div></div>




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
      <th>INCHES</th>
      <th>FAHRENHEIT</th>
      <th>CELSIUS</th>
      <th>TOBS_C</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1893-10-01</th>
      <td>0.94</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-02</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-03</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-04</th>
      <td>0.04</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-05</th>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-09-26</th>
      <td>0.00</td>
      <td>74.0</td>
      <td>23.333333</td>
      <td>23.333333</td>
    </tr>
    <tr>
      <th>2023-09-27</th>
      <td>0.00</td>
      <td>69.0</td>
      <td>20.555556</td>
      <td>20.555556</td>
    </tr>
    <tr>
      <th>2023-09-28</th>
      <td>0.00</td>
      <td>73.0</td>
      <td>22.777778</td>
      <td>22.777778</td>
    </tr>
    <tr>
      <th>2023-09-29</th>
      <td>0.00</td>
      <td>66.0</td>
      <td>18.888889</td>
      <td>18.888889</td>
    </tr>
    <tr>
      <th>2023-09-30</th>
      <td>0.00</td>
      <td>78.0</td>
      <td>25.555556</td>
      <td>25.555556</td>
    </tr>
  </tbody>
</table>
<p>45971 rows × 4 columns</p>
</div>


