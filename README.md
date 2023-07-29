# LinkedIn Easy Apply Bot

Automate your LinkedIn job applications with ease using this Python and Selenium-based bot. Tested successfully on
over 15,000 job applications, this bot simplifies the Easy Apply process. Please note that the bot is provided without
warranty, and usage is at your own risk. I cannot be held responsible for any consequences, including account
restrictions or suspensions by LinkedIn. Consider it an educational and enjoyable project!

## Fork Notes

This bot is a fork from the previous maintainers' GitHub repository. It has been enhanced with additional features such
as new skills, more answers, and the option to log the application submission date and time. With this functionality,
you can even deploy a PowerBI dashboard to monitor the bot's performance using the CSV files generated by the bot.

## How-to Video

To assist you in setting up and using the bot, I have created a helpful video tutorial.
Watch it here: [YouTube Link](https://youtu.be/-eZJH5EdQr0)

## Setup & Startup

_Note: For detailed step-by-step explanation of `config.yaml`, see "Appendix: Step-by-step guide to config.yaml" at
the bottom._

1. Start by configuring the `config.yaml` file. This is a one-time setup and contains the necessary inputs for running
2. the bot. Take care not to change the formatting or add spaces in the file. Detailed explanations for each input can
3. be found in the comments within `config.yaml`.
4. After configuring the file, install the dependencies listed in `requirements.txt`.
5. Finally, run the bot using your preferred method:
    - If using an IDE like PyCharm Community Edition, execute `main.py` from your IDE.
    - If using the command line or terminal, activate the virtual environment with `source venv/bin/activate`, then
      run `python3 main.py`.

If you encounter any "dependencies not found" errors, ensure that the dependencies are installed. You can confirm this
using your IDE or, if using the command line/terminal, run `pip install -r requirements.txt` before
executing `python3 main.py` to start the bot.

#### Known issues
1. IDEs like PyCharm sometimes conflict with the included virtual environment (venv) in this project. To resolve this,
   you can delete the `venv` folder and configure the Python interpreter to use the "local" option. Additionally,
   install the dependencies from `requirements.txt` to ensure a successful run of `main.py`.

2. FIXED: ~~Sometimes, the bot may encounter an issue where it gets stuck in an endless loop of opening external links. This
   situation arises when two specific conditions are met. First, when the bot reaches a page with text like "no matching
   jobs found for(...)" and second, LinkedIn suggests "Jobs you may be interested in..." along with links to external
   websites. There are two possible solutions: a) click on the next appearing Easy Apply job from the suggestions,
   or b) change the search keywords while the bot continues its task. As a last resort, stop and restart the bot.~~

3. The bot currently faces challenges in providing accurate or incomplete responses to questions in non-English job
   posts sometimes triggering endless loops. The solution is to simply close such a job so the bot can move on to
   the next in the queue. 
   

## Appendix: Step-by-Step Guide to config.yaml

Enter your LinkedIn email and password. Ensure not to upload your `config.yaml` to avoid exposing your login credentials.
```yaml
email: email@domain.com
password: yourpassword
```

`disableAntiLock` prevents your PC from sleeping so the bot may run uninterrupted. Set to `True` if you wish to disable this functionality.
```yaml
disableAntiLock: False
```

Set `remote` to `True` if you want to apply for remote jobs only.
```yaml
remote: False
```

Set `experienceLevel` to the level(s) of jobs you wish to apply. You must set at least one to `True`.
```yaml
experienceLevel:
 internship: False
 entry: True
 associate: True
 mid-senior level: False
 director: False
 executive: False
```

Set `jobTypes` to the nature of jobs you wish to apply for. You must set at least one to `True`.
```yaml
jobTypes:
 full-time: True
 contract: False
 part-time: True
 temporary: False
 internship: False
 other: False
 volunteer: False
```

Use `date` to decide the time range when the job was posted. Select ONLY ONE as `true`.
```yaml
date:
 all time: True
 month: False
 week: False
 24 hours: False
 ```

Use `positions` to search the job titles you are interested to apply for. Uncomment (remove hash sign) to add more positions, but at least one is required. For example:
```yaml
positions:
 - Warehouse In-charge
 - Warehouse Supervisor
 - Warehouse Manager
 #- ...
 ```

Set `locations` to the countries/places where you wish to work. Uncomment to add more locations, but at least one is required. For example: 
```yaml
locations:
 - Remote
 - Canada
 - Australia
 #- remove_hash_to_add_more
 #- remove_hash_to_add_more
 #- ...
```

Use `distancee` to determine the radius/distance from the place to search the job. Only specific values are allowed being 0, 5, 10, 25, 50, or 100 miles.
```yaml
distance: 25
 ```

`outputFileDirectory` is the directory where the log files generated by the bot are saved. Change `myDirectory` to your specific folder path.
```yaml
outputFileDirectory: C:\Users\myDirectory\
 ```

Use `companyBlacklist` to prevent bot from applying in specific companies. Uncomment and add company names as required.
```yaml
companyBlacklist:
 #- company
 #- company2
 ```

Use `titleBlacklist` to prevent bot from applying on jobs containing black listed words in titles.
```yaml
titleBlacklist:
 #- word1
 #- word2
 ```

Set file path of your resume and cover letter (if any) in `uploads` section. If bot shows "file not found or unable to upload resume", a simpler solution is to apply on job once manually and bot will use manually uploaded resume automatically.
```yaml
uploads:
 resume: C:\Users\myDirectory\Resume.pdf
 # Cover letter is optional
 #coverLetter: C:\Users\myDirectory\CoverLettter.pdf
 ```

