# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
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
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
//Cut off frequency
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs= analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512); // Frequency response
w=0:%pi/511:%pi ;
plot(w/%pi,abs(HW));
xlabel(' Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```

# OUTPUT: 
<img width="757" height="707" alt="image" src="https://github.com/user-attachments/assets/0c023a2b-d3ec-4462-9db8-f885b66acb18" />
<img width="800" height="948" alt="image" src="https://github.com/user-attachments/assets/248a778e-5a48-42af-87f7-1d3935cd4058" />
<img width="753" height="692" alt="image" src="https://github.com/user-attachments/assets/d63166e1-ecd6-44d0-92c8-f1b4ed181ba4" />
<img width="636" height="937" alt="image" src="https://github.com/user-attachments/assets/71dac6ab-be99-4f17-9607-48d28c78cbd9" />
<img width="911" height="1599" alt="image" src="https://github.com/user-attachments/assets/1f6b843e-890c-4393-82e7-e956217c2174" />
<img width="936" height="1599" alt="image" src="https://github.com/user-attachments/assets/131a3dff-dc6c-4fca-b298-e31de682e898" />
<img width="1149" height="1600" alt="image" src="https://github.com/user-attachments/assets/471738ba-5050-48d0-84a3-dc46246ffe6c" />



# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

