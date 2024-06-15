# Data Analysis with Python

## Cheat Sheet: Model Development

<table>
  <tr>
    <th>Process</th>
    <th>Description</th>
    <th>Code Example</th>
  </tr>
  <tr>
    <td>Linear Regression</td>
    <td>Create a Linear Regression model object</td>
    <td>
      <pre><code>from sklearn.linear_model import LinearRegression
lr = LinearRegression()</code></pre>
    </td>
  </tr>
  <tr>
    <td>Train Linear Regression model</td>
    <td>Train the Linear Regression model on dedicated data, separating Input and Output attributes. When there is a single attribute in Input, then it is simple linear regression. When there are multiple attributes, it is multiple linear regression.</td>
    <td>
      <pre><code>X = df[['attribute_1', 'attribute_2', ...]]
y = df['target_attribute']
lr.fit(X,y)</code></pre>
    </td>
  </tr>
  <tr>
    <td>Generate output predictions</td>
    <td>Predict the output for a set of input attribute values.</td>
    <td>
      <pre><code>y_hat = lr.predict(X)</code></pre>
    </td>
  </tr>
  <tr>
    <td>Identify the coefficient and intercept</td>
    <td>Identify the slope coefficient and intercept values of the linear regression model defined by \(y = mX + c\). Where m is the slope coefficient and c is the intercept.</td>
    <td>
      <pre><code>coeff = lr.coef_
intercept = lr.intercept_</code></pre>
    </td>
  </tr>
  <tr>
    <td>Residual Plot</td>
    <td>This function will regress y on x (possibly as a robust or polynomial regression) and then draw a scatter plot of the residuals.</td>
    <td>
      <pre><code>import seaborn as sns
sns.residplot(df[['attribute_1']], y=df[['attribute_2']])</code></pre>
    </td>
  </tr>
  <tr>
    <td>Distribution Plot</td>
    <td>This function can be used to plot the distribution of data w.r.t. a given attribute.</td>
    <td>
      <pre><code>import seaborn as sns
sns.distplot(df['attribute_name'], hist=False)
# can include other parameters like color, label and so on.</code></pre>
    </td>
  </tr>
  <tr>
    <td>Polynomial Regression</td>
    <td>Available under the numpy package, for single variable feature creation and model fitting.</td>
    <td>
      <pre><code>f = np.polyfit(x, y, n)
# Generates the polynomial features of order n
p = np.poly1d(f)
y_hat = p(x)
# p matches the polynomial model used to generate the predicted output
# y_hat is the predicted output</code></pre>
    </td>
  </tr>
  <tr>
    <td>Multi-variate Polynomial Regression</td>
    <td>Generates a new feature matrix consisting of all polynomial combinations of the features with the degree less than or equal to the specified degree.</td>
    <td>
      <pre><code>from sklearn.preprocessing import PolynomialFeatures
Z = df[['attribute_1', 'attribute_2', ...]]
poly = PolynomialFeatures(degree=2)
Z_ = poly.fit_transform(Z)</code></pre>
    </td>
  </tr>
  <tr>
    <td>Pipeline</td>
    <td>Data Pipelines simplify the steps of processing the data. We create the pipeline by creating a list of tuples including the name of the model or estimator and its corresponding constructor.</td>
    <td>
      <pre><code>from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
pipeline = Pipeline([('scaler', StandardScaler()), ('poly', PolynomialFeatures(include_bias=False)), ('model', LinearRegression())])
pipeline.fit(X,y)
Z = pipeline.predict(X)</code></pre>
    </td>
  </tr>
  <tr>
    <td>R² value</td>
    <td>R², also known as the coefficient of determination, is a measure to indicate how close the data is to the fitted regression line. The value of the R²-squared is the percentage of variation of the response variable that is explained by a linear model. 
    <br>a. For Linear Regression (single or multi attribute) 
    <br>b. For Polynomial regression (single or multi attribute)</td>
    <td>
      a.
      <pre><code>X = df[['attribute_1', 'attribute_2', ...]]
y = df['target_attribute']
lr = LinearRegression()
lr.fit(X,y)
R2_score = lr.score(X,y)</code></pre>
      b.
      <pre><code>from sklearn.metrics import r2_score
f = np.polyfit(x, y, n)
p = np.poly1d(f)
y_hat = p(x)
R2_score = r2_score(y, y_hat)</code></pre>
    </td>
  </tr>
  <tr>
    <td>MSE value</td>
    <td>The Mean Squared Error measures the average of the squares of errors, that is, the difference between actual value and the estimated value.</td>
    <td>
      <pre><code>from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y, y_hat)</code></pre>
    </td>
  </tr>
</table>
