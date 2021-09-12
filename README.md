# Interview Task 

Excel document containing all defined documentation: ([Assumptions Scripts and Stories.xlsx](https://github.com/Jacob130000x/Interview/files/7150229/Assumptions.Scripts.and.Stories.xlsx)
)

### Task define the test documentation for a door with a fingerprint lock</h3>

**You may choose any type you think is necessary (BDD, TestCases/Testplan, Checklist etc.).**

1) BDD would **not** be useful here as the best way to test this would be a manual way due to the fact that a physical device is being tested.
2) Test cases will be used and shown below
3) As in Agile documentation is kept to the minimum, the stories should be small enough and be part of all the 'Features' and 'Epics'. They should have all the required information to replace the traditional **Test Plans** to outline the scope and risks.
4) Checklists could be part of the story as tasks to show progress and increased transparency.


As I would personally go with the Agile approach please see the below: 
I would first start with refining the story to make sure it meets the definition of ready proposed by the whole team. The story would have the Title, Description and Acceptance result. Later on tasks can be added to track the scenarios that are being tested. The stories would be stored on a Kanband board in either Jira or Azure DevOps board.

## Story	001 Fingerprint Door Lock
### Description
"**As a** Security manager 
**I want** the fingerprint door lock to open only for the user's with pre-recorded fingerprints
**So that** I can maintain the right level of security 

**Scope:**
Testing of the functionality of the fingeprint lock itself - **in scope**
The fingerprint lock can only be opened by a fingerprint or directly from the office - **not in scope of the testing**
Heartbeat check that the device is up and running - **not in scope of the testing**
"
**Sizing**	XS (t- shirt sizing from extra small XS to XL)
### Acceptance Criteria
"Door Lock unlocks when a fingerprint is in the database for the user 
Door lock remain locked when incorrect fingerprint is scanned in
Door lock indicates when it is locked and unlocked
Door can be opened from the inside
Multiple users and fingerprints can be used to access the door 
"
	
### Tasks	
1	Pull The handle to see if the door is locked
2	Use a finger available in the database to open the locked door
3	Use a finger not available in the database to open the locked door
4	Record multiple finger prints to the same account and see if the
 fingers open the door
5	Volume and performance test the amount of fingers that can be
 recorded at the same time to the agreed amount of 10

## Test Scripts

I have come up with some **assumptions** to make sure that the test scripts abide by some predefined rules, please see the assumptions below:

### Assumptions made:
* Each person has an account linked to the door 
* The fingerprints are recorded in a different location
* This fingerprint lock's vendor states the lock is certified to be very accurate 
* This fingerprints lock's vendor states that 999 fingerprints can be stored ( agreed needed amount is 5, 10 for testing if needed in the future)
* Only the fingerprint lock is being tested and not the recording device
* The fingerprint lock is only on one side of the door, can be opened by pulling the handle from the inside
* Fingerprint lock times out within 5 seconds once unlocked
* The fingerprint lock can only be opened by a fingerprint or directly from the office ( not in scope of the testing)
* Only Black box testing is performed as the internal workings of the lock are unknown
* The fingerprint lock has a pulse and heat detectors for increased security, unable to be tricked by images of the finger
* There is a power generator in place in case of a power cut
* Heartbeat check that the device is alive could be tested
* All users in the database have access to this padlock. E.g it is a door to a laboratory 

## Scenarios
I have come up with certain scenarios before writing the test scripts as shown below:

### Scenarios:
1.	Pull The handle to see if the door is locked
2.	Use a finger available in the database to open the locked door
3.	Use a finger not available in the database to open the locked door
4.	Record multiple finger prints to the same account and see if the fingers open the door
5.	Volume and performance test the amount of fingers that can be recorded at the same time to the agreed amount of 10


## Scripts

