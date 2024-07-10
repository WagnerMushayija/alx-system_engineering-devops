
stmortem Report: **The Great Login Meltdown of July 2024**

Welcome to our latest postmortem adventure! Grab a coffee, maybe a donut, and let’s dive into how our **User Authentication Service** decided to take a nap for a bit too long on July 8, 2024.

## 🚨 Issue Summary 🚨

**🕰 Duration:** July 8, 2024, 14:30 UTC to July 8, 2024, 15:45 UTC

**📉 Impact:** Our User Authentication Service went on an unannounced break, leaving 95% of our users locked out of their accounts. It was like our service was on vacation, and the “out of office” message was not helpful!

**🕵️‍♂️ Root Cause:** A rogue firewall rule got a little too enthusiastic and blocked all incoming traffic to our authentication service. It was like inviting everyone to a party but forgetting to open the door.

## 🕰 Timeline of Events 📅

Here's how things unfolded:

| Time (UTC)   | Event Description                                                                 |
|-------------|-----------------------------------------------------------------------------------|
| **14:30**    | **🔔 Alert!** Our monitoring system detected a surge in failed logins.            |
| **14:31**    | **👀 Whoa!** An engineer saw the alert and started investigating the issue.       |
| **14:35**    | **🔍 What’s Going On?** Logs checked, and the authentication service was running but unresponsive. |
| **14:50**    | **💡 Eureka!** Network and firewall configurations were checked for possible misconfigurations. |
| **15:00**    | **🤦‍♂️ Found It!** Discovered a firewall rule change accidentally blocked traffic. |
| **15:05**    | **🚀 Escalation!** Network team swooped in to fix the issue.                        |
| **15:15**    | **🔧 Fixed It!** Corrected the firewall rule to allow traffic to the authentication service. |
| **15:25**    | **✅ All Good!** Verification showed that users could log in again.                 |
| **15:45**    | **🎉 Case Closed!** Incident marked as resolved after confirming service stability. |

## 🔍 Root Cause and Resolution 🔧

**Cause:** The firewall decided it was done with visitors and blocked all traffic to the User Authentication Service. Think of it as an overzealous bouncer at a club who decided to reject everyone.

**Resolution:** We rolled back the faulty firewall rule and let the users back in. It was like reopening the doors after a party snafu.

## 🛠 Corrective and Preventative Measures 🚧

To ensure this doesn’t happen again, we’re taking the following steps:

### **What We’re Improving:**

1. **🎯 **Firewall Rule Review:** We'll implement a review and approval process for firewall changes so every rule is checked twice before being applied.
2. **🧪 **Automated Testing:** We’re setting up automated tests to check if firewall rules are doing their job properly.
3. **📈 **Enhanced Monitoring:** We’re upgrading our monitoring systems to catch these issues faster.

### **Specific Tasks:**

1. **[TODO]** Create a comprehensive firewall rule change checklist and a new approval workflow.
2. **[TODO]** Develop automated tests for firewall rules and integrate them into the deployment pipeline.
3. **[TODO]** Enhance traffic monitoring and alerts for critical services to better detect anomalies.
4. **[TODO]** Establish a verification step for firewall rule changes to ensure service availability post-change.

## 🗺 Diagram

Here’s a **simple diagram** to show what went wrong and how we fixed it:

```plaintext
       +-------------+
       |   Users     |
       |  (Trying to  |
       |   Log In)    |
       +------+------+
              |
              v
       +------+------+
       |  Authentication |
       |   Service     |
       +------+------+
              |
              v
    +---------+-----------+
    | Firewall Rule Issue |
    +---------+-----------+
              |
              v
       +------+------+
       |  Fix the Firewall |
       |     Rule        |
       +------+------+
              |
              v
       +------+------+
       | Users Back  |
       | to Logging In |
       +-------------+


