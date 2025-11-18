## Weekly Report
- This file contains a paragraph of 1000 Characters or more about the progress made by the student for each week. I am creating the place holder for it.

### Week 1 (Date: Sept 8 - 12)
This week, my primary focus was on foundational research and project scoping. Following a meeting with the Digital Twin team on Wednesday, I chose the project I will be working on for the duration of this research study: enhancing the scalability of the DTUMOS platform through multi-threaded programming. This project aims to address the limitations of the current DTUMOS architecture by investigating and implementing multiprocessing or compiled extensions to improve the performance and scalability of CPU-bound simulations. To build a strong knowledge base for this work, I conducted my literature review. I analyzed three key papers. The first, "DTUMOS, digital twin for large-scale urban mobility operating system," served as a direct reference, detailing the current architecture and scalability challenges I will be addressing. The second paper, "The path to medical superintelligence" by Microsoft AI, though in a different domain, provided insight into benchmarking large-scale AI systems, which will inform how I measure the performance gains of my solution. The third paper, "TransETA: transformer networks for estimated time of arrival with local congestion representation," was crucial for understanding deep learning models for complex traffic simulations and highlighted the importance of computational efficiency. In a subsequent meeting, Mr. Sehra directed me to focus my initial research on core concepts like parallel processing, Python programming for multi-threaded applications, and thread-level processing. These topics will form the basis of my next steps as I transition from research to practical implementation. My work this week has successfully established a clear project direction and a strong theoretical foundation.

### Week 2 (Date: Sept 15 - 19)
This week, I continued my foundational research, with a specific focus on the core technical concepts that will underpin my project. I conducted review and research on parallel processing and multi-threaded programming, delving into how these techniques can be applied to enhance the performance of CPU-bound simulations. I also expanded my literature review to include research on optimizing DTUMOS, with attention to Estimated Time of Arrival (ETA) models. My research this week has been crucial for building a strong theoretical framework before I transition to practical implementation and codebase analysis. The knowledge I've gained will directly inform my approach to optimizing DTUMOS for improved scalability.

### Week 3 (Date: Sept 22 - 26)
This week, I shifted my focus from a broad literature review to a more practical analysis of the project. My primary accomplishment was completing a thorough review of the DTUMOS codebase. This deep dive was critical for identifying potential areas for optimization and understanding the existing architecture's limitations. Concurrently, I continued to refine my research into optimization strategies, multi-threaded programming, and parallel processing. This dual-pronged approach of hands-on code analysis and theoretical research has provided me with a clear roadmap for the next phase of my project, allowing me to pinpoint specific sections of the code that can benefit from performance enhancements. My work this week has successfully bridged the gap between foundational knowledge and practical application.

### Week 4 (Date: Sept 29 - Oct 3)
This week was  productive, I focused on detailed codebase analysis and strategic planning for the optimization phase. I familiarized myself with the complete DTUMOS codebase and made significant progress in detailing the time complexity of its core files. By the end of the week, I only had one and a half files remaining for time analysis documentation, which I aim to complete today.

Key strategic developments occurred during our meetings:
- Wednesday Meeting: We discussed and decided to investigate specialized software tools capable of measuring the load and performance of various files and processes within the codebase. This will complement the static time complexity analysis with dynamic profiling data.
- Thursday Meeting: I received guidance from Dr. Jiho, who advised me to consider using Rust to rewrite specific performance-critical functions. This approach, alongside the planned implementation of multi-threading and parallel processing, will be a core strategy for achieving significant performance and scalability improvements in DTUMOS.

My work this week has solidified the technical direction of the project, moving from analysis into concrete optimization planning.

### Week 5 (Date: Oct 6 - 10)
This week marked the completion of the foundational static analysis and the transition to preparing for dynamic analysis. I successfully finished the time complexity analysis for the remaining files in the DTUMOS codebase and ensured the platform was fully set up to run on my system. Along with that, I began refamiliarizing myself with the fundamentals of Rust and best practices for parallel processing, following the guidance received last week.

During the Wednesday meeting, Dr. Sehra advised that a dynamic analysis of the system—specifically, measuring which functions are called and how often—would be an invaluable asset for precisely identifying performance bottlenecks. I dedicated the latter half of the week to designing and structuring the implementation plan for this dynamic profiling. This includes determining whether to go with a tool or a script I create that would outline the required code structure and capture runtime frequency and load data. By the end of the week, I had the first version of the analysis script ready to run a dynamic analysis of DTUMOS. This dynamic data will be crucial for validating my static analysis and directing the subsequent optimization efforts.

