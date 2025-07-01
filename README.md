Sure! Here’s a comprehensive and professional README.md file based on the information you’ve provided, tailored for a GitHub project repository:

⸻

APC Propeller Dataset and Geometry-Performance Mapping

Overview

This project focuses on processing and analyzing the APC Propellers dataset from APC Propellers - Performance Data, which provides geometry (.peo) and performance (.dat) data for a wide range of propellers. The overarching goal is to link geometric features with aerodynamic performance to design optimal amphibian propellers using machine learning and data-driven approaches.

⸻

Objectives
	•	Convert .peo geometry files to .stl mesh files suitable for 3D learning.
	•	Associate .stl geometry with corresponding .dat performance files.
	•	Train geometric deep learning models (specifically DGCNN) to predict or optimize performance.
	•	Develop a streamlined approach to handle missing hub geometries.
	•	Enable a scalable and accurate method for optimal propeller design.

⸻

Dataset Description

1. Geometry Files
	•	Format: .peo (APC Propeller proprietary format)
	•	Contains 3D information of blade geometry only (no hub).

Conversion Process:
	1.	.peo → .bem Conversion
Using Julia script from APC2BEM GitHub Repository.

# Run from within Julia
julia convert_peo_to_bem.jl <input.peo>


	2.	.bem → .stl Conversion
Use OpenVSP (Open Vehicle Sketch Pad) to import .bem and export .stl.
⚠️ Note: Only the blade geometry is present in the .stl. The hub must be manually designed and attached, which is time-consuming and error-prone. Automating or simplifying this step is a current challenge and priority.

2. Performance Files
	•	Format: .dat
	•	Contains tabular performance data:
	•	Thrust coefficient (Ct)
	•	Power coefficient (Cp)
	•	Efficiency
	•	RPM, Airspeed, Pitch Angle, etc.

⸻

Model Architecture

We apply DGCNN (Dynamic Graph Convolutional Neural Network) for point cloud learning on 3D propeller geometry.

What is DGCNN?

DGCNN is a neural network architecture tailored for point cloud data. Unlike traditional CNNs, it dynamically constructs a graph of nearest neighbors at each layer, capturing local geometric features effectively.
	•	Citation:
Wang, Yue, et al. “Dynamic graph CNN for learning on point clouds.” ACM Transactions on Graphics (TOG) 38.5 (2019): 1–12.
[Paper Link (arXiv)]

⸻

Current Progress
	•	✅ Converted and trained DGCNN on first propeller .stl file — achieved 100% training accuracy.
	•	⚠️ On two additional files, overfitting occurred due to small dataset size and high model capacity.
	•	🔄 Currently working on linking .stl geometries to their corresponding .dat performance data.
	•	🛠️ Looking into automating or templating hub geometry creation.

⸻

Challenges
	•	Manual Hub Modeling: Hub geometries are missing from .peo files and must be manually modeled in OpenVSP or CAD tools. This is a bottleneck for scaling up.
	•	Small Dataset: With limited number of propeller samples, generalization of the DGCNN model is currently poor.
	•	Linking Data: Matching each .stl file to the correct .dat file reliably is an ongoing data preprocessing effort.

⸻

Future Work
	•	🔧 Develop or adopt a tool for automatic hub generation and attachment.
	•	📈 Increase dataset size via:
	•	Collecting more .peo and .dat files
	•	Data augmentation on .stl meshes
	•	🤖 Improve model generalization using:
	•	Transfer learning
	•	Regularization techniques
	•	Data normalization
	•	🔍 Analyze relationships between geometry features and performance metrics to generate design rules.

⸻

How to Run

Environment:
	•	Julia (for .peo to .bem conversion)
	•	OpenVSP (for .bem to .stl export)
	•	Python (for DGCNN training and evaluation)
	•	Recommended: Python 3.8+, PyTorch ≥1.11

Steps:
	1.	Convert .peo to .stl (see above).
	2.	Preprocess .stl into point cloud format.
	3.	Train DGCNN:

python train.py --data path_to_point_clouds --labels performance_labels.csv


	4.	Evaluate or visualize:

python evaluate.py



⸻

Repository Structure

.
├── data/
│   ├── raw/
│   │   ├── *.peo
│   │   ├── *.dat
│   ├── processed/
│   │   ├── *.stl
│   │   ├── *.pcd / *.npy
├── models/
│   └── dgcnn/
├── scripts/
│   ├── convert_peo_to_bem.jl
│   ├── stl_to_pointcloud.py
├── notebooks/
│   └── data_analysis.ipynb
├── README.md
└── requirements.txt


⸻

References
	•	APC Propeller Technical Data
	•	APC2BEM – Julia Conversion Code
	•	OpenVSP - NASA
	•	Wang, Y., Sun, Y., Liu, Z., Sarma, S. E., Bronstein, M. M., & Solomon, J. M. (2019). Dynamic graph CNN for learning on point clouds. ACM TOG. arXiv:1801.07829

⸻

Contact

For questions or collaboration, please contact:

[Your Name]
Email: [your-email@example.com]
GitHub: [your-github-profile]

⸻

Let me know if you’d like a badge section, license, or auto-install script too.
