DegreePath — Initial Requirements Backlog

1. Project Overview

Project name: DegreePath

Purpose: DegreePath is a centralized academic planning application that helps university students understand their degree requirements, generate personalized semester schedules, track academic progress, and estimate their expected graduation date.

The goal is to consolidate information that students would otherwise have to gather from degree flowcharts, course catalogs, prerequisite lists, and other academic resources. The application will help students make informed decisions about which courses to take and how their choices may affect graduation.

Initial scope: The first version will support a limited set of degree programs using structured course, prerequisite, and degree-requirement data. Direct integration with university registration systems is outside the initial scope.

2. Requirement Metadata

Each requirement includes:

* ID: Unique identifier.
* Priority: MoSCoW classification — Must have, Should have, Could have, or Won’t have in the initial version.
* Type: Functional or non-functional.
* Dependencies: Other requirements that should be implemented first.
* Acceptance criteria: Conditions used to determine whether the requirement has been satisfied.

3. Requirements Backlog

REQ-01: Student Academic Profile

Priority: Must have
Type: Functional
Dependencies: None

User story: As a student, I want to create an academic profile so that the application can personalize my degree plan.

Acceptance criteria:

* The student can enter their university, major, degree program, and catalog year.
* The student can specify their expected graduation semester.
* The student can specify their preferred credit load per semester.
* The application validates required fields before saving the profile.

REQ-02: Degree and Course Information Database

Priority: Must have
Type: Functional
Dependencies: None

User story: As a student, I want the application to contain degree requirements and course information so that I can plan my academic progress in one place.

Acceptance criteria:

* The system stores course codes, names, credit hours, and prerequisites.
* The system stores degree requirements, including required courses and elective categories.
* Courses can be associated with the degree programs that require them.
* The system can distinguish between required courses and courses that satisfy elective requirements.

REQ-03: Completed and In-Progress Courses

Priority: Must have
Type: Functional
Dependencies: REQ-01, REQ-02

User story: As a student, I want to record courses I have completed or am currently taking so that the application can determine my remaining requirements.

Acceptance criteria:

* The student can add completed courses and their completion status.
* The student can identify courses currently in progress.
* The system checks entered courses against the selected degree requirements.
* The system does not count an in-progress course as successfully completed.

REQ-04: Degree Progress Tracking

Priority: Must have
Type: Functional
Dependencies: REQ-02, REQ-03

User story: As a student, I want to see which degree requirements I have completed and which remain so that I can understand my progress toward graduation.

Acceptance criteria:

* The system displays completed, remaining, and in-progress requirements.
* The system identifies unmet requirements.
* The system calculates a progress indicator using a clearly defined method.
* The system updates the progress indicator when the student’s academic record changes.

REQ-05: Prerequisite Validation

Priority: Must have
Type: Functional
Dependencies: REQ-02, REQ-03

User story: As a student, I want the application to verify prerequisites so that it does not recommend courses for which I am not eligible.

Acceptance criteria:

* Each course can have zero or more prerequisites.
* The system checks prerequisites against completed courses and applicable academic rules.
* Courses with unmet prerequisites are excluded from eligible-course recommendations unless a documented exception applies.
* When a course is excluded, the system explains which prerequisite is missing.

REQ-06: Eligible Course Recommendations

Priority: Must have
Type: Functional
Dependencies: REQ-02, REQ-03, REQ-04, REQ-05

User story: As a student, I want to see which courses I can take next semester so that I do not have to manually compare multiple academic resources.

Acceptance criteria:

* The system identifies courses that satisfy outstanding degree requirements.
* The system filters out courses for which the student does not meet prerequisites.
* The system displays course names, credit hours, and the requirements they satisfy.
* The system distinguishes recommended courses from other eligible courses.

REQ-07: Schedule Preference Configuration

Priority: Should have
Type: Functional
Dependencies: REQ-01

User story: As a student, I want to specify my scheduling preferences so that suggested schedules fit my needs.

Acceptance criteria:

* The student can set a minimum and maximum credit load.
* The student can specify preferred class times and days.
* The student can specify unavailable time periods.
* The system distinguishes mandatory scheduling constraints from optional preferences.

REQ-08: Semester Schedule Generation

Priority: Must have
Type: Functional
Dependencies: REQ-05, REQ-06, REQ-07

User story: As a student, I want the system to generate possible schedules so that I can choose a suitable combination of courses for the next semester.

Acceptance criteria:

* The system generates schedules from eligible courses and available course sections.
* Generated schedules respect prerequisite requirements and the student’s mandatory constraints.
* The system respects the specified credit-load limits whenever a valid schedule is possible.
* The system presents multiple alternatives when multiple valid schedules exist.
* If no valid schedule is found, the system explains the limitation and suggests possible adjustments.

REQ-09: Schedule Comparison and Selection

Priority: Should have
Type: Functional
Dependencies: REQ-08

User story: As a student, I want to compare and save generated schedules so that I can select the option that best suits my preferences.

Acceptance criteria:

