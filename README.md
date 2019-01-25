# Senja

Sejna is an island in Norway.  It's also SENtinel ninJA- part of CIA (Component Intelligence Architecture), the agile toolkit for run teams in high-velocity environments.  It allows run developers to provide quick solutions to problems involving many interconnected systems.

## Purpose

It's 3 AM and you're fast asleep. Suddenly, the familiar PTSD-inducing chime of your phone wakes you up to advise you that there's a problem with your system that requires a high priority fix.  You look at your phone, which reads: "JOB IN224C89 ABEND, COST BALANCE REPORT FAILURE"  It's going to take you a while to jump online, go to your team's Sharepoint site, dig up the documentation, and go throught the context diagram that shows you all of the systems that influence the IN224C89 job.  Then you may have to login to various databases, run queries, look for files that didn't get picked up by FTP, etcetera.  Now imagine you're new to this team.  You were hired on a month ago, you were given the on-call phone for the first time just this week, and this job has a 4 hour SLA.  It needs to be fixed or people don't get paid this week.

This is just the kind of problem that Senja was designed to solve.

## Target Platform and Discussion

Senja is targeted at Python 2.6.  This is specifically because there are still many RHEL 6 based environments out there that can benefit from this toolkit.

## Architecture

Senja is composed of the following components:

1. Tasks
A Task is the smallest unit of work.  A task might consist of checking for a file in a directory, getting the contents of a ZIP file, running a database query, or calling a web service.  Tasks can be shared among many Tests and/or Remedies.

2. Tests
A Test is a collection of Tasks that is used for diagnostic purposes.  A Test might consist of first running a Task that will retrieve a batch total via a webservice call, then another Task that looks for a file in a particular location, and if it exists, total all numeric values in a particular XML tag and compare those two values.

3. Suggestions
A Suggestion is a bit of text that is displayed to the user.  Tests may display one or more Suggestions based upon values returned from Tasks.

4. Remedies
A Remedy is a collection of Tasks that is used to cure or alleviate an issue.  A Remedy might consist of a task that will select the most recent record from a database of documents and run a webservice query that updates another system.

5. Risk Units
A Risk Unit is something that can break- for example, the IN224C89 batch job referenced above.  This "something" doesn't need to be one of your projects.  If your Finance department has a job F224 that will fail and page you because your job IN224C89 fails, then F224 should be included in your instance of Senja.

## Alternatives

https://github.com/Runbook/runbook
https://github.com/madflojo/automatron  (This appears to be for completely automating things, and there is no method for interactivity.  some Tasks may require the entry of login information.)

## Resources

https://medium.com/adobetech/self-healing-code-a-journey-through-auto-remediation-60367eea312


