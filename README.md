# Rectifier-Tube-White-Noise-Generator-and-RNG

![Final_Build](IMG_0128.jpg)

I repurposed an old Sylvania 5U4G rectifier tube into a white noise generator. While contemplating the new and improved Plasma Entropy Source V.2 (coming soon) 
I was thinking about optimal sources of entropy for RNGs. Specifically , what is a spectacular source of white noise? What do I have at home sitting on my desk which I could turn into a RNG?
Then it struck me, why not repurpose an old rectifier tube! It's a simple mechanism , two plates for the current being rectified to enter and exit, and a filament, which undergoes thermionic emission. If I heat the filament, introduce a positive voltage field, then sample the fluctuating current (caused by shot noise) I should be able to harvest an ideal source of entropy.  

This is a fun project because the industry standard for a source of shot noise is typically to reverse bias a zener diode or BJT transistor, however how boring! It’s much cooler to imagine the electrons boiling off the vibrating atoms of the filament , traversing the vacuum in the tube, and colliding with the anode plate. Solid state vs vacuum tube. 

Immedietly going into this project I was struck with a series of issues. 
- How do I identify the Shot-noise?
- How do I know what the amplitude of the noise will be, this must be known for when gain is applied during the amplification stage.

These issues are tied together but the main issue is really how do I identify shot-noise from other noise. It being whitenoise makes it tricky to identify. Let’s say I have 4 sources of white noise, how do I identify or discern the sources from output? All of the outputting white noise will look pretty much the same , there are no peaks, or specific frequyencies I can pick out. That being said, I’m only interested in one of these sources of the white noise; the shot-noise. 
Johnson noise is white noise caused by thermal fluctuations in resistors. 
Heat = atoms vibrating , atoms vibrating = charge characters (electrons being knocked around) 

my idea for noise consolidation , is to filter out any introductory noise via LC and RC filters, mains hum and EMI will be delt with prior to current being inputted into the 5U4G tube.

I calculate the proportional johnson noise produced per resistor in my amplification , sum the noise, then square root that amplitude and the ADC baseline from the final Fourier Transform of shot noise. 