* The student can view each schedule’s courses, meeting times, and total credits.
* The student can compare schedules based on their preferences.
* The student can select and save a preferred schedule.
* The student can generate alternatives without losing a previously saved schedule.

REQ-10: Graduation Date Forecasting

Priority: Must have
Type: Functional
Dependencies: REQ-03, REQ-04, REQ-05, REQ-06

User story: As a student, I want to see my projected graduation semester so that I can determine whether my current academic plan is realistic.

Acceptance criteria:

* The system estimates graduation based on remaining degree requirements and planned course loads.
* The forecast accounts for prerequisite dependencies and the planned order of courses.
* The system identifies when required courses or prerequisite chains may prevent the student from graduating by their target date.
* The system explains the assumptions used to produce its estimate.

REQ-11: Alternative Graduation Planning

Priority: Should have
Type: Functional
Dependencies: REQ-08, REQ-10

User story: As a student, I want to compare alternative academic plans so that I can explore graduating earlier or avoiding a delay.

Acceptance criteria:

* The student can compare different credit loads and semester plans.
* The system can evaluate scenarios involving summer courses when applicable.
* The system identifies plans that may allow earlier graduation.
* The system identifies plans that may delay graduation.
* Each projection indicates the assumptions and course availability on which it depends.

REQ-12: Academic Progress Warnings

Priority: Should have
Type: Functional
Dependencies: REQ-04, REQ-10

User story: As a student, I want to receive warnings when my academic progress may delay graduation so that I can adjust my plan early.

Acceptance criteria:

* The system compares the student’s projected graduation date with their target date.
* The system warns the student when the target date appears infeasible under the current plan.
* The warning identifies relevant missing requirements or prerequisite bottlenecks.
* The system allows the student to explore alternative plans.

REQ-13: Academic Data Validation and Error Handling

Priority: Must have
Type: Non-functional
Dependencies: REQ-01, REQ-02, REQ-03

User story: As a student, I want the system to identify invalid or incomplete academic information so that my degree plan is not based on incorrect data.

Acceptance criteria:

* Invalid course codes and unsupported degree selections are identified.
* Missing prerequisite or degree-requirement data is not silently treated as confirmed information.
* The application provides understandable error messages.
* Calculations that depend on incomplete information are identified as estimates.

REQ-14: Student Data Privacy and Security

Priority: Must have
Type: Non-functional
Dependencies: REQ-01

User story: As a student, I want my academic profile and progress information to be protected so that other users cannot access my private information without authorization.

Acceptance criteria:

* Students can access only their own saved academic profiles.
* The application validates access to protected student information.
* Sensitive information is not exposed in error messages or application logs.
* Any stored student information is handled according to the application’s documented privacy practices.

REQ-15: Degree Plan Export

Priority: Could have
Type: Functional
Dependencies: REQ-04, REQ-08, REQ-10

User story: As a student, I want to export my degree plan so that I can review it outside the application or discuss it with an academic advisor.

Acceptance criteria:

* The student can export their selected schedule and projected semester-by-semester plan.
* The export includes planned courses, credit hours, and projected graduation semester.
* The exported plan identifies estimates and assumptions.
* The exported information matches the plan currently displayed in the application.

4. Initial Dependency Overview

The main implementation dependencies are:

1. Academic data foundation: REQ-01 and REQ-02 establish the student profile and degree information.
2. Academic record and progress: REQ-03 enables REQ-04 and supports prerequisite validation.
3. Course recommendations: REQ-05 and REQ-06 identify eligible courses.
4. Schedule generation: REQ-07 and REQ-08 use course eligibility and student preferences to generate schedules.
5. Graduation forecasting: REQ-10 estimates graduation based on academic progress and course dependencies.
6. Advanced planning: REQ-09, REQ-11, REQ-12, and REQ-15 build on generated schedules, progress information, and forecasts.

The dependencies indicate logical implementation order, not necessarily that every dependent requirement must wait until the entire preceding feature is finished.

5. Initial Scope and Assumptions

* The initial implementation will support a limited number of degree programs.
* Course offerings and meeting times will come from a structured dataset rather than a live university registration system.
* The system will generate planning recommendations but will not register students for classes.
* Graduation dates are projections, not guarantees.
* Official degree requirements and university policies remain authoritative.
* Requirements and priorities may change after feedback from students, advisors, and other stakeholders.

6. Questions for Further Requirements Elicitation

The following questions should be resolved before implementation:

1. Should the first release support only one major or multiple degree programs?
2. How will degree requirements and course offerings be entered, updated, and verified?
3. How should the system handle transfer credits, substitutions, minimum grades, and course retakes?
4. Should schedule generation use only official section meeting times or also allow tentative plans for future semesters?
5. How should the system rank schedules when not all preferences can be satisfied?
6. Should students be able to import transcripts or enter courses manually?
7. What university-specific rules must be considered when estimating graduation?

These questions identify gaps in the initial elicitation process and provide topics for stakeholder interviews and subsequent backlog refinement.
