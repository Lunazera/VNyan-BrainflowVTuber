# VNyan-Brainflow VTuber Control
Control parts of your VTuber model (like your ears or tail) with a BCI headset!

These are VNyan setups that use [BrainflowsIntoVRC](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat) to get incoming data from a Brain sensing headset like the Muse 2 to control your models ears or tails! There are a few different setup examples to choose from, so feel free to pick whichever suite your needs, or use as reference in building your own setups!

VNyan listens for OSC VRChat Avatar parameters as of v1.3.2, so you don't need any additional program to get the Brainflow data into VNyan. Parameters will be stored as their full addresses. Once the parameters are coming in, you can use them just like any other VNyan parameter in your graphs or pendulum chains to do whatever you wish! You can read a bit more about OSC parameters in the [VNyan Wiki.](https://github.com/Suvidriel/VNyanDoc/wiki/Parameters#osc-parameters)

## Requirements
- [VNyan](https://github.com/Suvidriel/VNyanDoc) (at least v1.3.3)
- [BrainflowsIntoVRC](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat)
- A compatible brain sensing headset [see list of headsets here](https://brainflow.readthedocs.io/en/stable/SupportedBoards.html)

## Setup
- Run BrainflowsIntoVRC with your brain sensing headset connected by bluetooth (you can find instructions on how to set this up in the [here](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat?tab=readme-ov-file#instructions))
- In VNyan, make sure the OSC Receiver Port is set to 9000. You can find this under `Menu > Settings > Misc`
- That's it! If the connection is found and working, VNyan is now receiving all the incoming OSC parameters from BFiVRC! You can check for these using the Monitor window.

### Brainflow Parameters
You can find more info about all the incoming parameters [here on the Brainflows github](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat?tab=readme-ov-file#parameter-descriptions). Parameters will be accessible in VNyan as their OSC address name. Below are a few examples of these parameters: 
- `BFI/NeuroFB/FocusLeft`
- `BFI/NeuroFB/FocusRight`
- `BFI/NeuroFB/FocusAvg`
- `BFI/NeuroFB/RelaxLeft`
- `BFI/NeuroFB/RelaxRight`
- `BFI/NeuroFB/RelaxAvg`
- `BFI/PwrBands/Left/Alpha`
- `BFI/PwrBands/Right/Alpha`
- `BFI/PwrBands/Avg/Alpha`

