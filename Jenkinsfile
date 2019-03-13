node(''){
	stage('git'){
	checkout scm
	}
	stage('upload firmware'){
	try{
	bat 'python firmware_upgrade.py'
	}
	catch(err){
	echo "Firmware could not be uploaded "
	}
	stage('wait time'){
	sleep 120
	}
	try{
	stage('check for fimware update'){
	bat 'python fimrware_check.py'
	}
	stage('Setting up the Venv'){
	bat '''set https_proxy=http://165.225.104.32:80 // This part is optional,we can create a single python2.7 executable in the node 
 		pip install virtualenv						// The problem is that each dependencies have to manually updated 
		virtualenv myproj
		Scripts\\activate
		pip install selenium
		pip install pymodbus
		pip install pymodbustcp
		pip install pandas
		pip install styleframe
		pip install wxpython
		pip install win-inet-pton
		pip install opencv-python
		pip install python-appium-client
   		'''
   	stage('running the tests'){
   	dir(''){// basically with the directory with has the sanity test bench ready to run 
   		bat 'test_bench.py' // run the test bench code  
   	}
   	
   	}


	}
	}
	catch(err){
	echo" Firmware is not properly updated" 
	}

	}
}
