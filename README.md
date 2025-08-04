# FTIR-Ethylene-Saturation
 
The purpose of the experiment is to predict the time it takes for an ethylene signal to become saturated when filling an FTIR spectrometer housing. This investigation was necessary as our team was working with limited quantities of ethylene and needed to saturate the spectrometer housing, without wasting excess ethylene, as soon as possible. This experiment thus found the parameters to facilitate an optimal use of our limited quantity of ethylene. The ethylene was then used to determine the additional (optical) pathlength the housing contributed to the absorbance values of each species under consideration, via Beer-Lambert law, however that analysis is proprietary and outside the scope of this experiment.

## Operational Setup
**Python Version** $\geq$ 3.8

**Libraries**
- numpy
- pandas
- matplotlib

## Results
It was determined that the ethylene will reach sufficient saturation after 3 air exchanges. This takes 21.5 minutes and leaves us with 64.5% of the ethylene bottle remaining. Indicating we can perform this pathlength determination for 2 more instruments, which is exactly what we did. The accuracy of the prediction with experimentation elucidates a feature of the gas dynamics inside the box as well. Namely, that we do indeed see a large percentage of mixing and very little displacement. Validating my assumption of (nearly) perfect mixing per the Continuous Stirred-Tank Reactor model. The notebook has all relevant figures and tables with predictions.
