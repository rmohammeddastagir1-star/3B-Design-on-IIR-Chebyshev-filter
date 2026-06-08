# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```asm
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time='); 
 
 
//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas='); 
 
 
//Order of the filter 
 
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap)); 
17 
 
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N='); 
 
 
 
//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
 
 
Epsilon = sqrt ((10^(0.1*alphap))-1); 
disp(Epsilon,'Epsilon='); 
 
 
[pols ,gn] = zpch1(N, Epsilon,omegap ); 
disp(gn,'Gain'); 
disp(pols,'Poles'); 
 
 
 
hs=poly(gn,'s','coeff')/real(poly(pols,'s')); 
 
disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
 
 
 
z=poly(0,'z');//Defining variable z 
 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp(Hz,'Digital LPF Transfer function H(Z)='); 
 
 
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude '); 
title(' Frequency Response of Chebyshev IIR LPF');

```
# OUTPUT: 
<img width="756" height="680" alt="image" src="https://github.com/user-attachments/assets/cb6481ff-330f-4740-bf76-a37738089f60" />
<img width="879" height="920" alt="image" src="https://github.com/user-attachments/assets/fbf742f3-90be-457a-918d-65057a13387b" />
<img width="944" height="1493" alt="image" src="https://github.com/user-attachments/assets/fd452b02-710f-4bbe-bdc7-90366ec935a1" />
<img width="892" height="1600" alt="image" src="https://github.com/user-attachments/assets/9d47dd9c-4bd9-43f7-9046-671350882b4b" />
<img width="892" height="1600" alt="image" src="https://github.com/user-attachments/assets/ff39d8fd-b05e-4520-9bf0-7cf8bd64e7af" />
<img width="960" height="1552" alt="image" src="https://github.com/user-attachments/assets/a741b2c8-3c10-4346-b015-5698ef1b2216" />



# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