Please see the whole document attached ([Assumptions Scripts and Stories.xlsx](https://github.com/Jacob130000x/Interview/files/7150230/Assumptions.Scripts.and.Stories.xlsx)
)
showing the Story, Scenarios, Assumptions, Test Scripts, Smoke and Regression Pack. The scripts are fully written with Prerequisites, Descriptions, Steps and Expected Results. The scripts should be stored in a central location. This could be stored in ALM or even in sharepoint as long as they are being maintained.
I have added priority to the test scripts from 1 to 3 (1 being a must test) in order to know when looking back at the scripts which ones must be run and which tests can be run if there is a sufficient time left. 

**Here is the list of the Scripts:**
note: SR stands for scenarios and TS for Test Script e.g. SR001.TS001 relates to Scenario 1 and it is the fist script on the list. 

* SR000.TS000 - Pre-requisite test case: Validating user's fingerprint in the database
* SR001.TS001 - Opening the Door
* SR002.TS002 - Access to the door
* SR002.TS003 - Door Locks after it is shut
* SR002.TS004 - Door opens from the inside
* SR002.TS005 - After Door is opened, unlock timeout
* SR003.TS006 - Accessing the door with an incorrect fingerprint
* SR003.TS007 - Accessing the door with an incorrect fingerprint, then using the correct finger
* SR004.TS008 - Using multiple fingers
* SR004.TS009 - Scanning in the fingers of multiple users
* SR005.TS010 - 10 Users able to access the door

There could be more stories written if the scope was increased or if more stories regarding different/integrating areas were written. The above tests solely focused on the functionality of the Fingerprint Lock. 

## After defining documentation, please define the Smoke/Sanity/Regression scopes for testing.

As **Smoke Testing** focuses on the most important areas of configuration, in this case they cover a large portion of all the test scripts due to the story being defined as quite small and the fact that it is vital for safety to cover off this functionality. I have chosen the below for it:


* SR000.TS000 - Pre-requisite test case: Validating user's fingerprint in the database  - It is vital important to check that the users have access to the doors in the database
* SR001.TS001 - Attempting Open the Door without scanning the fingerprint 		- Checking that the doors remain locked if the 
* SR002.TS002 - Access to the door							- Checking that the doors open if correct fingerprint is scanned
* SR002.TS003 - Door Locks after it is shut						- Checking for safety that noone can access the door again once it is shut, vital for safety
* SR002.TS004 - Door opens from the inside						- Make sure once someone is inside they can leave
* SR003.TS006 - Accessing the door with an incorrect fingerprint			- Make sure that anyone with without the access cannot gain access to the room
* SR004.TS009 - Scanning in the fingers of multiple users				- Making sure multiple users can access the room

**Sanity Testing** doesn't usually need to be documented or scripted as it is a quick check making sure that the part of the system is still there and is potentially working.
if I wanted to document it I would choose these three as the most important once in the case of the sanity regression testing:

* SR002.TS002 - Access to the door							- Checking that the doors open if correct fingerprint is scanned
* SR001.TS001 - Attempting Open the Door without scanning the fingerprint 		- Checking that the doors remain locked if the 
* SR003.TS006 - Accessing the door with an incorrect fingerprint			- Make sure that anyone with without the access cannot gain access to the room


**Regression Testing** as the fingerprint lock's has vital functionality as it used to protect unauthorised personnel  from accessing a room and also may be securing information or goods of high value therefore all the testing should be done as the regression if it is thought that the new changes may have an effect on the lock. As a minimum I would suggest to go with the smoke testing suite as it covers off the main areas whilst still keeping the number of test scripts low.

* SR000.TS000 - Pre-requisite test case: Validating user's fingerprint in the database  - It is vital important to check that the users have access to the doors in the database
* SR001.TS001 - Attempting Open the Door without scanning the fingerprint 		- Checking that the doors remain locked if the 
* SR002.TS002 - Access to the door							- Checking that the doors open if correct fingerprint is scanned
* SR002.TS003 - Door Locks after it is shut						- Checking for safety that noone can access the door again once it is shut, vital for safety
* SR002.TS004 - Door opens from the inside						- Make sure once someone is inside they can leave
* SR003.TS006 - Accessing the door with an incorrect fingerprint			- Make sure that anyone with without the access cannot gain access to the room
* SR004.TS009 - Scanning in the fingers of multiple users				- Making sure multiple users can access the room
