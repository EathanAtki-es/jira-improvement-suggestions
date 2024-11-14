<br />
<div align="center">
  <a href="https://github.com/github_username/repo_name">
    <img src=".github/resource/images/logo.png" alt="Logo">
  </a>

   <h3 align="center">Jira improvement suggestions</h3>
</div>
<br />

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#optimised-workflow-status">Optimised Workflow Statuses</a>
    </li>
    <li>
      <a href="#optimised-workflow">Optimised Workflow</a>
    </li>
    <li>
      <a href="#qa-fail-workflow">QA Fail Workflow</a>
    </li>
    <li>
      <a href="#e2e-automations">End to end automation suggestions</a>
    </li>
    <li>
      <a href="#issue-type-cleanup">Issue type cleanup</a>
    </li>
  </ol>
</details>

# Optimised Workflow Statuses <a id="optimised-workflow-status"></a>

1. **Prioritised**
   - **Description:** Task is prioritised and ready for development to begin.
   - **Transition:** Move to "In Progress."

2. **In Progress**
   - **Description:** Development work is underway.
   - **Transition Options:**
     - **Code Review**: Development is complete, and the code is ready for a review.
     - **Back to Ready**: If the task needs more clarification or is deprioritised.

3. **Code Review**
   - **Description:** Code is awaiting review.
   - **Transition Options:**
     - **Approval**: Code review is complete, pending approval by the project or product owner.
     - **In Progress**: If changes are requested in the code review.

4. **Approval**
   - **Description:** Awaiting final approval from the project owner.
   - **Transition Options:**
     - **Testing**: Task is approved and ready for QA.
     - **In Progress**: If additional work is needed based on feedback.

5. **Test Ready**
   - **Description:** Tasks awaiting QA.
   - **Transition Options:**
     - **Testing**: If QA identifies issues.
  
6. **Testing**
   - **Description:** Task is in QA testing.
   - **Transition Options:**
     - **Failed**: If QA identifies issues.
     - **Passed**: If QA is successful.

7. **Failed**
   - **Description:** Issues found in QA that need to be fixed.
   - **Transition Options:**
     - **In Progress**: Task returns to development for fixes.
     - **Testing**: After fixes, task is ready for retesting.

8. **Passed**
   - **Description:** QA is complete, and the task is Regress Ready testing.
   - **Transition:** Move to "Regress Ready."

9. **Regress Ready**
   - **Description:** The task is prepared to be included in regression testing, where it will be tested with other completed features.
   - **Transition:** Move to "Regressing" when regression testing begins.

10. **Regressing**
   - **Description:** Task is undergoing final regression testing to ensure stability and compatibility with other features.
   - **Transition Options:**
     - **Release Ready**: If regression testing is successful and the task is ready for deployment.
     - **Testing**: If regression testing identifies issues that need to be reworked.

11. **Release Ready**
    - **Description:** Task has passed all testing and is cleared for release.
    - **Transition:** Move to "Done" once the task is deployed.

12. **Done**
    - **Description:** The task is complete and successfully deployed or closed.

---

### Workflow Summary

1. **Prioritised → In Progress**
2. **In Progress → Code Review → Approval**
3. **Approval → Test Ready → Testing**
4. **Testing → Failed (loop) or Passed**
5. **Passed → Regress Ready → Regressing**
6. **Regressing → Release Ready → Done**

---

### Status Summary

| **Status**           | **Short Description**                              |
|----------------------|----------------------------------------------------|
| **Prioritised**            | Task is ready to start development.                |
| **In Progress**      | Development work is ongoing.                       |
| **Code Review**      | Awaiting code review.                              |
| **Approval**         | Awaiting project owner’s approval.                 |
| **Test Ready**       | Tasks awaiting QA.                             |
| **Testing**          | Undergoing QA testing.                             |
| **Failed**           | Issues found in QA, needs rework.                  |
| **Passed**           | QA complete, Regress Ready testing.         |
| **Regression Ready** | Ready to join other features in regression testing. |
| **Regressing**    | Undergoing final regression testing.               |
| **Release Ready**    | Cleared for release.                               |
| **Done**             | Task is complete and closed.                       |

---

<br>

# Optimised Workflow <a id="optimised-workflow"></a>

Reducing workflow statuses can streamline the process, making it easier for teams to manage tasks without losing visibility or important information. Here’s an approach to consolidating statuses while retaining clear stages:

---

### Steps to Reduce Workflow Statuses

