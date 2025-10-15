**Java Web Calculator Deployment Guide with Maven & Nexus**

This repository demonstrates how to build, deploy, and manage Java web application artifacts using Maven, Nexus Repository Manager, and Apache Tomcat. The project used here is a Java Web Calculator, and multiple versions of the application are deployed step-by-step.

**1. Create an Instance**

Create a server instance ( AWS EC2, Azure VM, or local VM). Choose Ubuntu as the OS and configure ports.

<img width="1918" height="878" alt="Image" src="https://github.com/user-attachments/assets/c79a626f-8176-4309-802e-4ad14ada9029" /> <img width="1918" height="860" alt="Image" src="https://github.com/user-attachments/assets/ca737fba-c047-419a-8dac-fa5cc1332a39" /> <img width="1918" height="866" alt="Image" src="https://github.com/user-attachments/assets/da059aee-3d8a-44a1-afde-6994b8f84046" /> <img width="1918" height="863" alt="Image" src="https://github.com/user-attachments/assets/213630e8-5584-4e49-a123-2c28a21806c9" />

 A dedicated instance ensures isolation for building and deploying applications and prevents conflicts with other environments.

**2. Connect to Terminal**

Connect to your instance using SSH:

ssh -i <keyfile.pem> ubuntu@<server-ip>

<img width="1491" height="767" alt="Image" src="https://github.com/user-attachments/assets/77f0ea5f-bc32-44be-b8a5-f8b6fb6c207c" />

 SSH provides secure remote access to your server.

**3. Install Java and Maven**

Update packages and install required software:

sudo apt update
sudo apt install openjdk-11-jdk maven -y
java -version
mvn -version

<img width="1487" height="756" alt="Image" src="https://github.com/user-attachments/assets/2319d281-2f3f-41cb-a471-7b7aeef77d83" /> <img width="1478" height="757" alt="Image" src="https://github.com/user-attachments/assets/07823680-2658-42bc-ba71-af2c9d5c1ae5" />

**Explanation:**

Java JDK is required to compile and run Java applications.

Maven is a build automation and dependency management tool.

**4. Clone Project Repository**

Clone your project using Git:

git clone <repo-url>
cd <project-folder>

<img width="1912" height="901" alt="Image" src="https://github.com/user-attachments/assets/75eef82d-ec9b-4a68-b76d-4075cafa8293" />

Clone to the terminal:

<img width="1473" height="760" alt="Image" src="https://github.com/user-attachments/assets/67942766-773d-4479-b642-e92ef8995397" /> <img width="1482" height="756" alt="Image" src="https://github.com/user-attachments/assets/bbe0ba21-0ea2-4a91-aa56-5218ed64e6f2" />

 Git ensures version control and allows easy updates from the central repository.

**5. Validate and Clean Project**
mvn validate
mvn clean

<img width="1486" height="767" alt="Image" src="https://github.com/user-attachments/assets/9e0ee9a4-9f4e-41b9-a9ba-0af616d99f4f" /> <img width="1481" height="762" alt="Image" src="https://github.com/user-attachments/assets/0cc76c47-0564-47dc-a43d-b922b4c9dfbf" />

**Explanation:**

mvn validate checks the project structure and dependencies.

mvn clean removes previous builds to avoid conflicts.

**6. Check the Artifact**

After building, your WAR file is generated in the target folder:

<img width="1482" height="757" alt="Image" src="https://github.com/user-attachments/assets/04e52a13-9a2a-4993-956c-f899efa5582a" />

WAR files package the application for deployment in Tomcat.

**7. Create Nexus Server**

Create a server instance for Nexus Repository Manager on port 8081. Connect via SSH:

<img width="1918" height="865" alt="Image" src="https://github.com/user-attachments/assets/0fcf4762-8e08-4000-acbc-737c71e0eef8" /> <img width="1918" height="872" alt="Image" src="https://github.com/user-attachments/assets/5e5278c1-f601-4017-afc1-3db9e39ac690" /> <img width="1918" height="878" alt="Image" src="https://github.com/user-attachments/assets/cdd45c90-0ca6-4a17-9a01-57e150bb8bbe" />

Connect SSH to terminal:

<img width="1485" height="757" alt="Image" src="https://github.com/user-attachments/assets/b8ca9596-8bae-483f-a406-d05e51c06088" />

**8. Install Java on Nexus Server**

sudo apt update
sudo apt install openjdk-11-jdk -y
java -version

<img width="1482" height="761" alt="Image" src="https://github.com/user-attachments/assets/0e03134e-3e94-48a9-ae6b-a396fb657d80" />

 Nexus also requires Java to run.

**9. Install Nexus Repository Manager**

Copy the download link from the Sonatype website and use wget:

<img width="1487" height="922" alt="Image" src="https://github.com/user-attachments/assets/429d4e52-f98e-474f-96e6-2c93a4eae3c8" />
wget <nexus-download-link>

