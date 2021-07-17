# Cryptocurrency Arbitrage Strategy
## Arbitrage Opportunities in Cryptocurrency

Cryptocurrency is traded on markets across the globe. It can be bought and sold at all times of the day. Since there is no downtime in trading cryptocurrencies, how can anyone know when the best time to buy and sell is? With the help of an analyst, they can help determine when the best time to buy and sell is, and if it's worth the hassle to do so. The cryptocurrency arbitrage strategy is to help clients understand when the best arbitrage opportunities exist, if there is potential for profits, and if the trend will cease.

---

## Technologies

In order for this program to run, this application must be used in JupyterLab, as it uses the Pandas/Python language. To run the program, it is essential to have JupyterLab installed. To ensure the code works, please open the file in a dev environment using python.

The operating systems and program versions are mentioned below and are highly recommended when running the program.

**Systems**

[conda 4.10.3](https://docs.anaconda.com/anaconda/install/index.html) - Package manager, Environment Manager

python 3.7 - included in Anaconda

JupyterLab - included in Python


---

## Installation Guide

As mentioned above, to ensure that there are no errors when running this application, the user or programmer must use JupyterLab to access the application file. 

Additional installs are needed before running the program. Please install in terminal, in a dev environment:

```JupyterLab
conda active dev
python -m ipykernel install --user --name dev
conda install -c conda-forge nodejs
conda deactivate

```
Once installed you should be able to open JupyterLab by the following code:

```
conda activate dev
jupyter lab
```

To exit out of JupyterLab hit: Ctrl + C

---

## Examples

When using the file, each line of code must be individually ran to capture the data. This ensures any data that needs to be pulled gets included in future calculations as we start to build out formulas for analysis. It is important that we do not miss a line of code.

To quickly run through the code, use the keyboard shortcut: Shift + Enter.


---

## Usage

To use the cryptocurrency arbitrage strategy, the repository will need to be cloned from GitHub and into a local repository.

In the crypto_arbitrage folder, you will want to use the 'crypto_arbitrage.ipynb' file. Enter into the dev environment by commanding: 

```
 conda activate dev
```
Next, use the code:

```
jupyter lab
```
to run the file.

1. Collect the Data

In this section, both datasets from Bitstamp and Coinbase are pulled and sorted by date/time with the usage of *index_col="Timestamp"*.



2. Prepare the Data
In order to prepare the data, the use of the functions *isnull()*, *duplicated()*, and *dropna()* were essential in providing clean data to work with. Using *isnull().mean()* or *isnull().sum()* helps to understand how much of the dataset is affected by incomplete data.


Code used to prepare/clean the data:

```
bitstamp.isnull()
bitstamp.duplicated()
bitstamp = bitstamp.dropna().copy()

```

Another important task that needs to be done before any analysis can begin is removing any currency signs from the dataset and changing the type of date to be float or an integer.




3. Analyze the Data

The focus becomes on analyzing the spread between the two exchange datasets. The goal is to capture the arbitrage spreade between the higher-priced exchange and the lower-priced exchange. The data that is focused on are the "Close" prices of that day.


Summary statistics are ran to understand the data we are working with. To do this we use the *describe()* function.



Visualizations are also used to help analyze the data. To do this we use the the code:

```
bitstamp_sliced['Close'].plot( figsize=(30, 20), title="Bitstamp v. Coinbase", color="green", label="Bitstamp")

```

To plot two graphs on one plot, we state *legend=True*
```
bitstamp_sliced['Close'].plot(legend=True, figsize=(30, 20), title="Bitstamp v. Coinbase", color="green", label="Bitstamp")
coinbase_sliced['Close'].plot(legend=True, figsize=(30, 20), color="orange", label="Coinbase")

```

This helps visualize the spread between the two exchange datasets.


Diving deeper, the focus turns to specific dates in order get a better idea of the data trends. The user will see individual historgrams and line graphs regarding the three time periods investigated. With the data provided by the individual time periods, the calculation of arbitrage spread begins by taking the higher-priced dataset minus the lower-priced dataset to understand the profit that could be gained or lost by the minute. From there the calculation to see what percentage of return a person could earn is computed by taking the gain (loss) and dividing it by the price of the lower-priced exchange 'close' data.

Filter the data by only including the returns that give a positive return (>0), and ensuring that it meets the 1% threshold to cover cost.

The returns that met these requirements are then multiplied by the price of the lower-priced exchange to show what the profit would be for that day.

The profits are then graphed to give an idea of how much profit is earned during what time of day. With further analysis, it can be infered that the arbitrage opportunity has ended by the end of the dataset as Bitstamp's prices increase and closely move with the prices of Coinbase. The spread gap closes and there is little profit that can be made.

---

## Contributors

[Julia Guanzon](www.linkedin.com/in/julia-guanzon)

## License

MIT License