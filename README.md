# VNyan Brainflow VTuber Control
Control parts of your VTuber model (like your ears or tail) with a BCI headset!

*Huge credit to [catboy](https://twitter.com/catboymech) for their work getting Brainflows into Warudo (this is definitely inspired by them!) and [ChilloutCharles](https://linktr.ee/ChilloutCharles) who put together the BrainFlowsIntoVRC tech!*

![Example gif of ears moving from BrainflowsIntoVRC](https://github.com/Lunazera/VNyan-BrainflowVTuber/blob/5bb00c64074e68716decc354422037e8e833d4bd/Brainflow-Ears-Example.gif)

I made a few VNyan setupts that use [BrainflowsIntoVRC](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat) to get incoming data from a Brain sensing headset (like the Muse 2) to control your models ears or tail! There are a few different setup examples to choose from, so feel free to pick whichever suite your needs, or use as reference in building your own setups!

VNyan listens for OSC VRChat Avatar parameters as of v1.3.2, so you don't need any additional program to get the Brainflow data into VNyan. Parameters will be stored as their full addresses. Once the parameters are coming in, you can use them just like any other VNyan parameter in your [Node Graphs](https://github.com/Suvidriel/VNyanDoc/wiki/Node-Graphs) or [Pendulum Chains](https://github.com/Suvidriel/VNyanDoc/wiki/Expressions-Colliders-Pendulums-Props#pendulum-chains) to do whatever you wish! You can read a bit more about OSC parameters in the [VNyan Wiki.](https://github.com/Suvidriel/VNyanDoc/wiki/Parameters#osc-parameters)

## Requirements
- [VNyan](https://github.com/Suvidriel/VNyanDoc) (at least v1.3.3)
- [BrainflowsIntoVRC](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat)
- A compatible brain sensing headset ([see list of headsets here](https://brainflow.readthedocs.io/en/stable/SupportedBoards.html))

## Setup
- Run BrainflowsIntoVRC with your brain sensing headset connected by bluetooth (you can find instructions on how to set this up in the [here](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat?tab=readme-ov-file#instructions))
- In VNyan, make sure the OSC Receiver Port is set to 9000. You can find this under `Menu > Settings > Misc`
- Import the Pendulum Chain `.vnchain` files or node graph files for whichever setup you chose
- Set the AvatarObject fields in the pendulum chains to your corresponding bones on your avatar (see below for an example)

That's it! If the connection is found and working, VNyan is now receiving all the incoming OSC parameters from Brainflows! You can check for these using the Monitor window.

## VNyan Graphs
This github contains a few example setups that you could use right away as is, or use as reference to build your own setups! All of these examples work by animating control bones on your model, but they could be easily adapted to animated blendshapes instead. They also all work by the [Pendulum Chain system](https://github.com/Suvidriel/VNyanDoc/wiki/Expressions-Colliders-Pendulums-Props#pendulum-chains), though you can use the OSC parameters anywhere that VNyan supports parameters.

### [Simple Ear Control](./SimpleEarControl)
This setup uses just one Pendulum Chain and the **Average Focus** parameter to rotate both your left and right ears around. As your focus increases, your ears will go more upright and 'alert'. Just import `SimpleEarControl.vnchain` and set your ear bones in the four Output Values to use it.

### [Focus-Relax Ear Control](./FocusRelaxEarControl)
This setup uses three Pendulum Chains. Your Left and Right ears will be independently rotated outwards by the **Left Focus** and **Right Focus** parameters respectively. The idea of this is that your ears will rotate out to the side more if that side of your brain has higher focus value. The third chain uses the **Average Relax** parameter to rotate both of your ears down and outwards the higher your relaxed measurement is.

### [Complex Ear Control](./ComplexEarControl)
This setup uses four Pendulum Chains to control your left and right ears by the **Alpha and Beta Power Bands**. Each ear will rotate outwards as each side's Beta power band increases, and rotate down and out as each side's Alpha power band increases.

### [Tail Wagging Control](./TailControl)
This setup uses two Pendulum Chains and a Node Graph to animate your tail by your brain waves. The **Tail Raise** chain will rotate to raise your avatar's tail as the **Focus Average Positive** parameter increases. The **TailWag** chain will animate your tail wagging back and forth and wag faster as the  **Average Beta** paramter increases. The Node Graph is a simple loop that animates a parameter between -1 to 1 repeatedly and increases it's speed as the brain sensing parameter increases.

## Pendulum Chain Example
Below is an example of what one of the imported [Pendulum Chain's](https://github.com/Suvidriel/VNyanDoc/wiki/Expressions-Colliders-Pendulums-Props#pendulum-chains) will look like. The outlined Avatar GameObject field is where you will enter the name of the Bone you want to be animated by the chain. You can press the magnifying glass icon to the right of this field to reveal a search window to help find this. 

![Example screenshot of an imported pendulum chain in VNyan, with the field to enter your desired avatar's bone](https://github.com/Lunazera/VNyan-BrainflowVTuber/blob/42154f672107bac5aa983b51d4fd2e28cc7b1dc6/PendulumChainExample.png)

## Brainflow Parameters
You can find more info about all the incoming parameters [here on the Brainflows github](https://github.com/ChilloutCharles/BrainFlowsIntoVRChat?tab=readme-ov-file#parameter-descriptions). Parameters will be accessible in VNyan as their OSC address name. You will be able to see all the incoming parameters in the Monitor window (if you left-click on any parameter name it will be copied into your clipboard). Below are a few examples of these parameters: 
- `BFI/NeuroFB/FocusLeft`
- `BFI/NeuroFB/FocusRight`
- `BFI/NeuroFB/FocusAvg`
- `BFI/NeuroFB/RelaxLeft`
- `BFI/NeuroFB/RelaxRight`
- `BFI/NeuroFB/RelaxAvg`
- `BFI/PwrBands/Left/Alpha`
- `BFI/PwrBands/Right/Alpha`
- `BFI/PwrBands/Avg/Alpha`