<img width="1478" height="758" alt="Image" src="https://github.com/user-attachments/assets/fd525c22-014f-4e54-aa31-d5e78f83b75c" />

Nexus Repository Manager is required to store Maven artifacts centrally.

**10. Extract Nexus Files**

tar -xvf <nexus-file>.tar.gz

<img width="1470" height="761" alt="Image" src="https://github.com/user-attachments/assets/cff971cb-7c60-423c-ab17-a83d85f48cff" /> <img width="1481" height="755" alt="Image" src="https://github.com/user-attachments/assets/b139b1c9-3cd3-4c98-83f5-91784166f165" />

**11. Verify Nexus is Running**

Install net-tools to check the port:

sudo apt install net-tools -y
netstat -tulnp | grep 8081

<img width="1491" height="747" alt="Image" src="https://github.com/user-attachments/assets/63db743a-0c8d-4b78-85f6-30f156f88fee" />

Check logs:

cd ~/sonatype-work/nexus3/log
tail -f nexus.log

<img width="1475" height="762" alt="Image" src="https://github.com/user-attachments/assets/d4284528-467a-4bf8-8e18-e3520454c2e9" />

Open browser: http://<server-ip>:8081

<img width="1918" height="1027" alt="Image" src="https://github.com/user-attachments/assets/1b6f7340-4ef0-40f4-85a3-ff15d4e1249a" />

Login Credentials:

cat ~/sonatype-work/nexus3/admin.password

<img width="1918" height="1032" alt="Image" src="https://github.com/user-attachments/assets/81caa75f-9385-4310-b36b-778e83eb2dd1" /> <img width="1500" height="767" alt="Image" src="https://github.com/user-attachments/assets/21cc3503-6434-4359-80f2-03f46b5863cf" />

**12. Create Nexus Repository**

Go to Settings → Repositories → Create repository → Maven 2 (hosted)

<img width="1918" height="980" alt="Image" src="https://github.com/user-attachments/assets/21708caa-6ebb-422c-89bc-bc14b006056a" /> <img width="1918" height="971" alt="Image" src="https://github.com/user-attachments/assets/29fd5190-d69d-4fc0-8e1b-84756be1b4d2" /> <img width="1911" height="975" alt="Image" src="https://github.com/user-attachments/assets/ccfda658-7ce5-435f-8ec8-722648462c08" />

**13. Build the First Function (Addition)**

Go to the build server and implement the first function (addition) in index.html.

<img width="1470" height="435" alt="Image" src="https://github.com/user-attachments/assets/6909c53f-fb43-4418-9b2f-f6aad8699dfd" /> <img width="1482" height="772" alt="Image" src="https://github.com/user-attachments/assets/2d586e22-4d36-4ab3-9de9-d154a7be8ecf" />

Each function in the web application represents a new versioned feature. Addition is version 0.0.1.

**14. Update pom.xml**

Edit pom.xml to define:

version

artifactId

groupId

packaging (war)

Nexus repository URL and credentials

<img width="1483" height="745" alt="Image" src="https://github.com/user-attachments/assets/220d1755-f816-4ee9-8a54-f3e699739ff1" /> <img width="1477" height="747" alt="Image" src="https://github.com/user-attachments/assets/a59ccf8b-a227-4e05-9d66-2f94a7efc678" />

**Explanation:** This connects Maven to Nexus, allowing automatic artifact deployment.

**15. Update Maven settings.xml**

The settings.xml file is usually located at /etc/maven/settings.xml or ~/.m2/settings.xml. Add your Nexus repository credentials:

<img width="1489" height="745" alt="Image" src="https://github.com/user-attachments/assets/9631074f-144f-4506-b12e-e9811a3764b2" /> <img width="1476" height="367" alt="Image" src="https://github.com/user-attachments/assets/ce9b26e3-ea09-4873-b4f4-20c4c71a3f10" />

**16. Validate, Package, and Deploy Artifact**

Run Maven commands:

mvn validate
mvn package
mvn deploy

<img width="1097" height="436" alt="Image" src="https://github.com/user-attachments/assets/3d2974fb-428d-418c-bdc5-f4a94b97f05b" /> <img width="1477" height="387" alt="Image" src="https://github.com/user-attachments/assets/7457bdb9-1401-41ee-a214-d38fa4a1f2fe" /> <img width="1500" height="747" alt="Image" src="https://github.com/user-attachments/assets/bbfe6a2e-e52d-47e1-9d56-283b723471c4" />

 This builds the WAR file and deploys it to Nexus automatically.

**17. Verify Artifact in Nexus**

Refresh the Nexus repository and browse to your newly created repository. Check for your artifact 0.0.1.

<img width="1918" height="600" alt="Image" src="https://github.com/user-attachments/assets/2762c37c-e68c-4fad-a8fc-a57a6253cea5" />

