# AUTOMATIC1111 has been update so ControlNET may not works properly (I am working to update this component)
📣 ControlNET has been updated to version 1.1 but AUTOMATIC1111 API support is not yet implemented. If you want to use this Grasshopper component, please be sure to install [the ControlNET v1.0 version as explained here](https://github.com/lllyasviel/webui-controlnet-v1-archived).

### AI as rendering engine (Stable Diffusion and ControlNET neural network run locally)

🆕 ✅**Ambrosinus-Toolkit v1.3.1**<br>
All the Grasshopper demo files have been updated to the latest ATk version with all new Stable SDiffusion Annotators, Preprocess models and Samplers.<br>

> [!NOTE]
>- [x] I have fixed the "loop execution" issue... stay tuned!
<br>
<br>

**Ambrosinus-Toolkit v1.2.6**<br>
The Variation mode (aka Image-To-Image mode) is added to the file named *"SD_Local_ControlNET_v10-11_v126_AIvariation_base&server_demo-01"* that is exactly the same as this: *"SD_Local_ControlNET_v10-11_v125_base&server_demo-01"* the main difference is that the definition v1.2.6 has the new component "AIimgToimg_loc" (Image-to-Image I2I) while in the v1.2.5 there is the "AIeng_loc" (Text-to-Image T2I). 

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2024/01/AIvariation_demo_01.jpg" width="70%" height="70%">
</div>
<br>

**Ambrosinus-Toolkit v1.2.3**
I have fixed a bug that comes up after some A1111 API updates. The issue generally appeared with this error message: "Index was outside the bounds of the array". it was related to the info text embedded in the generated image. Let me know if some other issues pop up! 😉

**Since Ambrosinus-Toolkit v1.2.2**
Now it is possible running Stable Difussion on your LAN. Please, [for more info have a look here](https://bit.ly/SDandCNinsideGH-Upd3) 😉

**Since Ambrosinus-Toolkit v1.1.9**
These are a set of components under development and are able to run SD and CN locally. The first two components developed are *LaunchSD_loc* and *AIeNG_loc*.


⚠️**Important Run Rhino as Administrator!** *Each session needs to run firstly the LAunchSD_loc component to establish a live connection between the Stable Diffusion engine and the Grasshopper components.*
<br>
<br>

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/03/def_test_01.jpg" width="70%" height="70%">
</div>
<br>
<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/06/remote_running-2.jpg" width="70%" height="70%">
</div>
<br>
<br>

### Have a look to the initial News frame at the top of the official article, there I highlight all the latest news and updates about the AI components

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/04/News_frame_02.png" width="90%" height="90%">
</div>
<br>


**OFFICIAL ARTICLE**  ---> [AI as Rendering Engine: running Stable Diffusion and ControlNET locally via Grasshopper](https://ambrosinus.altervista.org/blog/ai-as-rendering-eng-sd-controlnet-locally)

**Video 01:** https://youtu.be/D5UbDOOlm98

**Video 02:** https://youtu.be/ANsxTVHrFk8

**Video 03 LAN:** https://youtu.be/90DrY2AYaZQ

<br>
<br>

## Requirements

In order to run AIeNG_loc and LaunchSD_loc components the designer needs to install previously the AUTOMATIC11 and ControlNET project on his machine. There are a lot of guides about how to, anyway the simple procedure has been described in [my article](https://bit.ly/SDandCNinsideGH), please have a look to it before starting.

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/03/sdlocal_cmd_base.png" width="60%" height="60%">
</div>

<br>

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/03/SDlocal_extension.png" width="60%" height="60%">
</div>
<br>

### After the installation download at least one of the pre-trained datasets by [lllyasviel](https://github.com/lllyasviel) 

Again see my [official article](https://bit.ly/SDandCNinsideGH) where I have included all the datasets and the instructions.

**Enjoy your design exploration!** 😉