1. **Combine QA and Regression Testing Stages**  
   - **Current Statuses**: *Test Ready, Testing, Failed, Passed, Regress Prep, Regressing*
   - **Suggested Consolidation**:
     - **Testing**: A single status for all QA and regression testing. When issues are found, the task is marked as “Failed” (or returns directly to “In Progress”).
     - **Failed** (optional): If preferred, a **Failed** status can be maintained to specifically track tasks that didn’t pass QA, but this could also be managed through comments or labels instead of an actual status.
   - **Resulting Statuses**: Tasks move from “Testing” back to “In Progress” if they don’t pass, or directly forward if testing is successful.

2. **Use Labels or Custom Fields Instead of Specific Statuses**
   - Some details (e.g., **Regress Ready** vs. **Regressing**) can be managed using **labels** or a **custom field** instead of dedicated statuses.
   - This way, you maintain insight into specific testing phases without adding additional workflow steps. For example, use a custom field like “Testing Phase” with values such as **"QA"** and **"Regression"**.

3. **Merge Pre-Testing Approval Stages**
   - **Current Statuses**: *Code Review, Approval*
   - **Suggested Consolidation**: Combine **Code Review** and **Approval** into a single status, such as **Review** or **Approval**, where code review and any required approvals happen before moving to testing.
   - **Resulting Statuses**: This simplifies the process by consolidating all pre-testing reviews into one step.

4. **Condense Release-Ready Statuses**
   - **Current Statuses**: *Release Ready, Done*
   - **Suggested Consolidation**: If the difference between “Release Ready” and “Done” is minimal, consider having only **Done** for tasks that are cleared for release.
   - Alternatively, use **Done** to signify readiness for release and close the task post-release without needing an intermediate step.

---

### Optimised Workflow

After applying the consolidations above, the statuses could look something like this:

1. **Prioritised**  
2. **In Progress**
3. **Review** (combines Code Review and Approval)
4. **Testing** (combines all QA and regression testing phases)
5. **Done** (signifies readiness for release or already released)

---

### Workflow Summary

| **Status**   | **Description**                                            |
|--------------|------------------------------------------------------------|
| **Ready**    | Task is ready to start development.                        |
| **In Progress** | Active development is happening.                        |
| **Review**   | Code review and any necessary approvals are underway.      |
| **Testing**  | Task is in QA or regression testing phases.                |
| **Done**     | Task is complete and ready for or has already been released.|

---

### Benefits of This Reduced Workflow

- **Simplicity**: Reduces workflow to just five key statuses, covering the full task lifecycle with minimal steps.
- **Clear Accountability**: Each status has a distinct owner (developer, reviewer, tester) for easy tracking.
- **Improved Task Flow**: Fewer transitions mean tasks move faster, and teams can focus on completion.
- **Use of Labels/Fields for Flexibility**: Maintains phase distinctions like QA vs. regression using labels or fields rather than separate statuses.

This approach balances simplicity with clarity, ensuring streamlined workflows without sacrificing essential insights into task progress. Let me know if this aligns with your needs or if you'd like more specific examples!

When a feature fails QA, it’s generally best to have it move to a specific **"Failed"** status rather than directly back to **"In Progress"** or **"Ready**." This "Failed" status clarifies that the feature needs attention due to QA issues, while allowing teams to prioritise it, assess failure reasons, and decide next steps. Here’s how this approach can benefit the workflow:

---

# QA Fail Workflow<a id="qa-fail-workflow"></a>

If we choose to coninue with the QA statuses i think we need to align on what the process it with what happens with the failed ticket. In retro we discussed how figures reported for QA Failed tickets staying in this status for too long however i believe this to be because the parent stayed in this status until the defects were ready for QA again. I think we need a hybrid aproach of using this column and moving it back when the defects are in progress.

### Workflow for QA Failures

1. **Failed Status**:
   - When a feature fails QA, it moves to a **"Failed"** status. This serves as a clear signal that the feature didn’t meet quality requirements and requires rework.
   - This status allows the team to document failure reasons, making it easier to identify patterns, track issues, and assess whether they’re related to code, requirements, or testing.

2. **Transition from Failed to In Progress**:
   - After a failure assessment, the feature can transition back to **"In Progress"** for rework, where the developer can address the issues identified in QA.
   - This transition provides clarity on accountability by clearly moving the task back to the development team once QA documentation or failure insights are reviewed.

3. **Back to Testing**:
   - Once rework is complete, the task moves from **"In Progress"** to **"Testing"** again.
   - This structured process ensures the feature goes through the same QA standards as before, helping maintain consistency.

