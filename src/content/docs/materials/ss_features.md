---
title: SS Features
description: Breakdown of what the SS could do, notes on how to replace
---

Organised by tab in the top navbar, then subheadings within that tab's dropdown menu.

## Student Management

### Student Search - 生徒

Takes you to a search form for students. You can save search filters to reuse later.

Buttons to:

- Create a new student: Opens a new student form in a modal
- Save your search filter
- Load criteria from your saved filters
- Reveal detailed filters
- Search
- Clear filters
- Save results as CSV/Excel

Can search by:

- Standard filters:

  - Status (Inquirer: 問合せ者, Student: 生徒)
  - SSID: Two boxes for some reason, joined by a ~.
  - Name: Has partial matching
  - School
  - School Manager
  - Contract status (Non-contractor: 未契約者, Student: 受講者, Former Student: 元受講者): has a checkbox to check/uncheck all
    - Can be searched based on contract status at a given date
  - Join date: As a range
  - Order by (Name/SSID, Asc/Desc)

- Advanced filters:
  - Specify 'x' as a search condition
  - Registered staff (登録スタッフ)
  - Updated at: as a range
  - Last updated staff
  - Aggregation destination type (集約先種別): Has 3 checkboxes and check/uncheck all
  - Consolidated students: Seems like you can search for them, not sure what it does
  - Using bank transfer or not
  - Account transfer request destination: List of Zeus with a date and fallback date
  - Withdrawal date: as a range, or no withdrawal date
  - Management ID: same split field as SSID
  - Phone number: Single input, but with checkboxes to search by home/mobile/emergency numbers and lack of those
  - Has restrictions on phone contact
  - Contact email: One input, but with checkboxes to search by email1/2 and lack of email1/2
    - Reception settings for both
  - App notification available or not
  - Prefecture select
  - Grade select: Can select multiple with checkboxes
  - Birthday: As a range
  - Gender: includes unknown
  - Last login: as a range, can also check boxes for logged in or not
  - Photos allowed
  - Card registered or not
  - Card number
  - Student category: 内部生, 予約生, ◆キャンセル待ち（予約生）, 休会生, 休会オンライン生, オンライン生, 外部生, 退会者, 予約キャンセル, 【使用不可】, 【使用不可２】, 未選択
  - Scheduled start date of lessons: As a range
  - Scheduled withdrawal date: As a range
  - Transfer period: As a range
  - Allergy
  - Pickup location
  - Dropoff location
  - Kindy early arrival: y/n/unknown
  - Has siblings: y/n/both
  - Sibling DOBs
  - Part of online lessons
  - IB english level
  - School English level: checkboxes, multi-select

#### Category Filters

- Contract Info
  - Type: Individual/Monthly
  - Status: not finalized/confirmed/cancelled/invalid
  - Acceptance date: as a range
  - School
  - Staff who created/was responsible for the contract
  - Course format: Fixed attendance/reservation
  - Contract course: has a 'specify course' checkbox
  - Contract period: as a range
  - Contract start date: as a range
  - Contract end date: as a range
  - Course period: as a range
  - Course start date: as a range
  - Course end date: as a range
  - Number remaining: Days?
  - Courses remaining
- Contract group info
  - Course period: as range
  - Course start date: as range
  - Course end date: as range
  - Last continue date: as range
  - Continuous suspension period: as range
- Course info
  - reservation reception date: as a range
  - school
  - room
  - student date: as a range
  - class time: range of times
  - course format: fixed attendance/reservation
  - course: has a 'specify course' checkbox
  - lesson
  - teacher
  - attendance status: unregistered/attendance/absence
- Non-attendance information
  - school
  - room
  - Non-attendance period: as a range
  - missed time: as a range
  - course format: fixed attendance/reservation
  - course: has a 'specify course' checkbox
  - lesson
  - teacher

#### Notable Features

- Contract statuses are stored by date, with history
- Can export CSV which matches filters

#### Questions

1. Does anyone use the ability to save search filters?
2. What does 'registered staff' (登録スタッフ) do?
3. What are 'consolidated students' (集約先生徒) and what do they do?
4. What does ' 集約先種別' do?
5. What does 'account transfer request destination' (口座振替依頼先) do?
6. How is management ID different to SSID?
7. Does anyone have restrictions on phone contact? As text or just yes/no?
8. How is 'scheduled start date of lessons' (レッスン開始予定年月) different from start date? Same for 退会月/予約キャンセル受付月 and quit date?
9. What's a 'transfer period' (転籍時期)?
10. Which fields do we actually use?
11. What's "契約コース, コースを指定する" (contract course/specify course)
12. What are number remaining and courses remaining (残数, 受講残数)?
13. How is 'contract group info' (契約グループ情報指定) different from 'contract info' (契約情報指定)?
14. What do the 4 course/contract dropdowns that add extra fields represent? How are they different?
15. Do we want SSIDs as a range? Anyone use that? And what for?

