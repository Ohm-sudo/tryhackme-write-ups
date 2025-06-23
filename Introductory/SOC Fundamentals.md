<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/6645aa8c024f7893371eb7ac-1718872418242" alt="Room Icon" width="200"/>
</p>

# SOC Fundamentals
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/Aashir.Masood">Aashir.Masood</a>

<br>

## Task 1: Introduction
- A SOC (Security Operations Center) is a specialized security team.
  - Continuously monitors organization's network and resources.
  - Works 24/7.
<br>

#### Q1: What does the term SOC stand for?
<pre>Security Operations Center</pre>
<br>

## Task 2: Purpose and Components
- Main focus of SOC is to keep detection and response intact - using security solutions.
- **Detection** involves discovering vulnerabilities, unauthorized activity, policy violations, or intrusions.
- **Response** involves minimizing impact and performing root cause analysis of the incident.
- Three Pillars of SOC: **People, Process, and Technology**.
  - These make up a mature SOC environment.
<br>

#### Q1: The SOC team discovers an unauthorized user is trying to log in to an account. Which capability of SOC is this?
<pre>Detection</pre>
<br>

#### Q2: What are the three pillars of a SOC?
<pre>People, Process, Technology</pre>
<br>

## Task 3: People
- People in a SOC is always important.
- Also known as the SOC team.

| Role                         | Description                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SOC Analyst (Level 1)**    | Anything detected by the security solution would pass through these analysts first. These are the first responders to any detection. SOC Level 1 Analysts perform basic alert triage to determine if a specific detection is harmful, and report through proper channels. |
| **SOC Analyst (Level 2)**    | While Level 1 does the first-level analysis, some detections require deeper investigation. Level 2 Analysts dive deeper into investigations and correlate data from multiple sources to perform proper analysis.                                          |
| **SOC Analyst (Level 3)**    | Level 3 Analysts are experienced professionals who proactively hunt for threat indicators and support incident response activities. Critical-severity detections from Level 1/2 often become security incidents requiring containment, eradication, and recovery. |
| **Security Engineer**        | Analysts work on security solutions, but these need deployment and configuration. Security Engineers deploy and configure these tools to ensure smooth operation.                                                                                        |
| **Detection Engineer**       | Security rules are the logic behind security solutions. Level 2/3 Analysts often write these rules, but Detection Engineers may also own rule development and tuning independently.                                                                    |
| **SOC Manager**              | Manages SOC processes and provides support. The SOC Manager liaises with the CISO to update them on the SOC team’s security posture and ongoing efforts.                                                                                               |
<br>

#### Q1: Alert triage and reporting is the responsibility of?
<pre>SOC Analyst (Level 1)</pre>
<br>

#### Q2: Which role in the SOC team allows you to work dedicatedly on establishing rules for alerting security solutions?
<pre>Detection Engineer</pre>
<br>

## Task 4: Process
- Alert triage is the basis of the SOC team.
- Triage is focused on analyzing alert - determines severity and priority.
  - Answer the 5Ws - who, what, where, when, why.
- Reporting involves documenting information (i.e., tickets) for escalation, timely response, and resolution.
- In critical scenarios, teams perform an incident response and forensic activity - analyze system or network artifacts.
<br>

#### Q1: At the end of the investigation, the SOC team found that John had attempted to steal the system's data. Which 'W' from the 5Ws does this answer?
<pre>Who</pre>
Identifying person of the incident (who). In this case, John.

<br>

#### Q2: The SOC team detected a large amount of data exfiltration. Which 'W' from the 5 Ws does this answer?
<pre>What</pre>
Explains what happened.

<br>

## Task 5: Technology
- Technology refers to security solutions.
  - Helps minimize SOC team manual effort.
- Security solutions centralize information and automate detection and response.
- Examples:
  - SIEM: Security Information and Event Management. Collect logs from various devices. Detection rules configured to identify suspicious activity.
  - EDR: Endpoint Detection and Response. Real-time and historical visibility of devices' activities.
  - Firewall: Barrier between internal and external networks.

<br>

#### Q1: Which security solution monitors the incoming and outgoing traffic of the network?
<pre>Firewall</pre>

#### Q2: Do SIEM solutions primarily focus on detecting and alerting about security incidents? (yea/nay)
<pre>yea</pre>
<br>

## Task 6: Practical Exercise of SOC
Lab will appear on the right side of the screen and the following questions correspond with the lab.

#### Q1: What: Activity triggered the alert?
<pre>Port Scan</pre>
One of the first things you see when you open the lab.

<br>

#### Q2: When: Time of the activity?
<pre>June 12, 2024 17:24</pre>
When investigating the alert, you can see the timestamp on the left side.

<br>

#### Q3: Where: Destination host IP?
<pre>10.0.0.3</pre>
When investigating the alert, you can see the destination host IP under the Destionation IP column.

<br>

#### Q4: Who: Source host name?
<pre>NESSUS</pre>
Again, Source Host Name is one of the columns shown in the log.

<br>

#### Q5: Why: Reason for the activity? Intended/Malicious
<pre>Intended</pre>
Activity is a false positive. Traffic is in private network since SOC team running port scan activity. A Nessus scan is being performed to scan for vulnerabilities on the device (JOE PC).

<br>

#### Q6: Additional Investigation Notes: Has any response been sent back to the port scanner IP? (yea/nay)
<pre>yea</pre>
In the logs you can see traffic from the endpoint (JOE PC) back to the endpoint scanner - indicating a response.

<br>

#### Q7: What is the flag found after closing the alert?
<pre>THM{000_INTRO_TO_SOC}</pre>
