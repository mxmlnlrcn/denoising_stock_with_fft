# Denoising asset prices with fft
### Summary:

Denoise the variation of the stock, forex, crypto, etc prices with FFT assuming that the buy/sell forces act like a composition of waves obtaining an interesting result for the EUR/USD forex pair


### Assumtions:

1. The buyers and the sellers are two group of people that act like a wave
2. The speculation and news act like "noise" in the valuation


### Logic behind:

Having the previous assumtions in my head I start computing the daily change of the asset having something like a white noise that have noise on it, so I calculate the Power spectral density (PSD) to identify frequencies that have a PSD greater than 2 standard deviations to build the "denoised" daily changes in the asset price to build a trading strategy following the next steps:

* Compute the 5 next changes in the price
* Compute the price multiplying the inicial price with the computed variations
* Define the target as the expected price given by the previous calculations
* If the target is grater than the actual price the algorithm goes Long, otherwise it goes Short
* If the expected variation by the target and the actual price is greater than a trigger it "place" the order
* The algorithm save the results of the comparition of the real and expected final price


### Parameters:

* Amount of days to forecast: 'forecast' variable
* Amount of days to training: 'train' variable
* Minimum diference in the expected change to place the position: mindif


### Results:

Using the daily data of the EUR/USD from the beggining of the 2000 the algorithm obtain an aggregate profit of 61.27% but it may fluctuate if you change the parameters and the asset