### Student Import

Just a file upload input and a dropdown that lets you select the import format. Import format controls the columns in the DB that'll be updated, and there's a button to download a sample CSV with those columns.

The second step, once the file is uploaded, is a confirmation tab. Shows a list of all records uploaded with errors highlighted, whole upload fails if any errors.

Seems basically the same as my implementation, but with more stuff we might not need.

### Bulk Student Deletion

Also seems to be a CSV upload followed by a confirmation tab.

#### Questions

1. Why do we use this?
2. Would you be open to a version which doesn't require a CSV? What should it look like in terms of fields to search by etc.

### Medical Record

Search form for medical data, has the same filters as basic/advanced student search so I assume it gets the data through the student it's attached to.

The form for creating new medical data has:

- Child status: Inquirer/Student
- Student
- Date & time of entry
- Created by: autofills with current user
- Details

#### Questions

1. Why is there a date and time of entry? Is that not when you submit the form?
2. What exactly is a medical record? Health info? Or when a kid gets hurt?

### Medical Record Import

Same as the other import screens, seems no one uses this though.

### Messages

Search form for messages, with following filters:

- Message status: Outgoing: draft/unread/read and Incoming: unread/read
- Created at: as a range
- Message content
- Staff
- School
- Student
- Student's school
- Reply sent: boolean (only affects incoming messages)

### Student Email Distribution

Seems to be a way of scheduling emails/searching scheduled emails. Bit like creating a job in our version.

Scheduling an email to be sent has a confirmation screen.

Fields for the form to create a new email are:

- Scheduled sending time
- Recipient options: checkboxes for email 1/2, app notification and whether to send to people who opted out of receiving emails
- from address: defaults to school email if sent by a school, has radio buttons for HQ, selecting from a list of school emails, sending from the email of the assigned school or specifying an email to send from
- Importance: just a checkbox which makes it high priority
- Assigned school
- Staff
- A button that reveals inputs for adding read receipts by embedding a provided link in the email
- Checkbox to show separate subject/body for PC/mobile
- 'Embedded characters': there's a long list of select options
- Subject
- Body
- Attachments
- Internal notes

Has search fields for:

- Subject
- Scheduled sending date/time: as a range
- School
- Staff
- Status: draft/waiting/sent
- Order by: sending date asc/desc

#### Questions

1. Confirm it is for scheduling emails to be sent en masse later/that you can search for past mass emails.
2. What are embedded characters?
3. Do we ever send separate body/subject for PC/mobile?

### Student Announcements

Form to create new announcement has:

- Subject
- School
- Staff
- Notice period: as a range
- announcement location: checkboxes for PC/smartphone/both
- content for PC
- content for smartphone
- attachments
- internal notes
- send email notification: checkbox to determine whether students should receive an email about the announcement
- some way of adding filters to narrow down the recipients
  - There are also options to filter the recipients by contract or child info, unsure if this is part of the earlier heading or in addition to it
