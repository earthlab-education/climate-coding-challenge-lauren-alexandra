# Part 2: Wrangle your data

## Python **packages** let you use code written by experts around the world

Because Python is open source, lots of different people and
organizations can contribute (including you!). Many contributions are in
the form of **packages** which do not come with a standard Python
download.

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-read"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Read More: Packages need to be installed and imported.</div></div><div class="callout-body-container callout-body"><p>Learn more about using Python packages. How do you find and use
packages? What is the difference between installing and importing
packages? When do you need to do each one? <a
href="https://www.earthdatascience.org/courses/intro-to-earth-data-science/python-code-fundamentals/use-python-packages/">This
article on Python packages</a> will walk you through the basics.</p></div></div>

In the cell below, someone was trying to import the **pandas package**,
which helps us to work with [**tabular data** such as comma-separated
value or csv
files](https://www.earthdatascience.org/courses/intro-to-earth-data-science/file-formats/use-text-files/).

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Import a package</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Correct the typo below to properly import the pandas package under
its <strong>alias</strong> pd.</li>
<li>Run the cell to import pandas</li>
</ol></div></div>

> **Warning**
>
> Make sure to run your code in the right **environment** to avoid
> import errors!
>
> We’ve created a coding **environment** for you to use that already has
> all the software and packages you will need! When you try to run some
> code, you may be prompted to select a **kernel**. The **kernel**
> refers to the version of Python you are using. You should use the
> **base** kernel, which should be the default option for you.

## Download the practice data

Next, lets download some climate data from
**Boulder, CO** to practice with. We keep our
practice data on GitHub, so that we can check that it still works and
make sure it looks just like the data you would download from the
original source.

The cell below contains the URL for the data you will use in this part
of the notebook. There are two things to notice about the URL code:

1.  It is surrounded by quotes – that means Python will interpret it as
    a `string`, or text, type, which makes sense for a URL.
2.  The URL is too long to display as one line on most screens. We’ve
    put parentheses around it so that we can easily split it into
    multiple lines by writing two strings – one on each line.

However, we still have a problem - we can’t get the URL back later on
because it isn’t saved in a **variable**. In other words, we need to
give the url a **name** so that we can request in from Python later
(sadly, Python has no ‘hey what was that thingy I typed yesterday?’
function).

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-read"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Read More: Names/variables in Python</div></div><div class="callout-body-container callout-body"><p>One of the most common challenges for new programmers is making sure
that your results are stored so you can use them again. In Python, this
is called <strong>naming</strong>, or saving a
<strong>variable</strong>. Learn more in this <a
href="https://www.earthdatascience.org/courses/intro-to-earth-data-science/python-code-fundamentals/get-started-using-python/variables/">hands-on
activity on using variables</a> from our learning portal.</p></div></div>

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Save the URL for later</div></div><div class="callout-body-container callout-body"><ol type="1">
<li>Pick an expressive variable name for the URL.</li>
<li>Click on the <code>Jupyter</code> tab in the console panel at the
bottom of VSCode to see all your variables. Your new url variable will
not be there until you define it and run the code.</li>
<li>At the end of the cell where you define your url variable,
<strong>call your variable (type out its name)</strong> so you can take a look at it.</li>
</ol></div></div>

The `pandas` library you imported can download data from the internet
directly into a type of Python **object** called a `DataFrame`. In the
code cell below, you can see an attempt to do just this. But there are
some problems…

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Fix some code!</div></div><div class="callout-body-container callout-body"><ol type="1">
<li><p>Leave a space between the <code>#</code> and text in the comment
and try making the comment more informative</p></li>
<li><p>Make any changes needed to get this code to run. HINT: The
<code>my_url</code> variable doesn’t exist - you need to replace it with
the variable name <strong>you</strong> chose.</p></li>
<li><p>Modify the <code>.read_csv()</code> statement to include the
following parameters:</p>
<ul>
<li><code>index_col='DATE'</code> – this sets the <code>DATE</code>
column as the index. Needed for subsetting and resampling later on</li>
<li><code>parse_dates=True</code> – this lets <code>python</code> know
that you are working with time-series data, and values in the indexed
column are <strong>date time objects</strong></li>
<li><code>na_values=['NaN']</code> – this lets <code>python</code> know
how to handle missing values</li>
</ul></li>
<li><p>Clean up the code by using <strong>expressive variable
names</strong>, <strong>expressive column names</strong>, <strong>PEP-8
compliant code</strong>, and <strong>descriptive
comments</strong></p></li>
</ol></div></div>

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-warning"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div></div><div class="callout-body-container callout-body"><p><strong>Make sure to call your <code>DataFrame</code> by typing it’s
name as the last line of your code cell</strong> Then, you will be able
to run the test cell below and find out if your answer is correct.</p></div></div>




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
      <th>STATION</th>
      <th>PRCP</th>
      <th>TOBS</th>
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
      <td>USC00050848</td>
      <td>0.94</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-02</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-03</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-04</th>
      <td>USC00050848</td>
      <td>0.04</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1893-10-05</th>
      <td>USC00050848</td>
      <td>0.00</td>
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
      <td>USC00050848</td>
      <td>0.00</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>2023-09-27</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>2023-09-28</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>73.0</td>
    </tr>
    <tr>
      <th>2023-09-29</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>2023-09-30</th>
      <td>USC00050848</td>
      <td>0.00</td>
      <td>78.0</td>
    </tr>
  </tbody>
</table>
<p>45971 rows × 3 columns</p>
</div>



> HINT: Check out the `type()` function below - you can use it to check
> that your data is now in `DataFrame` type object




    pandas.core.frame.DataFrame



## Clean up your `DataFrame`

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-titled callout-task"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div><div class="callout-title-container flex-fill">Try It: Get rid of unwanted columns</div></div><div class="callout-body-container callout-body"><p>You can use <strong>double brackets</strong> (<code>[[</code> and
<code>]]</code>) to select only the columns that you want from your
<code>DataFrame</code>:</p>
<ol type="1">
<li>Change <code>some_column_name</code> to the Precipitation column
name and <code>another_column_name</code> to the Observed Temperature
column name.</li>
</ol>
<div data-__quarto_custom="true" data-__quarto_custom_type="Callout"
data-__quarto_custom_context="Block" data-__quarto_custom_id="9">
<div data-__quarto_custom_scaffold="true">

</div>
<div data-__quarto_custom_scaffold="true">
<p>Column names are text values, not variable names, so you need to put
them in quotes!</p>
</div>
</div></div></div>

<link rel="stylesheet" type="text/css" href="./assets/styles.css"><div class="callout callout-style-default callout-warning"><div class="callout-header"><div class="callout-icon-container"><i class="callout-icon"></i></div></div><div class="callout-body-container callout-body"><p><strong>Make sure to call your <code>DataFrame</code> by typing it’s
name as the last line of your code cell</strong> Then, you will be able
to run the test cell below and find out if your answer is correct.</p></div></div>




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



Great work! You finished the data cleaning section of this coding
challenge. You can go on to the next notebook – but first, make sure to
store the climate `DataFrame` you made so that you can use it in the
next notebooks. We’ll do this using the [ipython `store` **cell
magic**](https://ipython.readthedocs.io/en/stable/config/extensions/storemagic.html).
[Cell magic
commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html)
aren’t part of your regular code; they’re there to help you with coding
in Jupyter Notebooks. You can tell it’s a magic command because it
starts with `%`:

    Stored 'climate_df' (DataFrame)

