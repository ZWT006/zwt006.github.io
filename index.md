---
layout: page
---
<style>
@import url('https://fonts.googleapis.com/css2?family=Ma+Shan+Zheng&family=Yuji+Mai&display=swap');
.kai-name { font-family: "Ma Shan Zheng", 'KaiTi', 'STKaiti', 'KaiTi TC', 'DFKai-SB', serif; }
</style>
# Wentao Zhang (<span class="kai-name">张文涛</span>)
<!--張-->

<!-- Hide the fast navigation right part of page (just hide and leave these part blank but unused) -->
<!-- <script>
document.addEventListener('DOMContentLoaded', function () {
  // 隐藏 Recently Updated（通过 id）
  var recent = document.getElementById('access-lastmod');
  if (recent) recent.style.display = 'none';

  // 隐藏包含 Trending Tags 的 section（在生成 HTML 中，标签用 .post-tag）
  document.querySelectorAll('section').forEach(function(sec){
    if (sec.querySelector('.post-tag')) sec.style.display = 'none';
  });

  // 保险：如果主题在其它位置重复渲染，额外隐藏任何 .d-flex.flex-wrap 容器
  document.querySelectorAll('.d-flex.flex-wrap').forEach(function(el){ el.style.display = 'none'; });
});
</script> -->

<!-- ## Biography
--- -->
<img class="right" src="/images/person/Profile24.jpg" width="300px"  alt="robots" />
Greeting! I am wentao, an enthusiastic on robotics. My research goal is to build agile, safe, intelligent, and autonomous mobile robot systems. So my research lies in the intersection of robotics, planning, optimization, and control, both model-based and model-free methods are employed.    
Welcome cooperation and discussion.


<!-- <center class="half">
    <img src="/images/rm/robots.jpg" width="400"/>
    <img src="/images/rm/operate.jpg" width="400"/>
</center> -->

<!-- <div style="border: 0px solid #1182BF;padding: 4px;">
    <p style="text-align: justify;"> <img class="right" src="/images/rm/robots.jpg" width="490px" /> I am a highly-motivated person interested in robotics. My research goal is to build agile, safety, intelligent, and autonomous mobile robot systems. So my research lies in the intersection of robotics, planning, optimization, and control. Since 2022, I have been concurrently pursuing a M.Sc. in School Artificial Intelligence and Automation at Huazhong University of Science and Technology (HUST) under the supervision of Prof. Lijun Zhu. I received my B.Sc. in School of Control Engineering at Northeastern University at Qinhuangdao (NEUQ) in 2022.</p>
</div> -->
<!-- <div style="text-align: center">
    <p style="font-weight: bold">I am seeking a PhD position starting in Fall 2025.</p>
</div> -->
<!-- <p style="margin-top: 10px;">chigui-2 motion video in May, 2022</p> -->
<!-- Where I spent wonderful time with my friends, teammates, and teachers. -->

<!-- <img class="center" src="/images/person/Profile24.jpg" width="600px"  alt="robots" /> -->
<!-- ![robots](/images/rm/robots.jpg) -->

<!-- ## Education
---
**HuaZhong University of Science And Technology**, China 09/2022 - Present  
*Master* student in Control Science and Engineering, expected June 2025 (GPA 91.96/100)  
**Northeastern University at Qinhuangdao**, China 09/2018 - 06/2022  
*Bachelor* in Technique and Instrumentation of Measurements (GPA 92.22/100)   -->


