# Image-Annotation-Procedure

How Annotation works
=======================================
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