---

### Why a “Failed” Status Improves the Workflow

- **Enhanced Tracking and Documentation**: The **"Failed"** status provides a holding area where issues can be documented, and root causes can be analysed. This also helps with process improvement by making failure data available for review.
- **Reduced Ambiguity**: A dedicated **"Failed"** status eliminates any confusion about the feature’s current state and makes it clear that a feature is not in active development but awaiting rework due to QA feedback.
- **Efficient Transition and Accountability**: Moving from **"Failed"** to **"In Progress"** makes it easy to see which tasks are currently being reworked, and it clarifies developer responsibility for handling QA-related issues.

---

### Workflow Summary

- **Testing → Failed → In Progress → Testing**
- Each stage has a clear purpose, ensuring accountability and transparency across QA failures and rework.

### Automations

Automation can play a crucial role in managing tasks that fail QA by ensuring immediate visibility, accountability, and clear next steps. Here are some tailored automation suggestions for handling transitions and notifications when a task enters the **"Failed"** status:

---

### 1. **Automatic Transition Notifications**
   - **Notify Developers**: When a task moves to **"Failed"**, trigger an automated notification to the task’s assigned developer (or team) via email, Slack, or Jira’s built-in notifications. This helps ensure that the failure is immediately visible and actionable.
   - **Notify QA Team**: You can also set up notifications for the QA team if additional review or documentation is needed. This is useful for maintaining thorough records of failure reasons.

### 2. **Auto-Assignment on Failure**
   - **Assign Task to Developer or Team Lead**: When a task transitions to **"Failed"**, automation can automatically reassign it to the original developer or team lead for investigation and rework. This eliminates manual assignment and ensures the issue goes directly to the responsible person.
   - **Optional Assignment to Triage**: If your team prefers to review failures before rework, set up automation to assign the task to a triage lead, who will determine next steps before it moves back to development.

### 3. **Automatic Labeling or Tagging**
   - **Add “Failed” Label**: Automatically apply a label such as **"QA-Failed"** when a task moves to **"Failed"**. This label can be used to filter and track failed tasks separately for metrics or reporting, giving insight into common failure reasons or trends.
   - **Flag High-Priority Failures**: If a task fails repeatedly, automation can add a “High-Priority” label or flag the task for management review. This helps avoid repeated cycles of failure without deeper investigation.

### 4. **Automated Comment with Failure Details**
   - **Add Context from QA**: Require QA to enter failure details in a specific field or comment before the task can move to **"Failed"**. Automation can then copy these details to the task’s comment section, ensuring that developers have all the information they need to address issues quickly.
   - **Checklist of Failure Reasons**: Use an automated checklist of common QA failure reasons (e.g., functionality, performance, UI) to provide structured feedback on the reason for failure, which can help with later analysis.

### 5. **Automatic Status Reset Upon Rework Completion**
   - **Auto-Move to Testing After Fixes**: When the developer marks the task as “Rework Complete” or moves it to **"In Progress"**, automation can automatically transition it back to **"Testing"** once it’s ready, reducing manual transitions and minimising the chance of a task stalling between statuses.

### 6. **Escalation Rules for Unresolved Failures**
   - **Set SLAs for Failed Tasks**: If a task remains in **"Failed"** for a set period (e.g., 2 business days), automation can trigger an escalation notification to a team lead or project manager, ensuring visibility and prioritisation of unresolved issues.
   - **Escalate Repeated Failures**: If a task fails multiple times, automation can add it to a high-priority queue or trigger an alert to a senior team member to ensure root causes are addressed before retesting.

### 7. **Create a Report or Dashboard for Failed Tasks**
   - **Track Failure Metrics**: Automatically log and track metrics on failed tasks (e.g., failure reasons, time in **"Failed"** status, number of failures per task) using a Jira dashboard or reporting tool. This provides insights into potential bottlenecks, high-failure areas, or recurring issues in development.

### 8. **Automation Rules for Linked Issues**
   - **Link Related Issues on Failure**: When a task fails QA, automation can create or link to a “Bug” or “Sub-task” issue to track specific failure points separately. This can help document rework needs clearly without cluttering the main task.

---

### Example Automation Rules in Practice

1. **Trigger**: Task transitions to **"Failed"**  
   - **Actions**:
     - Notify assigned developer and team lead via email and Slack.
     - Add **"QA-Failed"** label.
     - Add a comment with the reason for failure and QA notes.
     - Assign task back to the developer or to a triage lead.
   