Update the answers in `checkboxes` to meet your specific needs as these would be used in all applications. In case of degrees, remove the hash sign to activate the ones you wish to mention in the application.
```yaml
# ------------ Additional parameters: checkboxes ---------------
checkboxes:
 # Do you have a valid driver's license? (yes/no checkbox)
 driversLicence: True
 # Will you now, or in the future, require sponsorship for employment visa status (e.g. H-1B visa status)? (yes/no checkbox)
 # This is relative to the location and your citizenship applying above, and same with legallyAuthorized.
 requireVisa: False
 # Are you legally authorized to work in COUNTRY? (yes/no checkbox)
 legallyAuthorized: True
 # We must fill this position urgently. Can you start immediately? (yes/no checkbox)
 urgentFill: True
 # Are you comfortable commuting to this job's location? (yes/no checkbox)
 commute: False
 # Are you comfortable working in a remote environment? (yes/no checkbox)
 remote: True
 # Are you comfortable taking a drug in accordance with local/state laws? (yes/no checkbox)
 drugTest: True
 # Are you willing to complete an assessment? (yes/no checkbox)
 assessment: True
 # Have you completed the following level of education: DEGREE TYPE? (yes/no checkbox)
 degreeCompleted:
  - High School Diploma
  - Bachelor's Degree
  #- Associate's Degree
  #- Master's Degree
  #- Master of Business Administration
  #- Doctor of Philosophy
  #- Doctor of Medicine
  #- Doctor of Law
 # Are you willing to undergo a background check, in accordance with local law/regulations?
 backgroundCheck: True
 ```

Update `universityGpa`  by entering your GPA which must be a decimal value to one decimal point (e.g., 3.8 or 3.0)
```yaml
# ------------ Additional parameters: universityGpa ---------------
universityGpa: 4.0
 ```

Use `salaryMinimum` to specify the minimum expected salary. Keep the input to integer without decimals or commas or currency symbols.
```yaml
# ------------ Additional parameters: salaryMinimum ---------------
salaryMinimum: 106000
 ```

Use `languages` section to specify languages you speak with proficiency being either "None", "Conversational", "Professional", "Native or bilingual". Do not change these as LinkedIn expects specific values. Also, the language spelling must be the same as used in Linkedin. For example:
```yaml
# ------------ Additional parameters: languages ---------------
languages:
 english: Native or bilingual # None, Conversational, Professional, Native or bilingual
 arabic: Conversational
 french: Conversational
```

Add notice period in weeks specific to your circumstances. For example:
```yaml
# ------------ Additional parameters: noticePeriod in weeks ---------------
noticePeriod: 8
```

Update following section based on your specific needs. Some skills are added as a default value, but feel free to add more as necessary to your profession and industry. The years of experience must be a whole number.
Use the `default` as a generic values for skills unexpected questions from employers so the bot does not respond with zero on those unexpected skills.

Note: This is based on keywords in the job questions. If you put 'R' for experience with the programming language R, this will match all questions with the character 'r'.
```yaml
# ------------ Additional parameters: years of experience ---------------
# How many years of work experience do you have ...? (whole numbers only)
experience:
 # normal ones
 Accounting/Auditing: 0
 Administrative : 0
 Advertising : 0
 Analyst : 0
 Art/Creative: 0
 Business Development: 0
 Consulting: 0
 Customer Service: 0
 Distribution Design: 0
 Education: 0
 Engineering: 0
 Finance: 0
 General Business: 0
 Health Care Provider: 0
 Human Resources: 0
 Information Technology: 0
 Legal: 0
 Management: 0
 Manufacturing: 0
 Marketing: 0
 Public Relations: 0
 Purchasing: 0
 Product Management: 0
 Project Management: 0
 Production: 0
 Quality Assurance: 0
 Research: 0
 Sales: 0
 Science: 0
 Strategy/Planning: 0
 Supply Chain: 0
 Training: 0
 Writing/Editing: 0
 #python: 0
 #selenium: 0
 # default to put for any industry/skill that you did not list
 default: 0
```

Use `personalInfo` to provide your information. 
```yaml
# ------------ Additional parameters: personal info ---------------
personalInfo:
 First Name: FirstName
 Last Name: LastName
 Phone Country Code: Canada (+1) # See linkedin for your country code, must be exact according to the international platform, i.e. Italy (+39) not Italia (+39)
 Mobile Phone Number: 1234567890
 Street address: 123 Fake Street
 City: Red Deer, Alberta # Include the state/province as well!
 State: YourState
 Zip: YourZip/Postal
 Linkedin: https://www.linkedin.com/in/my-linkedin-profile
 Website: https://www.my-website.com # github/website is interchangeable here
  ```

For such questions in job post, the bot will attempt declining answers. However, you may add the information for future use.
```yaml
# ------------ Additional parameters: USA employment crap ---------------
eeo:
 gender: None
 race: None
 vetran: None
 disability: None
 citizenship: yes
 clearance: no
```

Please make sure to provide the necessary information accurately.

## Need Further Assistance?

If you are new to Python, I recommend watching the [YouTube](https://youtu.be/-eZJH5EdQr0) video first for a better understanding. If you encounter any
issues with the code, please raise them in the "Issues" section of this repository. For general inquiries and support,
feel free to post a comment with a description of your problem under the YouTube video.

## Support This Project

You can show your support by buying me a coffee through this [PayPal Link.](https://paypal.me/voidbydefault)