**18. Copy Artifact URL**

Click on the version 0.0.1, locate the WAR file, and copy its download URL from the right-hand corner.

<img width="1918" height="977" alt="Image" src="https://github.com/user-attachments/assets/a79f6f00-2bba-41aa-9fea-c392a2b1c8a4" />

**19. Deploy Artifact to Deploy Server**

On the deploy server, download the artifact using wget or curl:

wget --user=<username> --password=<password> <artifact-url>

<img width="1918" height="977" alt="Image" src="https://github.com/user-attachments/assets/0b982146-696d-4fe0-a685-af256c80bf50" /> <img width="1507" height="537" alt="Image" src="https://github.com/user-attachments/assets/da802222-0dc1-47f2-a5d3-e4807ea39c12" />

Move the WAR file to Tomcat webapps:

mv webapp-0.0.1.war ~/apache-tomcat-9.0.111/webapps/

<img width="1515" height="293" alt="Image" src="https://github.com/user-attachments/assets/0ef20a10-3c43-411e-890e-a4f11b51af5c" />

**20. Configure Tomcat**

If you encounter 403 Forbidden, edit:

context.xml – Remove or update restricted lines

<img width="1517" height="761" alt="Image" src="https://github.com/user-attachments/assets/e3d39dd2-0188-4384-b579-55316773c633" />

tomcat-users.xml – Add user credentials for manager access

<img width="1510" height="766" alt="Image" src="https://github.com/user-attachments/assets/df67266d-2fa9-4e7f-8ab0-68a9fe1e19e0" />

**21. Verify Deployment**

Refresh Tomcat manager. You should see your deployed application version 0.0.1.

<img width="1918" height="911" alt="Image" src="https://github.com/user-attachments/assets/5a7e75a4-3b80-449f-87a0-8f5cb894e90a" />

**22. Test Application Output**

Test the addition function in your browser.

<img width="1051" height="477" alt="Image" src="https://github.com/user-attachments/assets/accb725a-4f15-4df6-882b-7eb29f698d94" />

**23. Build Second Function (Subtraction)**

Add subtraction functionality in index.html. Update pom.xml and settings.xml with version 0.0.2.

<img width="1502" height="757" alt="Image" src="https://github.com/user-attachments/assets/9ed8bd9c-c772-42ed-b887-772a4388d8bc" /> <img width="1507" height="322" alt="Image" src="https://github.com/user-attachments/assets/53dd1a6d-1543-4ac1-9086-2d59c746f28d" />

**24. Validate, Package, Deploy Version 2**

mvn validate
mvn package
mvn deploy

<img width="1502" height="756" alt="Image" src="https://github.com/user-attachments/assets/d18dd432-09be-497a-b149-4bf00626bb59" />

**25. Verify Version 2 in Nexus**

Refresh repository. The second version (0.0.2) appears.

<img width="1918" height="532" alt="Image" src="https://github.com/user-attachments/assets/f8a96484-1167-4ad3-8c4c-cf630c9ea867" />

Copy the artifact URL and deploy to deploy server.

<img width="1918" height="980" alt="Image" src="https://github.com/user-attachments/assets/7db18a0f-87f7-4b13-abf4-8b4eaf161edf" /> <img width="1501" height="752" alt="Image" src="https://github.com/user-attachments/assets/e5e21573-9386-4914-90cc-f58fc22ed149" />

**26. Build Version 3 (Multiplication)**

Add multiplication function in index.html. Update pom.xml to version 0.0.3. Validate, package, and deploy.

<img width="1506" height="768" alt="Image" src="https://github.com/user-attachments/assets/cd0e1dc2-38e3-4ffe-b24b-09ff0dbc694d" /> <img width="662" height="126" alt="Image" src="https://github.com/user-attachments/assets/ef515dcf-0f7c-4c49-b8d4-df93fd9a5b67" />
 <img width="1506" height="747" alt="Image" src="https://github.com/user-attachments/assets/22746412-5a88-4d16-b185-f30c66660325" />

**27. Deploy Version 3 & Verify**

Download version 3 artifact from Nexus, move to webapps, and refresh Tomcat. Test multiplication functionality.

<img width="1513" height="757" alt="Image" src="https://github.com/user-attachments/assets/029fa372-62ce-4f8f-9828-a3a6974f31c0" /> <img width="1918" height="907" alt="Image" src="https://github.com/user-attachments/assets/d94fd005-acd6-43b0-acd4-6878d7e31e96" /> <img width="1918" height="970" alt="Image" src="https://github.com/user-attachments/assets/510f1577-67bf-4b7b-af6e-55870afd02f5" />

**Conclusion:**

Each function corresponds to a new artifact version in Nexus.
Nexus acts as a central repository for storing Maven artifacts.
Tomcat deploys WAR files to the end-users.

This workflow allows versioned, controlled, and repeatable deployments.
