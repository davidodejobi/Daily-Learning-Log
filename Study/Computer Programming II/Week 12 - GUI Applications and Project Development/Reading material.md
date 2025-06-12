# Week 12: GUI Applications & Project Development – Detailed Notes

## 🎯 Learning Objectives

* Outline the **stages** of a full‑fledged GUI app lifecycle (requirements → design → implementation → testing).
* Describe key **project‑management** practices (planning, collaboration, version control, deployment).
* Summarise robust **testing & debugging** strategies for GUI software (unit, integration, UI, usability).

---

## 1  Stages of GUI Application Development

| Stage                                    | Purpose                                                                       | Deliverables & Best Practices                                                                                                           |
| ---------------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Requirements Gathering & Analysis** | Discover user needs, target audience, functional/non‑functional requirements. | • Interview stakeholders, create user stories.<br>• Prioritise must‑have vs. nice‑to‑have features.                                     |
| **2. Design & Prototyping**              | Visualise interface and flow before coding.                                   | • Wireframes & low‑fidelity mock‑ups (Figma, Balsamiq).<br>• Iterate on feedback, refine layout, colours, accessibility.                |
| **3. Implementation**                    | Build app using frameworks (Qt, wxWidgets, GTKmm, Dear ImGui…).               | • Modular architecture (MVC/MVD).<br>• Use signals/slots, resource files, and consistent coding standards.                              |
| **4. Testing & Debugging**               | Ensure quality, fix bugs, validate UX.                                        | • Unit tests with Embunit / Google Test.<br>• Integration + UI automation (Squish, Qt Test).<br>• Usability sessions with target users. |
| **5. Deployment & Maintenance**          | Package, distribute, update, support.                                         | • Installers (windeployqt/macdeployqt).<br>• Auto‑update mechanism.<br>• User support & issue‑tracking workflow.                        |

---

## 2  Project Management Essentials

| Aspect                                 | Key Actions                                                                                       |
| -------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Planning & Scheduling**              | • Break down tasks into milestones.<br>• Use Gantt charts or Kanban boards (Trello, Jira).        |
| **Team Collaboration & Communication** | • Daily stand‑ups, weekly demos.<br>• Code reviews & pair programming.<br>• Shared design docs.   |
| **Version Control**                    | • Git flow (feature branches → PR → main).<br>• Tag releases, maintain changelog.                 |
| **Issue Tracking**                     | • Classify bugs vs. feature requests.<br>• Assign severity & owner.<br>• Link commits to tickets. |
| **Deployment Planning**                | • Choose packaging type (static vs shared libs).<br>• Plan update channels & rollback strategy.   |

---

## 3  Testing & Debugging Strategies

| Technique                             | Purpose                                         | Tool Examples                                                    |
| ------------------------------------- | ----------------------------------------------- | ---------------------------------------------------------------- |
| **Unit Testing**                      | Verify individual widgets/helpers.              | Embunit, Google Test, Catch2.                                    |
| **Integration Testing**               | Validate component interaction (model ↔ view).  | Qt Test with `QSignalSpy`.                                       |
| **UI Testing (Record/Replay, Image)** | Automate clicks, assert visual state.           | Squish, SikuliX.                                                 |
| **Usability Testing**                 | Real users perform tasks; identify friction.    | Observational studies, heatmaps.                                 |
| **Debugging Tools**                   | Inspect runtime state, event flow, performance. | Qt Creator debugger, event‐loggers, `QML Profiler`, breakpoints. |

### Debugging Tips

1. Enable `QT_LOGGING_RULES` to filter noisy categories.
2. Use **visual debuggers** to inspect widget hierarchy.
3. Watch CPU/GPU usage—render loops can bottleneck.

---

## 4  Advantages of Structured GUI Project Workflow

* **Predictable delivery** – clear timeline & milestones.
* **Quality assurance** – systematic testing catches regressions.
* **Team scalability** – version control & issue tracking prevent chaos.
* **User satisfaction** – iterative design yields intuitive, polished UI.

---

## 5  Mid‑Lesson Quiz (Answers)

1. Stage NOT typical in GUI development? → **Deployment & Sales** is outside core dev cycle.
2. Why use version control? → Manage code changes & enable seamless team collaboration.
3. Which test simulates real user interactions visually? → **UI/Image‑based testing**.
4. Purpose of usability testing? → Evaluate user experience & collect feedback.

---

## 6  Practical Checklist Before Release

* [ ] All critical paths unit‑tested.
* [ ] UI passes accessibility audit (contrast, keyboard nav).
* [ ] Application icon & metadata set.
* [ ] Installer tested on fresh OS image.
* [ ] Crash‑report mechanism integrated.
