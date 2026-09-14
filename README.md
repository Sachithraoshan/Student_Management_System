Student Management System — Team Guide

Read Before You Start Coding
1. Push the shared foundation files FIRST (see Step 1 below) before anyone writes their individual page. Everyone's page depends on them.
2. Do NOT rename classes, properties, or the namespace. All files use the namespace StudentManagementSystem. If you rename something, everyone else's code breaks.
3. Do NOT edit DatabaseHelper.cs alone. It is shared by every page. If your page needs a new query or method added to it, message the team leader first, then whoever adds it pushes immediately and tells everyone to git pull.
4. Pull before you push. Always run git pull before you start working and again before you push, to avoid overwriting someone else's changes.
5. One person = one assigned file. Don't edit another member's form file unless agreed. 
6. Test your page individually first (Login -> Dashboard -> your page) before assuming it's done.
7. Naming convention: Keep file names exactly as listed below — PascalCase, matching the class name inside.
8. Comment your code: Briefly explain what each method does. We're being graded as a team; markers may check individual understanding.
9. No advanced C# features: Stick to standard loops, basic OOP, and try-catch blocks.
10. If you break the build, say so immediately in the group chat — don't push broken code and go silent.

---

Step 1: First Upload to Git (Shared Foundation)
The Team Lead pushes these first, before anyone starts their individual page. These are shared by all modules:

Database & Core:
- DatabaseHelper.cs (Handles SQLite connection and SchoolDB.sqlite)
- Program.cs
- DashboardForm.cs (Main navigation hub)
- LoginForm.cs
- Styles/SharedStyles.cs (Central Style Sheet & Design System - MUST USE FOR ALL PAGES)
- Icons/ (Project icon assets)

Models (/Models/ folder):
- Student.cs
- Course.cs
- Enrollment.cs
- AttendanceRecord.cs
- Grade.cs
- Payment.cs
- ResourceItem.cs (and subclasses BookResource.cs, LaptopResource.cs, OtherResource.cs)
- Notice.cs
- Exam.cs
- UserAccount.cs

Action: Everyone must git pull this foundation before writing your own page — your code will not compile without these.

---

Step 2: 10-Member Workload & Page Assignments
Fill in your names next to your assigned files:

Member 1 (Lead): DatabaseHelper.cs, DashboardForm.cs, Program.cs | Core Setup, Git Merges & Final Submission
Member 2: LoginForm.cs & CourseForm.cs | Authentication & Course Catalog
Member 3: StudentRegistrationForm.cs | Student Directory & Registration
Member 4: EnrollmentForm.cs | Course Enrollment Mapping
Member 5: AttendanceForm.cs | Attendance Tracking
Member 6: GradesForm.cs | Grades & Assessment
Member 7: FeeForm.cs | Fee & Billing Management
Member 8: LibraryForm.cs | Library Checkouts (OOP Polymorphism)
Member 9: NoticeBoardForm.cs & ExamScheduleForm.cs | Announcements & Exam Timetables
Member 10: AdminUserManagementForm.cs & ReportForm.cs | Admin Control Panel & Reporting

---

Step 3: Pushing Your Own Page
1. Push only your assigned form file(s).
2. Commit message format: Add [PageName] - [YourName] (e.g., Add CourseForm - Nimal).

---

UI Design & Main Style Sheet Guide (`Styles/SharedStyles.cs`)
IMPORTANT: All pages must use the central style sheet (`SharedStyles.cs`) to keep the application consistent, modern, and user-friendly. Do NOT hardcode dark background colors or manual styling inside your forms.

If you need custom colors, badges, or special layout builders specifically for your individual page, create a dedicated style file under `Styles/` named specifically for your page (e.g., `Styles/StudentRegistrationStyles.cs`).

1. Applying Form & Layout:
   - Call `SharedStyles.ApplyForm(this);` inside your form's `InitializeComponent()`.
   - Use `SharedStyles.CreateHeaderBar(this.ClientSize.Width, "Page Title", "icon_name.png")` to add the standard top header.
   - Use `SharedStyles.CreateCard(left, top, width, height, borderColor)` to create clean white card panels for your form inputs and lists.
   - Use `SharedStyles.CreateCardStripe(card.Width, SharedStyles.PrimaryBlue)` for the top accent stripe on cards.

2. Form Controls:
   - Labels: Use `SharedStyles.CreateFieldLabel("FIELD NAME", left, top)` for field headers.
   - TextBoxes: Use `SharedStyles.CreateStyledTextBox(left, top, width)` for input boxes.
   - ComboBoxes: Call `SharedStyles.ApplyComboBox(myComboBox);`.
   - ListBoxes: Call `SharedStyles.ApplyListBox(myListBox);`.
   - Action Buttons: Use `SharedStyles.CreateActionBtn("Button Text", left, top, w, h, "icon_name.png", accent: true)` (or `danger: true` for delete actions).
   - Dividers: Use `SharedStyles.MakeDivider(left, top, width)` for 1px separator lines.

3. Icons:
   - Place icon graphics in the `Icons/` folder.
   - Load icons cleanly with `SharedStyles.GetIcon("icon_name.png", width, height)`.

4. Color Palette Reference:
   - Form Background: `SharedStyles.FormBackground` (Pale Ice Blue)
   - Sidebar / Panel Tint: `SharedStyles.SidebarBg` (Soft Periwinkle)
   - Primary Accent: `SharedStyles.PrimaryBlue` (Royal Blue)
   - Card Background: `SharedStyles.CardBackground` (White)
   - Text Colors: `SharedStyles.TextPrimary` (Dark Charcoal) and `SharedStyles.TextSecondary` (Slate Gray)
   - Status: `SharedStyles.Success` (Green) and `SharedStyles.Danger` (Red)

---

Project Notes
- Project Type: Windows Forms App (.NET Framework)
- Database: Persistent local data is stored using SQLite (SchoolDB.sqlite) created automatically on first run. Default admin login is username: admin, password: 1234.