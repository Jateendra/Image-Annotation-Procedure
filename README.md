# Image-Annotation-Procedure [ Manual ]

0 . Pre-requisites . From URL : https://tzutalin.github.io/labelImg/

	 - download last file : Windows_v1.8.0
	 - Unzip it , open "predefined_classes.txt" file under "Downloads\windows_v1.8.0\data" folder 
			- remove all contents & paste/write below
					nine
					ten
					jack
					queen
					king
					ace

1 . Go to "tfod\models\research\images\train" folder and copy randomly 4 .jpg image files 	

2 . Go back to "tfod\" folder create a new folder "SampleImages" & paste these 4 .jpg image files .	

3 . Go to "Downloads\windows_v1.8.0" folder and double click "labelImg.exe" file .

4 . In this tool , click "Open Dir" icon , select "tfod\SampleImages" folder .

		- The below are for sample purpose ( not need to do any action , for knowing purpose )
			- Click PascalVOC ( xml format ) , it shows  yolo
			- You click back yolo it shows PascalVOC
			- PascalVOC -> .xml format , yolo -> .txt format

5 . Click on "Create RectBox" and start annotating the cards with labels .

		- Click on "Save" ( .xml file will be created for the first image in the same folder ) 
		
		- Repeat the above step for all images and form .xml files .
		
		- **Try opening .xml file and go through them for understanding ( check depth  , bndbox , etc )
		
		
		
# Labelling and Annotation of Images [ Auto-Labelling ]
====================================
1 . github.com/Cartucho/OpenLabeling
	- Download code and extract it.
	- Copy .zip file and extracted folder to location : "C:\Users\Sasmitabhoi\Documents\DL_CV_NLP\Object_Detection\Project\Facemask_TFOD-2\OpenLabeling-master"
2 . Open cmd
    - cd C:\Users\Sasmitabhoi\Documents\DL_CV_NLP\Object_Detection\Project\Facemask_TFOD-2\OpenLabeling-master
	- pip install -r requirements.txt	
3 . Go to folder "C:\Users\Sasmitabhoi\Documents\DL_CV_NLP\Object_Detection\Project\Facemask_TFOD-2\OpenLabeling-master\main"
	- Delete  the content of "class_list.txt" file . Fill with below content .
		???
		with_mask
		without_mask
	
	- Remove images & videos from "input" folder . Put all your downloaded .jpg images .
		- Download images from "https://www.kaggle.com/omkargurav/face-mask-dataset" or 
		- Put them back  in "input" folder .

4 . cd main
	- pip install tensorflow
	- ** Check version of tensorflow
		- python
		- >>> import tensorflow as tf
		- >>> tf.__version__
			2.3.1 
		- >>> exit()

5 . ** Above works in tensorflow 1.X

6 . To make it work in tensorflow 2.X
	- Open "main_auto.py" in any editor
	- Do following changes :
	
		#sys.path.insert(0, "..")
		sys.path.insert(0, "../object_detection")
		
		#from object_detection.tf_object_detection import ObjectDetector
		from tf_object_detection import ObjectDetector
		
		# graph_model_path = "../object_detection/models/ssdlite_mobilenet_v2_coco_2018_05_09/frozen_inference_graph.pb"
		graph_model_path = "frozen_inference_graph.pb"
		
		#new_path = img_path.replace(INPUT_DIR, new_path, 1)
        new_path = os.path.join(new_path,os.path.basename(os.path.normpath(img_path)))
		
	-****Download frozen_inference_graph.pb by running below commands in google collab .
			!git clone https://github.com/tensorflow/models
			checkpoint_name = 'ssdlite_mobilenet_v2_coco_2018_05_09'
			!wget http://download.tensorflow.org/models/object_detection/{checkpoint_name}.tar.gz
			!tar -xf {checkpoint_name}.tar.gz
			
	- place "frozen_inference_graph.ph" under "OpenLabeling-master\main" folder			
	- delete "output" folder under "OpenLabeling-master\main"
	
7 . To make file "tf_object_detection.py" under "OpenLabeling-master\object_detection"  to work in tensorflow 2.X
	- Open "tf_object_detection.py" in any editor
	- Do the changes :	
	
8 . Edit file "config.ini" :

	OBJECT_SCORE_THRESHOLD = 0.3
	OBJECT_IDS = 1,2
	CUDA_VISIBLE_DEVICES = 0
	
9 . python main_auto.py -i input -o output -t 2	

10 . python main.py -t 2 ( To see annoted images . press d or a to see next or previous images )

For  Video :

11 . Remove the files/folders contents from "input" & "output" folders .

12 . Copy video to "input" folder .

13 . python main_auto.py -i input -o output -t 2



*** Can find the labelled data set under : medium.com/p/bec3390eda2d/edit
	github.com/techzizou/OpenLabeling/tree/master		