2. **Trigger**: Task remains in **"Failed"** for 48 hours  
   - **Actions**:
     - Send an escalation notification to the project manager.
     - Mark task as high-priority if it hasn’t been addressed.
  
3. **Trigger**: Task transitions from **"Failed"** to **"In Progress"**  
   - **Actions**:
     - Remove **"QA-Failed"** label.
     - Update task assignment to the original developer.
     - Automatically transition to **"Testing"** when marked as “Rework Complete.”

---

# End to end automations <a id="e2e-automations"></a>

Implementing automation for transitions and notifications throughout the entire workflow can significantly improve efficiency, accountability, and visibility. Here are additional automation suggestions that cover the full workflow, from development through release.

---

### 1. **Automatic Assignment and Notifications for Key Transitions**

   - **Auto-Assign During Status Changes**: 
     - When a task moves to **"In Progress"**, auto-assign it to the developer who picked it up. 
     - After **Code Review** or **Approval**, automatically assign the task back to the original developer if rework is required, or assign it to the QA team when it moves to **Testing**.
   - **Transition-Based Notifications**:
     - Notify the code reviewer when a task moves to **Review**.
     - Notify the QA team when a task moves to **Testing** or **Test Ready**. These notifications help ensure that tasks don’t linger between stages.

### 2. **Automate Task Transitions with Development Events**
   
   - **Transition Based on Pull Requests**:
     - When a developer opens a pull request, transition the task to **Code Review** automatically. 
     - When the pull request is merged, automatically move the task to **Testing** if no additional approvals are needed. This reduces manual transitions and aligns with development activity.
   - **Reopen Task on Pull Request Rejection**:
     - If a pull request is rejected, automate the transition of the task back to **In Progress** and notify the developer, allowing for quick rework.

### 3. **QA Feedback Loops**
   
   - **Fail Notification**:
     - When a task moves to **Failed** from **Testing**, automatically notify the developer and the project manager, ensuring both visibility and accountability.
   - **Automated “Failed” Cycle**:
     - If a task fails QA more than once, apply an “Escalation” label or notify a lead to prompt further investigation, helping prevent continuous loops without deeper analysis.

### 4. **SLA Automation for Timely Task Progression**

   - **Set SLAs for Each Stage**:
     - Use automation to trigger reminders if a task stays too long in a particular status. For instance:
       - If a task stays in **In Progress** for more than 3 days, notify the assigned developer and their team lead.
       - If a task remains in **Testing** for more than 2 days, alert the QA team lead.
   - **Escalation on Overdue Tasks**:
     - After SLA breaches, escalate overdue tasks to a project manager for prioritisation, helping the team stay on track and minimising delays.

### 5. **Automate Priority-Based Transitions**

   - **Automatic Transition to High Priority**:
     - For tasks marked as **High Priority**, automate fast-tracking by notifying relevant stakeholders and moving the task to the top of the queue in each status, such as jumping to the front of **Testing** or **Review**.
   - **Priority Notifications**:
     - Send a priority-based notification to developers when tasks move into **Prioritised** with a high-priority label, helping prioritise urgent work early on.

### 6. **Automate Status Changes for Release and Completion**

   - **Automatically Transition to “Release Ready”**:
     - When all associated tasks or subtasks in a sprint are marked **Passed**, trigger automation to move them collectively to **Release Ready** for final deployment, reducing last-minute confusion over release status.
   - **Post-Release Transition**:
     - Once a release is confirmed, automatically move all tasks from **Release Ready** to **Done**, ensuring consistency in tracking.

### 7. **Real-Time Slack or Email Notifications for Key Statuses**

   - **Set up Slack/Email Integration**:
     - Automate notifications to dedicated Slack channels or email lists for specific transitions, such as **"Review"**, **"Testing"**, and **"Release Ready"**. This can help the team stay updated in real-time without needing to check Jira constantly.
   - **Notify Stakeholders on “Done”**:
     - Send a notification to relevant stakeholders (like product owners or managers) when tasks transition to **Done**, ensuring they’re aware of completed work.

### 8. **Weekly Digest for Workflow Summary**

   - **Summary Report Automation**:
     - Generate and send out a weekly summary report listing tasks in each workflow stage, emphasising any stalled or high-priority items. This provides team leads with an overview of progress, blockers, and upcoming releases.

