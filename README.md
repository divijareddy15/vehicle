# vehicle
•  You made changes to one file in the above project but haven't staged them yet. You realize they were a mistake. What Git command will you use to discard the local changes?
•	Command: git checkout -- <file-name> or git restore <file-name>
•  You made a commit but typed the wrong commit message. You haven't pushed it yet. How do you fix it?
•	Command: git commit --amend -m "your new message"
•  You want to view the commit history of the current branch in a readable format. What Git command should you use?
•	Command: git log --oneline or git log --oneline --graph
•  You're on the main branch. Create the branch Featuer/patient and switch to that branch. What commands do you use?
•	Command: git checkout -b Featuer/patient
•  You've made some commits locally and now want to upload them to the remote repository. What do you run?
•	Command: git push
•  You want to see all the branches that exist both locally and on the remote. How?
•	Command: git branch -a
•  Create a branch Suggestions and merge with patient branch, how can it be?
•	Commands:
1.	git checkout patient (to move to the patient branch)
2.	git merge Suggestions (to merge the Suggestions branch into patient)
•  How do you pull the latest changes from the remote repository and merge them into your local branch?
•	Command: git pull or git pull origin <branch-name>
•  Specify the git command when pushing for the first time and want to set the remote branch.
•	Command: git push -u origin <branch-name> or git push --set-upstream origin <branch-name>
•  You cloned a remote repository, but later you find that you need to push your changes to a different remote repository. How do you configure your local repository to push to this new remote?
•	Command: git remote set-url origin <new-remote-url>
•  After running git pull, you notice that your local branch is behind the remote branch. How would you proceed to bring your local branch up to date without losing your local changes?
•	Command: git pull (This is the correct command; Git is designed to merge changes automatically without losing your local work.)
•  You've pushed a patient branch to a remote repository, but now you need to delete the branch from the remote. How would you do that?
•	Command: git push origin --delete patient
•  How do you apply a .patch file provided by your teammate and include it in your commit history?
•	Commands:
1.	git apply <patch-file-name.patch>
2.	git add .
3.	git commit -m "Applied patch from teammate"











Based on the images provided, here are the questions and their answers, clearly broken down with simple explanations and commands.
________________________________________
Questions 1-6
1.	Download the given repository and show the list of the files?
o	Command: git clone https://github.com/KumbhamBhargavi75/HospitalMgmtSystem
o	Explanation: After this, you need to navigate into the new folder and list the files.
o	Command: cd HospitalMgmtSystem followed by ls (on Linux/macOS) or dir (on Windows).
2.	mvn CLEAN package, when I run this getting an unknown lifecycle phase error why?
o	Explanation: This error usually happens when there's a spelling mistake in the command or the Maven pom.xml file has an error. The command clean package is correct, but Maven cannot understand an unknown lifecycle phase if it is not a correct phase name. A common mistake is a typo, for example, packege instead of package.
3.	Add the dependency servlet-api of 2.5 to your project.
o	Answer: You need to add this dependency block inside the <dependencies> section of your pom.xml file.
o	Code:
XML
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>servlet-api</artifactId>
    <version>2.5</version>
</dependency>
4.	You try to build the project with JDK 21, but compilation fails. Why might this happen? How to fix in pom.xml?
o	Explanation: This happens because newer JDK versions (like JDK 21) have strict rules. The code in your project might be using features that are removed or changed in newer JDKs.
o	Fix: You need to tell Maven which Java version your project should use. You can do this by adding the maven-compiler-plugin to your pom.xml.
o	Code:
XML
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
        </plugin>
    </plugins>
</build>
	Note: Here, 1.8 is used as an example for Java 8, which is often a safe choice for older projects.
5.	In the dependency section: <dependency> <groupId>SE</groupId> <artifactId>junit</artifactId> <version>4.6.0</version> </dependency> What will Maven do in this case? How can you solve?
o	Explanation: Maven will fail to download this dependency. The groupId and artifactId are not correct for JUnit. Maven looks for these details on the Maven Central Repository, and it won't find anything with groupId as "SE".
o	Fix: You need to use the correct groupId and artifactId for the JUnit dependency.
o	Correct Code:
XML
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.6.0</version>
    <scope>test</scope>
</dependency>
6.	After building the WAR, you notice the generated file is named hospitalmgmtSys-1.0-SNAPSHOT.war instead of HospitalMgmtSystem.war, how to fix it?
o	Explanation: Maven adds the project's <version> to the final file name by default.
o	Fix: You can remove the version from the final file name by adding a <finalName> property inside the <build> section of your pom.xml.
o	Code:
XML
<build>
    <finalName>HospitalMgmtSystem</finalName>
</build>
________________________________________
Questions 7-13
7.	Add the central dependency of Java Servlet API 4.0.0-b01 to your existing project. Check the complete pom.xml file and run it.
o	Answer: You need to add the following dependency block inside the <dependencies> section of your pom.xml.
o	Code:
XML
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>4.0.0-b01</version>
    <scope>provided</scope>
</dependency>
8.	A developer removes the <dependencies> section completely. Will Maven still build the project? What issues might occur during testing?
o	Explanation: Maven will still build the project if there are no dependencies required for compilation. However, issues will occur during testing.
o	Issues during testing: The test code will fail because it won't be able to find the necessary libraries like JUnit or Mockito, which are required to run the tests.
9.	Failed to execute goal [org.apache.maven.plugins:maven-compiler-plugin:3.13.0:compile] on project [project-name] [ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK? Identify the error?
o	Explanation: The error is exactly as stated: "No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?" Maven needs the JDK (Java Development Kit) to compile the code. The JRE (Java Runtime Environment) is only for running Java applications, not compiling them.
10.	In Build is having finalname as <finalName>localhost:8080/FoodSystem</finalName>, is it works, if not how can you fix it?
o	Explanation: This will not work. The <finalName> is only meant for the name of the final build file (like a .jar or .war file). It should not contain a URL or any special characters like : or /.
o	Fix: The correct finalName should be just the name of the file, such as FoodSystem.
o	Code:
XML
<build>
    <finalName>FoodSystem</finalName>
</build>
11.	Your project is meant to deploy on Tomcat, but <packaging>jar</packaging> is like this in pom.xml. How do you solve it?
o	Explanation: To deploy a project on Tomcat, it must be packaged as a .war file. The <packaging> element in pom.xml must be set to war.
o	Fix: Change the packaging type to war.
o	Code:
XML
<packaging>war</packaging>
12.	In the <url> tag, written <url>http://maven.java.org12</url>. Will Maven accept this? What is the correct purpose of the <url> element in pom.xml?
o	Explanation: Yes, Maven will accept this URL. Maven does not check if the URL is valid or exists.
o	Purpose: The <url> element's purpose is to provide the URL for the project's website. It is used for documentation and information, not for any functional part of the build process.