### Week 6 (Date: Oct 13 - 17)
This week, coinciding with the mid-semester break, was dedicated to refining the tools necessary for the upcoming dynamic analysis phase. I focused on revising the dynamic function count analysis script that I had designed the previous week. I aimed to ensure the script was robust and ready for deployment. However, I encountered a significant technical roadblock: my local machine proved to be too underpowered to run the DTUMOS simulation in any reasonable amount of time. This limitation prevents me from performing the crucial dynamic profiling on my current setup, necessitating a shift in the plan to utilize a more powerful resource (e.g., cloud computing or a dedicated lab machine) for the next phase of work.

### Week 7 (Date: Oct 20 - 24)

This week, I successfully completed a **static analysis** of the DTUMOS system architecture. Using specialized tools, I created an in-depth visualization of the codebase structure:

* **Dependency Graph Generation:** I generated module-to-module dependency graphs using three distinct tools—**Tach**, **PyReverse**, and **Pyan**—to ensure cross-validation and achieve a highly accurate and comprehensive understanding of the system's structural dependencies.
* **Function Flow Analysis:** I continued the static analysis by using **code2flow** to generate a graph that clearly outlines the control and data flow between functions within the DTUMOS system.

The result of this work is a very detailed and reliable set of visual assets that clearly map the entire DTUMOS architecture and its internal function calls. This **in-depth static analysis** directly supports the upcoming dynamic profiling phase by providing a clear structural reference point for identifying optimal functions and modules to target for parallel processing and optimization.

### Week 8 (Date: Oct 27 - 31)

This week delivered a significant breakthrough in performance optimization, fundamentally addressing a major scalability bottleneck in the DTUMOS platform.

Initially, I purchased a new machine with improved specifications to resolve the runtime issues encountered during dynamic profiling. Counterintuitively, the simulation ran **worse** on the new hardware. Through focused investigation, I identified the root cause: the substantial **HTTPS overhead** generated by the system's sequential requests to the **OSRM** (Open Source Routing Machine) API for distance and ETA calculations.

The solution involved a strategic architectural change: replacing the sequential OSRM calls with a **Matrix API** approach that handles all distance requests in a single batch.

* **Result:** This implementation led to a dramatic runtime improvement, reducing the simulation time by approximately **99%**. Runtimes that previously ranged from **129 to 220+ hours** were slashed down to a mere **2.21 seconds**. 
* **Next Steps:** While the performance gain is massive, some **bug fixing** is required. Specifically, I've observed abnormal behaviors concerning **idle vehicles** and **in-service vehicles** that need to be resolved to ensure the logistical correctness of the simulation despite the accelerated routing.

This successful transition to batch processing validates the project's optimization goals and sets the stage for resolving the remaining logical issues before final integration.

### Week 9 (Date: Nov 3 - 7)

This week was dedicated to **knowledge transfer and documentation** following the major OSRM optimization. I comprehensively updated my project **Wiki page**, ensuring all critical analytical data was cataloged and easily accessible. This documentation now includes all the artifacts from the static analysis phase, including the **Codebase Analysis Graphs** (Code2flow, Pyan-uses, Pyan-define, Pyan-full, and Pyreverse), alongside detailed notes on my initial **DTUMOS Runtime Optimization findings** regarding the OSRM batch call implementation. This work ensures that all foundational analysis and breakthrough optimization data are formally recorded.

### Week 10 (Date: Nov 10 - 14)

This week was dedicated to **debugging and validating** the significant performance optimization achieved through the OSRM Matrix API implementation.

I successfully implemented a **fix** that resolved the abnormal vehicle behaviors noted in the previous week, bringing the logistical behavior of the simulation into close alignment with the expected results, and specifically, the completion graph sent by Mubarrat.

* **Runtime Adjustment:** While this fix enhanced the logical correctness, it slightly increased the runtime of DTUMOS. The simulation time adjusted from **2 minutes and 21 seconds** to **5 minutes and 29 seconds**. This adjustment is considered acceptable, as it reflects the necessary computational steps for **accurate vehicle behavior** and prioritizes integrity over raw speed.

This work ensures the optimization is not only fast but also **logically sound** before moving into the final stages of the project.
