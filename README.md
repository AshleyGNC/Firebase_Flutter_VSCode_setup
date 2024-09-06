# Firebase_Flutter_VSCode_setup
Setting up the firebase connection to an existing flutter project in vscode.


1. Prepare workspace

       a. Install the Firebase CLI and log in (You should be able to do it with your email)
   
2. Install and run the FlutterFire CLI

       a. From any directory run this command: dart pub global activate flutterfire_cli
		   b. If you get this warning fix it by adding to your path. 
      		
  	    Building package executables... (8.2s)
		    Built flutterfire_cli:flutterfire.
		    Installed executable flutterfire.
		    Warning: Pub installs executables into C:\Users\Ashley\AppData\Local\Pub\Cache\bin, which is not on your path.
		    You can fix that by adding that directory to your system's "Path" environment variable.
		    A web search for "configure windows path" will show you how.
		    Activated flutterfire_cli 1.0.0.


		c. Run npm install -g firebase-tools
		d. In your root directory for your flutter project run: flutterfire configure --project=mavtech-36382
			Select Platforms for your project. In our case we deselect ios, macos, and windows. As our app will work solely on andorid and web. It should look like this once you're done:
			
			C:\Users\Ashley\Documents\FlutterProjects\MAV_Tech>flutterfire configure --project=mavtech-36382
			✔ Generated FirebaseOptions file C:\Users\Ashley\Documents\FlutterProjects\MAV_Tech\lib\firebase_options.dart already exists, do you want to override it? · yes
			i Found 4 Firebase projects. Selecting project mavtech-36382.
			✔ Which platforms should your configuration support (use arrow keys & space to select)? · android, web
			i Firebase android app com.example.mav_tech is not registered on Firebase project mavtech-36382.
			i Registered a new Firebase android app on Firebase project mavtech-36382.
			i Firebase web app mav_tech (web) registered.
			
			Firebase configuration file lib\firebase_options.dart generated successfully with the following Firebase apps:
			
			Platform  Firebase App Id
			web       1:773487790727:web:53e7e02046253a05938622
			android   1:773487790727:android:6411ffa9efacf361938622
			
			Learn more about using this file and next steps from the documentation:
			 > https://firebase.google.com/docs/flutter/setup
			
			
			
			
			
			This automatically registers your per-platform apps with Firebase and adds a lib/firebase_options.dart configuration file to your Flutter project.
			
	3. Initialize Firebase and add plugins

            a. In the command line type firebase_options.dart file in your directory. This file will have some errors but they will be fixed with the following step

             i. In the pubspec.yaml file add under 'dependencies:'
			
			        firebase_core: ^3.4.0 //latest version as of 2024
			
			ii. Save file
			
		       b. In the main.dart file add:
			
			import 'package:firebase_core/firebase_core.dart';
			import 'firebase_options.dart';
			
			void main() async {
			  await Firebase.initializeApp(
			    options: DefaultFirebaseOptions.currentPlatform);
			  runApp(const MyApp());
			}
		
	