### 9. **Automated Labeling and Filtering for Easy Tracking**

   - **Automatic Labels Based on Status**:
     - When tasks enter specific statuses, apply labels automatically (e.g., “Ready for QA,” “In Review”), enabling easy filtering and visibility into the task lifecycle.
   - **Filter by Labels**:
     - Automation can apply and remove labels when tasks enter or leave specific statuses, making it easier to create filters and dashboards for each workflow stage.

### 10. **Custom Notifications for Dependencies**

   - **Notify Dependent Task Owners**:
     - When a task with dependencies (such as subtasks or linked issues) moves to **Done**, notify the owners of dependent tasks, ensuring that work can proceed smoothly without delays.
   - **Automated Blocking Notifications**:
     - If a task is blocked and marked with a “Blocked” label, automatically notify the assignee of the blocking task to resolve the issue quickly.

---

### Summary of Benefits

These automation rules can:
- Improve communication and reduce manual transitions.
- Enable efficient, real-time tracking of task progress.
- Promote accountability by automatically notifying relevant team members.
- Help maintain timelines with SLA-based reminders and escalations.
- Provide clarity on task dependencies and priorities across the team.

# Issue type field cleanup <a id="issue-type-cleanup"></a>

Limiting fields in Jira issue types to a concise set of essential information offers several advantages, especially in making the process more efficient, clear, and developer-friendly. Here are the main reasons why it’s beneficial to keep Jira fields to a minimum:

---

### 1. **Reduces Cognitive Load and Speeds Up Issue Creation**
   - **Less Overhead**: Fewer fields mean developers and team members spend less time filling out or reviewing unnecessary information, allowing them to focus on critical data that drives the task forward.
   - **Streamlined Issue Creation**: With only essential fields present, developers can create issues faster and with fewer distractions, enabling a more agile workflow.

### 2. **Enhances Focus on Key Information**
   - **Clarity on Priority Fields**: By limiting the number of fields, the most important fields—such as **Description**, **Priority**, **Assignee**, and **Status**—stand out, making it easy for developers to understand the task requirements at a glance.
   - **Reduces Information Overload**: Too many fields can clutter the interface and overwhelm developers, potentially leading to misunderstandings or overlooking critical information. Focusing on the essentials keeps the issue page clean and understandable.

### 3. **Improves Data Quality and Consistency**
   - **Fewer Fields to Maintain**: A concise set of fields reduces the likelihood of outdated or irrelevant fields, ensuring that all information in the issue is relevant and up-to-date.
   - **Less Room for Error**: The more fields available, the more chance of inconsistencies or mistakes when filling them out. By limiting fields, you improve data accuracy, as each field has a clear purpose and is likely to be filled in correctly.

### 4. **Facilitates Faster Issue Navigation and Tracking**
   - **Easy to Scan**: When issues contain only the most relevant information, developers and stakeholders can scan through issues quickly, helping them understand progress, blockers, or dependencies with minimal clicks and scrolling.
   - **Efficient Tracking**: Limiting fields to essential ones means you can design more focused filters, views, and reports, making it easier to track progress across multiple issues or projects without getting lost in extraneous details.

### 5. **Aligns with Agile and Lean Principles**
   - **Focus on Value-Added Information**: Agile emphasises efficiency, adaptability, and value-focused processes. Keeping fields concise aligns with this by ensuring that only valuable, actionable information is requested and maintained.
   - **Less is More**: Minimising fields fosters a leaner process by eliminating unnecessary steps, ensuring developers can focus on coding and problem-solving rather than administrative tasks.

### 6. **Reduces Onboarding Time and Increases Adoption**
   - **Simplicity for New Developers**: For new team members or developers who are unfamiliar with your Jira setup, a simplified, essential field set makes it easier to get started without extensive onboarding.
   - **Higher Adoption**: When developers find it easy to use and understand Jira issues, they’re more likely to embrace the tool and keep issue information updated.

### 7. **Eases Maintenance and Customisation of Workflows**
   - **Simpler Workflow Customisation**: Fewer fields mean that any automation rules, workflows, or reporting tied to those fields are easier to maintain and update as project needs evolve.
   - **Greater Flexibility for Future Updates**: Limiting fields allows admins to make changes quickly and more effectively when requirements change, without needing to review and update a complex field structure.

---

### Key Takeaway

By limiting Jira fields to essential ones, you reduce complexity, enhance focus on critical information, and support an agile, user-friendly workflow. A concise set of fields not only benefits developers by streamlining their interactions with Jira, but it also enhances overall productivity, consistency, and data quality across the team.