<style>
.news-box {
  border: 0px solid #1182BF;
  padding: 8px;
  max-height: 250px; /* 可根据需要调整高度 */
  overflow-y: auto;
  overflow-x: hidden;
  box-sizing: border-box;
  background: transparent;
}
.news-box h3 { margin-top: 0; }
.news-box ul { margin: 6px 0 12px 18px; padding-right: 8px; }
.news-box details { margin-top: 8px; }
/* 美化滚动条 (WebKit) */
.news-box::-webkit-scrollbar { width: 10px; }
.news-box::-webkit-scrollbar-track { background: #f1f1f1; border-radius: 10px; }
.news-box::-webkit-scrollbar-thumb { background: #c1c1c1; border-radius: 10px; }
/* FireFox */
.news-box { scrollbar-width: thin; scrollbar-color: #c1c1c1 #f1f1f1; }
@media (max-width: 600px) {
  .news-box { max-height: 200px; }
}
</style>

<div class="news-box" tabindex="0" aria-label="News">
    <h3><b>News</b></h3>
    <ul>
        <li><em>Oct. 2025</em>: On paper (1st) has been accepted by RA-L，a nice end of my master's journal </li>
        <li><em>Oct. 2025</em>: Start my PhD journal in <a href="http://www.dragon.t.u-tokyo.ac.jp">DRAGON Lab</a>.  Happy to meet nice people in here</li>
        <li><em>June. 2025</em>: Start my internship on Shanghai AI Lab. Very happy to join in the excellent gropu (Embodied AI Center) </li>
        <li><em>Jun. 2024</em>: Two paper (1st, 2nd author) have been accepted by IROS 2024.</li>
        <li><em>May. 2024</em>: Participated in ICRA 2024 (Yokohama, Japan). Honorary to present an Oral Presentation!</li>
        <li><em>Jan. 2024</em>: Three co-authored papers have been accepted by ICRA 2024. Very happy that one of it earned Finelist for Best Conference Paper Award</li>
    </ul>
</div>

## Internship
---
<style>
.internship-row { --internship-gap: 28px; display: flex; gap: var(--internship-gap); align-items: flex-start; margin: 12px 0; }
.internship-img { --logo-scale: 0.9; /* 比例：logo 在容器中的占比 (0.0 - 1.0) */
    flex: 0 0 200px; width: 200px; height: 180px; overflow: hidden; border-radius: 4px; display: flex; align-items: center; justify-content: center; background: #fff; padding: 6px; box-sizing: border-box; line-height: 0; }
.internship-img img { /* 使用 --logo-scale 控制 logo 相对于容器的最大尺寸，便于不同图片按比例显示且居中 */
    display: block;
    margin: auto; /* 保证图片在容器中水平/垂直居中备用 */
    width: auto;
    height: auto;
    max-width: calc(var(--logo-scale) * 100%);
    max-height: calc(var(--logo-scale) * 100%);
    object-fit: contain;
    object-position: center center; }
.internship-content { flex: 1; /* 文本容器 */
  font-size: 1.10rem; /* 字号增大 */
  line-height: 1.15; /* 行间距减小，比较紧凑 */
  color: inherit;
}
.internship-title { color: #1182BF; font-weight: 700; margin: 2px 0 6px; font-size: 1.2rem; }
@media (max-width: 700px) {
    .internship-row { --internship-gap: 12px; flex-direction: column; }
    .internship-img { flex: 0 0 auto; width: 100%; height: auto; }
    .internship-img img { height: auto; object-fit: contain; }
    .internship-content { font-size: 1rem; line-height: 1.25; }
}
</style>

<div class="internship-row">
    <div class="internship-img" style="--logo-scale:0.95;">
        <img src="/images/logos/SHAILab.png" alt="Shanghai AI Laboratory">
    </div>
    <div class="internship-content">
        <p        ></p>
        <p class="internship-title">Shanghai AI Laboratory</p>
        <p><strong>June. 2025 - Oct. 2025</strong> OpenRobotLab, Shanghai, China</p>
    <p>Closely worked with <a href="https://wangjingbo1219.github.io" target="_blank" rel="noopener noreferrer">Jingbo Wang</a></p>
        <p><strong>Topic:</strong> Whole-body Humanoid-Object Interaction</p>
    </div>
</div>

## Education
---
<div class="internship-row">
   <div class="internship-img" style="--logo-scale:0.9;">
    <img src="/images/logos/UTokyoLogoB.jpg" alt="University of Tokyo">
    </div>
    <div class="internship-content">
        <p        ></p>
        <p class="internship-title">University of Tokyo, Tokyo, Japan</p>
        <p><strong>Oct. 2025 - Future</strong> Doctor Student of Mechanical Engineering</p>
    <p>Supervisor: Assoc. Prof. <a href="http://www.dragon.t.u-tokyo.ac.jp/author/moju-zhao/" target="_blank" rel="noopener noreferrer">Moju Zhao</a></p>
        <p><strong>Topic:</strong> Articulated-Aerial Robot, Motion Planning and Control</p>
    </div>
</div>

<div class="internship-row">
    <div class="internship-img" style="--logo-scale:0.8;">
        <img src="/images/logos/HUSTLogo.jpg" alt="Huazhong University">
    </div>
    <div class="internship-content">
        <p class="internship-title">Huazhong University of Science and Technology, Wuhan, China</p>
        <p><strong>Step. 2022 - June. 2025</strong> Master Student of Control Science and Engineering</p>
    <p>Supervisor: Prof. <a href="http://faculty.hust.edu.cn/ZHULIJUN/en/index/2288717/list/index.htm" target="_blank" rel="noopener noreferrer">Lijun Zhu</a></p>
        <p><strong>Topic:</strong> Quadruped Robot, Motion Planning and Control</p>
    </div>
</div>

<div class="internship-row">
    <div class="internship-img" style="--logo-scale:0.65;">
        <img src="/images/logos/NEUQLogo.png" alt="Northeast University">
    </div>
    <div class="internship-content">
        <p class="internship-title">Northeast University at Qinhuangdao, Qinhuangdao, China</p>
        <p><strong>Step. 2018 - June. 2022</strong> Bachelor Student of Measurement and Control Technology and Instrument</p>
    <p>Supervisors:  Assoc. Prof. <a href="https://graduate.neuq.edu.cn/info/1397/5161.htm" target="_blank" rel="noopener noreferrer">Lu Cai</a>, <a href="http://kzgc.neuq.edu.cn/info/1023/1235.htm" target="_blank" rel="noopener noreferrer">Wenyi Sun</a> </p>
        <p><strong>Topic:</strong> Mobile Robot, Motion Planning and Control</p>
    </div>
</div>

<!-- new with a expandable button -->
<!-- <div>
    <h3><b>News</b></h3>
    <ul>
        <li><em>Oct. 2025</em>: Two paper (1st, 2nd author) have been accepted by IROS 2024.</li>
        <li><em>June. 2025</em>: Start my internship on Shanghai AI Lab. Very happy to join in the excellent gropu (Embodied AI Center) and supervio</li>
    </ul>
    <details>
        <summary><b>Old News</b></summary>
        <ul>
            <li><em>Jun. 2024</em>: Two paper (1st, 2nd author) have been accepted by IROS 2024.</li>
            <li><em>May. 2024</em>: Participated in ICRA 2024 (Yokohama, Japan). Honorary to present an Oral Presentation!</li>
            <li><em>Jan. 2024</em>: Three co-authored papers have been accepted by ICRA 2024. Very happy that one of it earned Finelist for Base Conference Paper Award</li>
        </ul>
    </details>
</div> -->

## Awards & Honors
---
• Huazhong University of Science and Technology Outstanding Graduate (2025)  
• Finalist for the Best Conference Paper Award (ICRA-2024)  
• Finalist for the Best Student Paper Award, and (ICRA-2024)  
• Finalist for the Best Paper Award on Multi-Robot Systems (ICRA-2024)  
• Xiaomi Scholarship for Postgraduate Students (2023)  
• Northeastern University Outstanding Graduate (2022) <!-- , University Level -->  
• Northeastern University Outstanding Graduation Thesis (2022) <!-- , University Level -->  
• National Inspiration Scholarship for Undergraduates (2020, 2021) <!-- , National Level -->  
• National Scholarship for Undergraduates (2019) <!-- , National Level -->  
<!-- • National College Robot Competition ROBOMASTER(2021, Third Prize)   -->
<!-- ## Skills
---
• Software: MATLAB, Altium Designer, Keil, SolidWorks, Wolfram Mathematica  
• Programming: C/C++, Python for Linux(ROS) and Embedded Systems(RTOS)  
• Engineering: Circuit/PCB Design and Debug, Mechanical Assembly  
• Soft Skills: Planned, Responsible, Organized, Self-Motivating, Teamwork, Adaptability, Analytical Thinking -->

## Selected Research
---
### [PhysHSI: Towards a Real-World Generalizable and Natural Humanoid-Scene Interaction System](https://why618188.github.io/physhsi/)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p style="margin: 0 0 0px;">Huayi Wang*, <strong>Wentao Zhang*</strong>, Runyi Yu*, Tao Huang, Junli Ren, Feiyu Jia, Zirui Wang, Xiaojie Niu, Xiao Chen, Jiahe Chen, Qifeng Chen, Jingbo Wang and Jiangmiao Pang</p>
    <p style="margin: 0;">
        <iframe class="left" width="480" height="270" src="https://www.youtube.com/embed/dTj6FjoQ5u0?si=ysK_4ezAkb6but9H" title="Hybrid Dynamics Modeling and Trajectory Planning" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        Deploying humanoid robots to interact with real-world environments—such as carrying objects or sitting on chairs—requires generalizable, lifelike motions and robust scene perception. Although prior approaches have advanced each capability individually, combining them in a unified system is still an ongoing challenge. In this work, we present a physical-world humanoid-scene interaction system, PhysHSI, that enables humanoids to autonomously perform diverse interaction tasks while maintaining natural and lifelike behaviors. PhysHSI comprises a simulation training pipeline and a real-world deployment system. In simulation, we adopt adversarial motion prior-based policy learning to imitate natural humanoid-scene interaction data across diverse scenarios, achieving both generalization and lifelike behaviors. For real-world deployment, we introduce a coarse-to-fine object localization module that combines LiDAR and camera inputs to provide continuous and robust scene perception. We validate PhysHSI on four representative interactive tasks—box carrying, sitting, lying, and standing up—in both simulation and real-world settings, demonstrating consistently high success rates, strong generalization across diverse task goals, and natural motion patterns.
    </p>
</div>

### [Hybrid Dynamics Modeling and Trajectory Planning for a Cable-Trailer System with a Quadruped Robot](/posts/SledNav)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p style="margin: 0 0 0px;"><strong>Wentao Zhang</strong>, Shaohang Xu, Gewei Zuo, Bolin Li, Jingbo Wang, and Lijun Zhu<sup>十</sup></p>
    <p style="margin: 0;">
        <iframe class="left" width="480" height="270" src="https://www.youtube.com/embed/x52NgrAE96Y?si=ZeYOP1Zb1nAu_V2E" title="Hybrid Dynamics Modeling and Trajectory Planning" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        Inspired by the utilization of dogs in sled-pulling for transportation, we introduce a cable-trailer system with a quadruped robot. The motion planning of the proposed robot system presents challenges arising from the nonholonomic constraints of the trailer, system underactuation, and hybrid interaction through the cable. To tackle these challenges, we develop a hybrid dynamics model that accounts for the cable's taut/slack status. Since it is computationally intense to directly optimize the trajectory, we first propose a search algorithm to compute a sub-optimal trajectory as the initial solution. Then, a novel collision avoidance constraint based on the geometric shapes of objects is proposed to formulate the trajectory optimization problem for the hybrid system. The proposed trajectory planning method is implemented on a Unitree A1 quadruped robot with a customized cable-trailer and validated through experiments.
    </p>
</div>


### [Agile and Safe Trajectory Planning for Quadruped Navigation with Motion Anisotropy Awareness](/posts/AgileNav)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p style="margin: 0 0 0px;"><strong>Wentao Zhang</strong>, Shaohang Xu, Peiyuan Cai, and Lijun Zhu<sup>十</sup></p>
    <p> <img class="left" src="/images/agilenav/systemoverview.bmp" width="500px" alt="systemoverview"/> Quadruped robots demonstrate robust and agile movements in various terrains; however, their navigation autonomy is still insufficient. One of the challenges is that the motion capabilities of the quadruped robot are anisotropic along different directions, which significantly affects the safety of quadruped robot navigation. This paper proposes a navigation framework that takes into account the motion anisotropy of quadruped robots including kinodynamic trajectory generation, nonlinear trajectory optimization, and nonlinear model predictive control. In simulation and real robot tests, we demonstrate that our motion-anisotropy-aware navigation framework could: (1) generate more efficient trajectories and realize more agile quadruped navigation; (2) significantly improve the navigation safety in challenging scenarios. The implementation is realized as an open-source package at <a href="https://github.com/ZWT006/agile_navigation" target="_blank" >agile_navigation: Quadruped Robot Planning ROS Package (github.com)</a></p>
</div>

### [Quadruped Robot Planning Framework for Navigation, Formation, Collaboration, and Flocking](/posts/MultiAgent)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p> <img class="left" src="/images/multinav/framework.bmp" width="500px" alt="framework" /> After multiple optimization iterations, we developed and deployed the complete navigation framework, encompassing both hardware and software. The hardware is characterized by its compactness and lightweight design. Meanwhile, the software integrates perception, planning, and control functionalities, facilitating the seamless deployment of various algorithms. Several of our projects leverage this framework, spanning quadruped robot navigation, formation control, collaboration, and flocking.</p>
</div>

### [chigui: A novel Spherical Robot Drive by Barycenter Offset and Conservation of Angular Momentum](/posts/Robotchigui)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p> <img class="left" src="/images/ballbot/chigui.bmp" width="200px" alt="chigui" /> The spherical robot chigui integrates the drive principles of Barycenter Offset (BCO) and Conservation of Angular Momentum (COAM), propelled by three motors with two reaction wheels. Employing the Euler-Lagrange system dynamics model based on the d’Alembert principle, we analyze the robot's motion behavior and introduce three basic robot motions to simplify the dynamics model and derive equations for external torque input motion. We design a cascade controller for the robot's basic motion and establish a ROS-Gazebo physical simulation platform for algorithm testing. Additionally, we assemble mechanical structures, develop a hardware control system, and author embedded real-time control code for experimentation.</p>
</div>

### [Wheeled Robot for RoboMaster University Series Competition](/posts/RobotWheeled)
<div style="border: 0px solid #1182BF;padding: 4px;margin-top: -15px;">
    <p> <img class="left" src="/images/rm/hero2.jpg" width="200px" alt="hero"/> The RoboMaster University Series (RMU) is a platform for robotic competitions and academic exchange, specially designed for global technology enthusiasts. It requires participants to go beyond their textbooks to form robotics teams, develop a diverse fleet of robots, and participate in team battles. I participated RMU2021 with my teammates as leader of the Electric Control Group. We design schemes, make circuit boards, and debug embedded programs. We tirelessly tested and optimized our robots, and endured countless sleepless nights. It' a memorable and cherished time.</p>
</div>


---
<div style="text-align: center">
    <a href="https://m.maploco.com/details/71f666nh"><img style="border:0px;" src="https://www.maploco.com/vmap/10366253.png" alt="Locations of Site Visitors" title="Locations of Site Visitors"/></a>  
</div>