# PerformanceTesting_Restful-Booker
This is my first Performance Testing project using JMeter on [Restful-Booker](http://restful-booker.herokuapp.com/), which is an API testing site. 
As I was already familiar with the site APIs and their functionalities, I chose this site to do the performance testing for convenience. 
I have done Load Testing, Endurance Testing, and Stress Testing as part of this project to learn more about different types of Performance Testing. 
The following report is on how I conducted the performance testing using JMeter.

## API Collection
For testing, a set of APIs for [Restful-Booker](http://restful-booker.herokuapp.com/) covering different HTTP methods such as GET, POST, PUT, and DELETE are used in JMeter.
Data and tokens are created, called, and then updated and deleted using the created tokens, all inside this set of APIs for the test coverage.

![TestPlan](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/8db9f81f-de42-4be3-b2e6-2d82cddbc0c8)

After Collecting APIs and adding HTTP requests, the Thread Group was tweaked using different values for the Number of Threads, Ramp-up period, and Loop Count, and the Test Plan was saved as a JMX file.


![APIs](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/b5d0d24b-e3d4-4ec8-9d5f-84de0d02bece)

The JMX file was then used in Command Prompt to run the test and create a JTL file. 

Command to run the JMX file for testing and creating the JTL file: **_jmeter -n -t TestPlan.jmx -l TestPlan.jtl_**

Finally, the JTL file was used to generate a test report.

Command to run the JTL file and create an HTML report file: **_jmeter -g TestPlan.jtl -o TestPlan_6000.html_**


![TestReport](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/b8a2e20a-7d48-4183-b27a-7d491a032902)

## Load Testing
Load testing involves assessing how a system performs under expected loads. For finding the maximum load capacity of [Restful-Booker](http://restful-booker.herokuapp.com/) when requesting a collection of APIs, Thread Groups of 4680, 4690. 4695, and 4700 threads are used. 
For all Thread Groups, the Ramp-up period is set to 10s with a loop count of 1.

### First Thread Group
Number of Threads 4680, Ramp-up period 10s, loop count of 1:
| Summary Report | Errors |
| ------------- | ------------- |
|  ![4680_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/397e7646-7d5c-4911-b08f-a5cfc19406f5) |![4680_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/f8481f53-435c-4447-80ba-42467a3265aa)|

### Second Thread Group
Number of Threads 4690, Ramp-up period 10s, loop count of 1:
| Summary Report | Errors |
| ------------- | ------------- |
|![4690_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/7842cfbe-e7ce-49f2-86cc-5126933a2c09) |![4690_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/40ed3a4d-dea8-4b50-9add-3e2f41ec6f6e)|

### Third Thread Group
Number of Threads 4695, Ramp-up period 10s, loop count of 1:
| Summary Report | Errors |
| ------------- | ------------- |
|![4695_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/e5b3cc0e-85b2-426b-8b3a-76c6def85558) |![4695_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/0f3e4dbb-7d0f-4cca-9b9a-dab08d7dbbd9)|

### Fourth Thread Group
Number of Threads 4700, Ramp-up period 10s, loop count of 1:
| Summary Report | Errors |
| ------------- | ------------- |
|![4700_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/39c40fb6-6bba-4f73-883a-fc9354f90725) |![4700_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/cfc14094-6eaa-4c86-b15e-797d7224259c)|

### Summary of Load Testing
* The first thread group with 4680 has an error 0f 0.21%
* The second and third thread groups with 4690 and 4695 threads have no errors
* The fourth thread group with 4700 threads has an 8.89% error
Assuming a maximum of 1% error is acceptable for the website, it can be observed that the Load of [Restful-Booker](http://restful-booker.herokuapp.com/) is 4695 users.

## Endurance Testing
Endurance testing is testing where we test the system performance under certain load conditions over an extensive period. In this test plan, 4695 threads are used as Load, Loop count is 1 and the Ramp-up period is set to 600 seconds or 10 minutes. 
| Summary Report | Errors |
| ------------- | ------------- |
|![endurance_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/d8d6d444-b027-4eb5-8762-b3a4649dba88)|![endurance_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/ddad1bd2-646f-428b-8426-26031f4f6d73)|

### Summary of Endurance Testing
* Load: 4695 threads, Ramp-up period: 10 Minutes
* Error rate of 0.13%
The system can endure the load of 4695 users for 10 minutes without noticeable error.

## Stress Testing
Stress testing is a type of performance testing that evaluates how a system or application behaves and performs under extreme conditions. In this project, the system was tested with 6000 threads for stress testing. 
| Summary Report | Errors |
| ------------- | ------------- |
|![stress_summary](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/11f4297f-f3ab-4548-a696-837e1e64b005)|![stress_error](https://github.com/salekinraju/PerformanceTesting_Restful-Booker/assets/58147883/311a2d39-0573-4b19-953e-55467e104aa3)

### Summary of Stress Testing
* 6000 threads
* Error rate of 24.86%
The load of the system is 4695 users. When 6000 users are added to the system in a span of 10 seconds, the system fails with an error rate of 24.86%. But the system can recover fully from this condition and perform efficiently.

## Conclusion
The performance testing conducted on the [Restful-Booker](http://restful-booker.herokuapp.com/) website APIs provided valuable insights into the system's behavior and performance under various conditions. The results found from the test are:
* Load of the system: 4695 users
* The system can comfortably endure for 10 minutes within its load
* The system can be under stress with 6000 users where it fails but can fully recover
