We are partnering with the Work research group here at Vanderbilt’s Institute for Software Integrated Systems, as their research focuses around traffic and mobility. The goal of our project is to automate recording of the Tennessee Department of Transportation’s (TDOT) network of cameras so that researchers can have access to videos of traffic incidents to examine traffic patterns, observe how accidents impact traffic, and work to optimize traffic flow. The camera network in place is so vast that it would be functionally impossible to store recordings from every camera at all times, so we will specifically aim to record the aftermath of traffic incidents.

The following is an overview of all the files in our system and the function performed by each one:

email_downloader.py - this program monitors the email inbox for traffic alerts and then downloads the relevant emails to a txt file. It also manages the inbox by deleting previously downloaded emails, and ensuring that only the emails from authorized senders are downloaded as accident reports.

email_parser.py - this program first reformats the txt files of the traffic incident alerts into a standardized format. It then parses through the email to extract relevant information such as the GPS location of the accident, the description of the incident, and the time of the incident. It then passes the relevant information on to the camera locator and adds the current recording to the output log.

locate_camera_auto.py - this program locates the closest camera to the incident, given GPS coordinates. It outputs the name and m3u8 url of the camera to be turned on

locate_camera_manual.py - this program allows a user to manually input a mile marker and highway, and it outputs the name and m3u8 url of the camera to be turned on

camera_info.csv - contains the name, highway, mile marker, coordinates, and m3u8 url for each of the cameras in the network

video_recording_log.csv - contains an updated output log of all stored recordings on the device with identifying information

start_cameras.py - the stream recorder that activates storage of the camera live stream after being given the camera name and URL

camera_automation.py - ties together all the above programs so that once an email alert is received, a recording at the appropriate location is subsequently stored in a labeled folder and the log is simultaneously updated

tests.py - a file that contains all tests for each of the components mentioned above
