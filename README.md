# The Resaturation and Bleed effect

#### Given variables:

`C` Color selected from colorwheel

`R` Resaturation `[0..1]`

`B` Bleed `[0..1]`

`K` Sampled color from canvas beneath cursor (Sampled continiously)

`S` Sampled color from canvas where brush-stroke started. (Only sampled once)

`N` Number of brush-dabs that were spawned since stylus-down.


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