- a way of adding schools to send the notification to, seems groups are possible
- buttons to save as draft (it won't be published when the date hits) or save (it will)

Search form for student announcements, with following filters:

- Subject
- School
- Staff
- Notice period: as a range
- publication status: draft/waiting/published/publication finished

#### Questions

1. Do we use the separate PC/smartphone content?
2. What options do you have for narrowing down the recipients in お知らせ対象?

### Student Attendance

Fields are:

- SSID: as a range
- name
- attendance date: as a range
- school
- room
- checkboxes for arrived or not and a time range to narrow it
- checkboxes for left or not and a time range to narrow it
- order by attendance date, SSID, entry time, departure time in asc or desc

The form adds internal notes and a checkbox to notify parents or not.

#### Questions

1. Is this actually attendance? Google translates as entry/exit
2. What is 'room'(ルーム)/ do we need it?

### School year registration

Seems to be a way of setting the year kids are in at school based on their age?

#### Questions

1. This is marked as used by basically everyone, but I don't understand why it would ever be used after being initially set/why it would need to be configurable?

### School year update

You can choose to update by incrementing their grade by one year, or calculating it from their birthday.

There's a table showing the history of updates and who did them. Based on that they do in fact manually update every single year.

#### Questions

1. Why is this manual? I can't think of any possible reason, and can think of so many for it to not be manual. I want to make sure I'm not missing something here, cos this and the last one seem completely pointless to me.

## Contract Management

### Contract

Main part is a search form like other sections, but also has buttons to create a new contract from scratch and from pre-defined templates.

#### Search

- Basic fields
  - Radio button for 表示単位: 契約単位/契約グループ単位
  - Contract status: checkboxes, and one to select all, for: not finalized/confirmed/cancelled/invalid
  - Student
  - Course: whether it specifies a course
  - Course format: checkboxes for fixed or reservation
  - Type of contract: Individual/monthly
  - Contract period: as a range
  - Contract start date: as a range
  - Contract end date: as a range
  - Template used
  - Order by contract number, student code or student name in kana asc or desc
  - CSV output format: per contract course or per contract amount breakdown unit
- Advanced filters
  - All the advanced student filters are available here too
  - Separate sections for student and contract advanced filters
  - Contract acceptance date: as a range
  - Contract confirmation date: as a range
  - Contract school
  - Contract registration staff
  - Course period: as a range
  - Course start date: as a range
  - Course end date: as a range
  - Pause period: as a range
  - Number remaining: as a range
  - Number of remaining courses: as a range
  - Contract amount: as a range
  - Registration date: as a range
  - Assigned staff
  - Last updated: as a range
  - Who made the last update
  - Amount details/type: There are checkboxes for the type of the 'amount', then search fields which open a new window where you can select from a list of predefined sets of details

#### New Registration

- Type of contract: radio button, toggles between individual and monthly, toggling it to monthly adds fields below
- Shared fields
  - Student
  - Acceptance date
  - Contract reception school
  - Contract reception staff
- Monthly
  - Course period: as a range
  - Continuation start date

#### Template selection

Lets you create a contract from a list of templates. Can select from the list, or search by type of contract/template content (as text fields for some reason).

#### Questions

0. Just a general overview of what contracts/courses are for and how they interact would be very helpful.
1. What is 表示単位: 契約単位/契約グループ単位?
2. What does the 'specifies a course' (コースを指定する) checkbox mean?
3. What's the difference between these for CSV output? 契約コース単位で出力/契約金額内訳単位で出力
4. How does pausing a course work? Do you just enter a number of days it was paused, or the actual range of dates it was paused? Can there be multiple separate pauses?
5. What's the difference between contract registration staff and assigned staff?
6. What's up with 金額内容/金額タイプ? Is there a contract for each of these, are they add-ons to the contract? They're all predefined by us?
7. What's the difference between the different dates? Like acceptance date (契約受付日), continuation start date (継続開始年月) etc.

### Import Contract Data

- Radio buttons for individual or monthly
- Action: create/update/group update
- Radio button for whether the imported contracts should be marked not finalized or confirmed
- File field
- A button to download a sample CSV

#### Questions

1. Why the toggle for individual/monthly and confirmed/not? Couldn't that just be part of the CSV data?

### Contract Templates

Search form and a button to create them.

#### Search form

- Basic fields
  - Type of contract: radio button, toggles between individual and monthly
  - Template code: as a range
  - Template name
  - Template content
  - Registered school
  - Validity period: as a range
  - Availability: checkboxes for available or not
- Advanced fields
  - School used: separate fields for school and school group
  - restrictions on which schools the contract can be accepted
    - checkboxes for whether to display templates with limits on the school/not/both
    - search fields for school/school group
- Attendance: fixed/reservation
- Course: checkbox for whether it's specified
- Class: checkbox for whether it's specified

#### New template creation

- Basic fields
  - Contract type: radio button, toggles between individual and monthly
  - Template code
  - Template name
  - Template content
  - Registered school
  - Schools used at: a searchable list of schools it can be used in, and checkbox to select all schools
  - Validatity period: as a range
  - Availability: checkbox to make unavailable
- Terms and Conditions
  - Contract acceptance date: a bunch of different options for how to set the acceptance date
    - Radio buttons for no initial value/calculated from operation date/manual entry
    - If you're calculating it, there's another set of radio buttons for how it's calculated which reveal the relevant inputs
    - Manual entry reveals an input
  - Course period from/to: options as above
  - Continuation start date
    - same fields as above
    - plus you can set the base date for the continuation period
    - and calculation settings for months after base date

#### Questions

1. What is the class option here? I assume it's different from 'room' in other forms, what's the difference?
2. In 契約条件, what do all the options for 契約受付日 do? The contract acceptance date is calculated?
3. The two options for 算出設定 seem the same to me when translated, what's the difference?

### Sales

Search form for sales, buttons for sales registration/return registration.

#### Search fields

- Basic filters
  - Display fields: sales unit/sales item unit
  - Sales status: not confirmed/confirmed/invalid, checkboxes for all and one to select all
  - Sales/contract number: as range
  - Sales date: as a range
  - Child status: checboxes inquirier/student
  - Child
  - Inquirer
  - Sales staff
  - Sales type: sale/return
  - Sales registration type: contract/sale
  - Line type: seems to be the categories of sale available
    - Enrollment fee/kit
    - Tuition fee/extension
    - Maintenance/snack fee
    - Materials fee
    - Event/test/meal
    - Reservation fee
    - Discount
    - Order: sale date/student code asc/desc
- Advanced filters
  - Has the same advanced fields as children, plus for sales
  - Sales management ID: as a range
  - Sales school
  - Details: same as the line items above?
  - Cost: as a range
  - Registration date: as a range
  - Registration staff
  - Last updated: as a range
  - Who made the last update

#### Sales/return registration

Separate buttons.

- Sales type: sale/return, prefilled from the button
- Status: inquirer/student
- Student
- Sale date
- Sales school building
- Sales staff
- details
- Detail information
  - There's a table where you select the line type from a box, then select an item from that line, auto updating unit cost quantity and total amount
  - You can add multiple to a sale, shows the total for all at the bottom
  - There's also a breakdown of cost by line type
  - Billing notes
- Payment info
  - Buttons for bulk addition, add difference line, add blank line and account transfer info
  - There's a table with columns for
    - date
    - method
    - and columns for each line type with the amount they paid from that line type
    - delete line button
  - Bottom two rows are total and difference, difference is automatically calculated
- Other
  - Another notes section

Rather than payment info, refunds have

- Refund date
- Refund amount
- Select for refund method

#### Questions

1. What's the difference between sales and return (販売種別/販売/返品/販売登録種別/契約/販売)?
2. What's the difference between sales unit and sales item unit (販売単位/販売明細単位)?
3. What's inquirer (問合せ者)?
4. Do we add the line types (明細タイプ) ourselves?

### Import Sales

Button to download sample CSV.

- radio buttons for processing: create/update
- sales status: confirmed/not
- file upload

### ~~Deposit List~~ NOT NEEDED

- Basic fields
  - Status: inquirier/student
  - Student
  - Inquirer
  - School in charge
  - Sales school
  - Planned deposit date
  - Deposit type: deposit/refund
  - Scheduled deposit method:
    - account transfer
    - bank transfer
    - reservation deposit application
    - welfare coupon
    - refund to customer account
    - cash
    - others
    - usage prohibited
    - usage prohibited
    - TBD (that's actually what it says)
  - Deposit status: not paid/partially paid/paid/overpaid
  - Payment application date: as a range
  - account transfer status: checkboxes for unregistered, results not imported, results imported, transfer not possible
  - order: planned deposit date/student name asc/desc
- Advanced fields
  - All the student fields
  - All the contract info fields
  - Estimated deposit amount
    - For each line type, a range of amounts
    - Staff in charge
    - internal notes
  - Attendance info
    - School
    - Room
    - Student date: as a range
    - Class time

#### Questions

1. Which deposit methods do we use/do we want to use?
2. Would be nice to have proper translations for the ones we use.
3. Do we add the payment methods ourselves?
4. What's account transfer status (口座振替状況)? And its options

## Course

Create button, search fields

### Search

- Basic fields
  - Course code: as a range
  - Course name
  - Lesson: clicking the magnifying glass brings up a modal
    - with a searchable table of lessons, cols are:
      - name, capacity, length, active range
  - Course format: fixed/reservation
  - Contract type: individual/monthly
  - Validity period: as a range
- Advanced fields
  - School building
  - School building group

### Create

- Basic fields
  - Course code
  - Course name
  - Course name kana
  - Course display name
  - Attendance format: fixed/reservation
  - Contract type: individual/monthly
  - Lesson: can be chosen from a list
  - Change number of contracts: checkboxes for what seem to be conditions under which the courses in the contract can be changed
  - Unit price settings
    - Use them or not
    - Allow them to be changed in certain circumstances, like above
  - Amount change: same options for being able to change the amount
  - School: can be chosen from a list, checkbox to use all schools
  - Validity period: as a range
  - Internal comments
- Carryover information
  - checkbox to carry over subscriptions or not
  - carryover limit: no limit/number/percentage(rounded up/down)
  - max months carried forward
  - order of use: carried balance first/carried last
- Course reservation setting
- Display settings
  - Display on site or not
  - Show number of contracts
  - Show number reserved or not
  - Show number remaining or not
- Default values
  - Default school: can be from a defined list, the student's school or the school the contract is signed at
  - Course transfers
  - Course schedule: 7 rows of dropdowns, cols are:
    - No idea, day, hour, minute
  - Number of contracts
    - Set a limit on contracts, optionally per month
    - unit price
    - total price
  - Same fields as above but for monthly and continuation contracts

#### Questions

1. Why is there a separate display name?
2. What is change number of contracts (契約数変更)? And the options (個別契約で契約数の変更を可能とする/月謝契約（初回）で契約数の変更を可能とする/月謝契約（継続）で契約数の変更を可能とする)
3. We don't use carryover info right? That section is red on the sheet
4. What's コース予約設定情報? What difference does selecting one of the options make?
5. What are course transfers (受講振替)? And the associated options?
6. What are the options from the first column in 受講日程?

### Course Data Import

Button to download sample CSV

### Course Reservation Settings

- Seems to be a way of restricting courses/actions that can be taken by students in the course
- Lots of difficult to translate Japanese details here

#### Questions

1. What's this used for?
2. Are we likely to need to add more or is it pretty set?
3. Can I get an overview of what the restrictions are/what they apply to? e.g only apply to a single course or can apply to multiple

### Monthly contract continuation

#### Questions

1. Does this section just give staff a way to copy contracts that are going to be renewed from previous months?
2. What's the difference between the initial page and the one you can access from the 継続状況確認 button in the top right?

### Contract amount details

Can search or create. Separate page for import, just the file field.

- Amount type: items from line type, but only a selection
- Amount code
- Amount name
- kana
- display name
- Quanity/amount change: restrictions on change to each attribute, as above
- Schools it's used in
- Validity period
- Internal comments
- Price, separate for individual and monthly contracts
  - Monthly is broken into initial and continuation contract prices
  - Can potentially be changed by month

#### Questions

1. What exactly are these? Looks like charges that fall into categories from the line items above, but only some of them?
2. What's the 月別設定 option on the form for? Is it used?

### Teaching Materials

Seems to be much the same as contract amount details, is it just a different category of the same thing?

#### Questions

1. Is this just a different category of contract amount details, but the same basic idea?

### Discount

Seems to be much the same as contract amount details, is it just a different category of the same thing?

#### Questions

1. Is this one also basically the same as contract amount details?

### Account transfer list

This seems to be where you can create of options for account transfers, currently 6th/27th using Zeus.

#### Questions

1. Do we need an interface to add these or can they be part of the code?
2. What context are they used/selected in?

### Billing emails

Seems to be a way of sending emails from a billing template, where they just fill in the necessary info. Seems like something we could automate away. They can also search sent emails by:

- Send date: as a range
- School it was sent from
- Staff who sent it

## Lesson Management

### Lessons

Seem to be the different levels/times they can sign up for, like Keep Up/Specialist/seasonal(am/pm), maybe early arrival options, kindy arriving at 1:30/3 etc.

#### Questions

1. This seems to be most of the things we charge for, are the contracts etc. just collections of these?
2. Do the limits on people to use them actually do anything, cos they seem low?

### Lesson Data Import

### Reservation status (by room)

Seems to be a way of listing all the lesson reservations by month/day/week or in a list. For time based views it's shown in a calendar-like table with rows for each school/level combination.

#### Questions

1. Are rooms levels? e.g. galaxy, land, sky

### Attendance status

Searchable list of attendance. Editing is done from the table of results by pushing buttons.

### Reservation slot

Seems like a list of all the potential times/dates the 'Lesson's can be delivered at and their available slots/attendance.

#### Questions

1. Am I right about the purpose of the page?
2. Is this the same info as the attendance status page in a different format?

### Reservation Slot templates/batch creation/import

Templates for whatever the previous one is, and a way to bulk create them (using the templates). There's another one after it that seems identical.

Import does the usual stuff.

#### Questions

1. What's the difference between 予約枠一括作成 and 予約枠一括作成・取込履歴?
2. What is 予約枠テンプレートデータ取込, and 予約枠 in general?

## Instructor Management

The only thing they use it for is IP locks, we can do that through schools so nothing to implement here from the SS, we'll just be adding our own features.

## School Management

### School

Search form and a button to create a new one.

- Search
  - Name
  - Validity period??
  - Visibility
- Create
  - Name
  - Kana
  - Display name
  - Address input: postcode/prefecture/line1/line2, also option to automatically set from postcode
  - Phone
  - Fax
  - Sending email address
  - confirmation email address
  - validity period: as a range
  - displayed/hidden
  - remarks
  - notes for billing email
  - transfer information
  - group: this would be area for us
  - student restrictions
    - close registrations (can only be added to a waitlist, school is full)
    - prevent cancellations by parents (only school can cancel reservations)
  - student limits
    - cannot transfer to substitute course
    - students cannot cancel their classes

#### Questions

1. Is there any reason we'd need the validity period for schools? They all seem infinite. Is there any record we do use the validity period field on, like contracts/courses/templates?
2. Do we need separate names and display names?
3. Is 送信メールアドレス the address that school sends mail from? And 確認メールアドレス is where they receive notification emails from the system?
4. What are 請求メール用備考 and 振込先情報?
5. What are 受講振替登録制限 and 受講キャンセル制限 restrictions? Do we use them?
6. What fields do we actually use from the creation form?

### School Data Import

The usual import view, just a file field and confirmation screen after.

### School Groups

Yeah these are literally just areas.

### Room

This seems to be a mixture of levels, courses and seasonal stuff. Maybe some completely different thing repurposed to serve a bunch of purposes.

- Search
  - School
  - name (partial matching)
  - validity period
- Create
  - School (that the room belongs to, can only be one)
  - name
  - Kana
  - display name
  - extension number
  - capacity
  - validity period
  - remarks
  - same student restrictions as schools

#### Questions

1. This seems to represent a lot of loosely related stuff that's not quite the same, like courses but also some levels which don't seem to correspond to our level system and seasonal school. Is this actually all one category of stuff or are there some things in here that aren't really the same as the rest, and if it is one category what exactly is it?

### Room Data Import

Standard.

### Staff

- Search
  - staff code: as a range
  - name
  - school
  - validity period
  - instructor collaboration: radio for all/available/not available
  - email
  - login: checkboxes for login or not, if login then a range of last login date
- Create
  - staff code
  - name
  - kana
  - school
  - validity period
  - remarks
  - whether to display schools based on search conditions?
  - password/confirmation
  - email 1 & 2
    - receive notification emails or not
    - receive message received notifications or not
  - permissions

#### Questions

1. What's 講師連携 and what do the options do?
2. What's 校舎検索条件/検索条件の校舎を初期表示しない in the form to create new staff?
3. What can each role/permission set do?
4. Would bilingual teachers have different permissions to native teachers?
5. Do we have any users who have a combination of permissions from multiple roles? If so who and why?

### Staff Data Import

As usual.

### School permissions

- Controls which schools staff can access, we'd do this with Pundit.

### School permissions import

As usual.

## System Management

**Gave up on this one part way through, so over detailed I need to sit down with someone and hash out what actually needs to be configurable/can be hardcoded**

### PS Usage Status

PS is Platinum School, the platform.

For the current and previous month, shows:

- number of registered students
- number of enrolled students
- storage used
- number of entry/exit terminals
- emails sent

#### Questions

1. What are 入退室端末数?
2. How are we storing 58.5 GB of data? Do we store files here or is it all the database?
3. Nakagawa san apparently uses this, what information is important from here? Is there other information that would be useful? The available info here seems very random/limited.

### Language settings

We have other ways of doing this, can be done per user.

### "Basic" Configuration

#### School info

Probably more like org info in LMS context

- Name
- Kana name
- Address (as other address fields)
- Phone
- Start on Sunday or Monday
- New arrival display period: in days
- School title

#### School closure/holidays

- Display holidays on calendar or not
- Use school holidays checkbox
- Title of closed days

#### Aliases for student info fields

We can do this with translations/helpers if necessary. The same for course, lesson and class etc. aliases below.

#### Contract/Sales info

- Checkboxes to enable monthy/individual contracts
- Radio button for default contract type

#### Questions

0. What configuration options from this page are actually useful, and which can we just have as defaults? For example as far as I'm aware the start date of Japanese school doesn't often change, that could just be hardcoded (and is on the event site, so we don't need to manually adjust grades)

### Operation log inquiry

#### Questions

1. Do we need logs of interaction? e.g. test result changes, student changes. DO we need to log all changes for everything or can there be a cutoff?
2. With changes? Or just when and who did it?
