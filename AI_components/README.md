# Toolkit sub-category "AI"
  Here you will find...Components from category: Ambrosinus // Sub-Category: AI  **(new position since Ambrosinus-Toolkit v1.2.1 | 3.AI)**
<br>

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/GHUSER_icon-LA.png" width="10%" height="10%"><img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/GH_icon-LA.png" width="10%" height="10%">

<br>
<br>

> [!IMPORTANT]  
> Crucial information necessary for users to succeed in using these AI components.
> 
> **These components require some Python libraries in order to work properly, so I have realized a full installation guide.**
> 
> <img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/04/ATk_guide_cover_v1_1.jpg" width="20%" height="20%">
>
> [ATk Requirements Installation - User Guide](https://bit.ly/ATkReqInstallGuidev1)

<br>
<br>

> [!TIP]  
> Since ATk v1.3.2, it is possible to use the SDstyles component, which utilizes the styles contained in this CSV file.
> 
> **Download it and copy&paste into the SD root folder: ...\stable-diffusion-webui\styles.csv**
> [Download CSV styles](https://github.com/lucianoambrosini/Ambrosinus-Toolkit/edit/main/AI_components/styles.csv)
>
> <img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2025/02/ATk-Styles_comp-3.png" width="30%" height="30%">

<br>
<br>

### AI as rendering engine (Stable Diffusion and ControlNET neural network run locally)
**Since Ambrosinus-Toolkit v1.1.9**
These are a set of components under development and can run Stable Diffusion and ControlNET locally (thanks to AUTOMATIC1111 project). The first two components developed are *LaunchSD_loc* and *AIeNG_loc*, but many other components have been added, even **AI outpainting since ATk v1.2.8**.
<br>

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/03/def_test_01.jpg" width="70%" height="70%">
</div>
<br>
<br>

## Outpainting
<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2024/04/AIoutpaint_demo_02.jpg" width="70%" height="70%">
</div>

**OFFICIAL ARTICLE**  ---> [AI as Rendering Engine: running Stable Diffusion and ControlNET locally via Grasshopper](https://ambrosinus.altervista.org/blog/ai-as-rendering-eng-sd-controlnet-locally)
<br>
**Video demo:** https://youtu.be/D5UbDOOlm98
<br>
<br>

### MeshyAI (text to 3D, image to 3D and text to texture)
As many already know, new platforms and services dedicated to AI are growing visibly. Meshy is one of them and promises to empower content creators to effortlessly turn text and images into captivating 3D assets in under a minute. Waiting for further developments... I'm starting to integrate these features within Ambrosinus Toolkit v1.2.6😉

Download: https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/MeshyAI_GH

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2024/01/ImageTo3D_demo_05.jpg" width="70%" height="70%">

**Extra info:** https://bit.ly/MeshyAIthroughGH
<br>
**Video demo:** https://youtu.be/h3d9UPJCVcQ
<br>
<br>

### DPTto3D-GH
This component runs the DPT process to calculate the monocular depth estimation of the image source. It also can generate PointCloud coordinates stored in a PLY file and a 3D preview of the PoinCloud or of the mesh object.

Download: https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/DPT-tools

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2023/02/DPTto3D_dept_PC_01.jpg" width="70%" height="70%">

**Extra info:** https://bit.ly/LA-WYSIWYTfromDPTto3D
<br>
**Video demo:** https://youtu.be/IzLwI8sw-LU
<br>
<br>

### DPTSemSeg-GH
This component runs the DPT image semantic segmentation. It also can generate segmented-image, segmented-mask and all data analysis of the process.

Download: https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/DPT-tools

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2024/06/DPTSemSeg_def_05.jpg" width="70%" height="70%">

**Extra info:** https://bit.ly/SemanticSegmentationGH
<br>
**Video demo:** https://youtu.be/t3ztM7b8I48
<br>
<br>

### StabilityAI_StableDiffusion_GH
Stable Diffusion inside Grasshopper with Python and Stability AI library from DreamStudio

**Download:** https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/StabilityAI-DS_GH

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/LA_StabilityAI-GH_comps_02-a.jpg" width="70%" height="70%">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/DS_StabilityAI-GH_demo_011.jpg" width="70%" height="70%">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/DS_StabilityAI-GH_demo_01.jpg" width="70%" height="70%">

**Extra info:** https://bit.ly/OpenAI-insideGrasshopper
<br>
**Video demo #04:** https://youtu.be/QbATRKGPYjc
<br>
**Video demo #01:** https://youtu.be/aymGdj9M9AQ
<br>
<br>

### OpenAI_Dall-E_GH "Light version"
DALL-E inside Grasshopper with Python and Open AI library

**Download:** https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/OpenAI_DALL-E_GH

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/demo_05.jpg" width="70%" height="70%">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/demo_01.jpg" width="70%" height="70%">

**Extra info installation/Light version:** https://bit.ly/OpenAI-insideGrasshopper
<br>
**Video demo Light version:** https://youtu.be/qrnbB2wb0PA
<br>
<br>

### OpenAI_Dall-E_GH "Advanced version"
DALL-E inside Grasshopper with Python and Open AI library

**Download:** https://github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/OpenAI_DALL-E_GH

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/ImageMask_OpenAI-GH_v2_demo-02.jpg" width="70%" height="70%">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/11/OpenAI-GH_v2_VAR_demo-04.jpg" width="70%" height="70%">

**Extra info Advanced version:** https://bit.ly/OpenAI-insideGrasshopperADV
<br>
**Video demo Advanced version (EDIT mode):** https://youtu.be/nmJTP1QvuIE
<br>
**Video demo Advanced version (VARIATION mode):** https://youtu.be/UPTc5o6rOLM
<br>
<br>

### Ask_To_OpenAI for tips (not only) - GPT-3 models
This ghuser component can execute the requesting process for OpenAI "text completion mode". This AI capability allows designer/users asking for answers or sunmitting instructions to AI, even code something...

**Download: https:**//github.com/lucianoambrosini/Ambrosinus-Toolkit/tree/main/AI_components/OpenAI_DALL-E_GH

<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/12/LA_OpenAI-GHask_demo-04.jpg" width="70%" height="70%">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2022/12/LA_OpenAI-GHask_demo-03.jpg" width="70%" height="70%">

**Extra info Ask to OpenAI:** https://bit.ly/OpenAI-QandA-insideGrasshopper
<br>
**Video demo Ask to OpenAI (Completion mode):** https://youtu.be/A5ReBxqf_SI
<br>
**Video demo Ask to OpenAI for code (GPT-3 model):** https://youtu.be/NU3ILLuBl3g
