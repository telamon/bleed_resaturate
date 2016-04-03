# The Resaturation and Bleed effect

The resaturation effect reminds you alot about the dulling mode of krita-smudge brush,
but it's behaviour different as it tries to simulate having a physical brush loaded color particles and painting onto a canvas containing wet-color.

Your brush get's tainted with the wet-color on the canvas and slowly as the brush disperses the particles your brush-stroke starts
to paint the color that you actually loaded it with.

The bleed factor creates an effect that at low values reminds you of some kind of digital Oil
while at high-values acts like digital watercolor.

#### Given variables:

`C` Color selected from colorwheel

`R` Resaturation `[0..1]`

`B` Bleed `[0..1]`

`K` Sampled color from canvas beneath cursor (Sampled continiously)

`S` Sampled color from canvas where brush-stroke started. (Only sampled once)

`N` Number of brush-dabs that were spawned since brush-stroke started.


#### Given alpha blending function:


    function blend(A,B,alpha) {
       return A * alpha + B * (1-alpha); 
    }

#### Then:
the function to calculate what color to render a dab during a stroke can be described as following:



    tint = blend(S,K,B);
    progress = N * R;  
    return blend(C,tint, progress);


<img src="https://raw.githubusercontent.com/telamon/bleed_resaturate/master/resaturation_and_bleed.png">
