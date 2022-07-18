# Early Reflaction
Attenuation of acoustic early reflections in simulated room using pretrained speech synthesis neural network.

In a recording room, the sound signal captured by a microphone is degraded do to the effects of noise and the reverberation of the signal in the room. unlike noise, there is a correlation in the reverberation we can utilized in order to extract of original clean sound signal. the reverberation can be split into the desired direct sound, early acoustic reflections (which arrive in the first 50 ms after the direct sound) and late reflections (anything later then 50 ms). although early reflections mostly considered a desirable effect, and can boost speech coloration and intelligibility, a clean and direct sound signal can be use for the tasks on monitoring and evaluation of a audio signal and equipment. this is why TV and radio station use an acoustic recording room in order to cancel these reflection.

In this project we have build a fully early reflection simulation engine, that run on the GPU. and can simulate infinite amount of early RIR is a linear time, after simulated a room to sample the RIR from.

![image](https://github.com/BIueMan/Early_Reflaction/blob/main/images/room_2.png)

We simulated the room in asending reflection cycles, as explained in the article. the room was simulated by devided the room into nomerical panels, and was simulated using a simulated energy flux from the sound sorce.

![image](https://github.com/BIueMan/Early_Reflaction/blob/main/images/panels.PNG)

We use the simulated RIR as the dataset to train a U-net_HIFI-gen model, to extract the early reflectio corelation from the digreted sound.

![image](https://github.com/BIueMan/Early_Reflaction/blob/main/images/DL.PNG)

Unlike previous articles, the model could have been train using multiple input signal. and the model was tested on a single input, 2 input, and the previous methods.


* $original$ - the original clean signal $x(t)$.
* $noisy$ - the degraded signal $y(t)$.
* $G$ - the reconstructed signal using only the HIGI-gen signal, $G(|Y_M|)$.
* $F_{old} + G$ - the proposed model, that was train with a randomly drawn RIR.
* $F_{1}+G$ - our proposed model [chapter 3], on a single input channel.
* $F_{2}+G$ - our proposed model [chapter 3], with two input channels.

![image](https://github.com/BIueMan/Early_Reflaction/blob/main/images/scoure_2_same.png)

graph of how the methods do on diffrent distanse from the couse.
![image](https://github.com/BIueMan/Early_Reflaction/blob/main/images/bar_2_same.png)

bars of how the methods do on average base on the original degrated signal.

# code
code will be added later
