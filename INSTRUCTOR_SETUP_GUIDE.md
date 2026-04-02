# Instructor Setup Guide for GitHub Repository

## Quick Start: Publish Your Starter Repository

Follow these steps to create and publish the starter repository on GitHub:

---

## Step 1: Initialize Git Repository Locally

Open terminal and navigate to the starter repository folder:

```bash
cd "/Users/mahdikhemakhem/Library/CloudStorage/GoogleDrive-mahdi.khemakhem@enetcom.usf.tn/My Drive/TEACHING/KSA/00_OS/Assignment/assignment 472/OS-Assignment1-Starter"
```

Initialize the Git repository:

```bash
git init
git add .
git commit -m "Initial commit: Starter repository for CS3701 Assignment 1"
```

---

## Step 2: Create Repository on GitHub

1. Go to **GitHub.com** and log in
2. Click the **"+"** icon in top right → **"New repository"**
3. Fill in the details:
   - **Repository name**: `OS-Assignment1-Starter`
   - **Description**: `Starter repository for CS3701 Operating Systems Assignment 1 - Multithreading`
   - **Visibility**: ✅ **Public** (students need to fork it)
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)
4. Click **"Create repository"**

---

## Step 3: Push to GitHub

GitHub will show you commands. Use these (replace USERNAME with your GitHub username):

```bash
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/OS-Assignment1-Starter.git
git branch -M main
git push -u origin main
```

**Example** (if your username is `prof-mahdi`):
```bash
git remote add origin https://github.com/prof-mahdi/OS-Assignment1-Starter.git
git branch -M main
git push -u origin main
```

---

## Step 4: Verify Repository

1. Go to your repository URL: `https://github.com/YOUR_USERNAME/OS-Assignment1-Starter`
2. Verify you see all files:
   - ✅ README.md
   - ✅ SchedulerSimulation.java
   - ✅ DEVELOPMENT_LOG.md
   - ✅ REFLECTION.md
   - ✅ ANSWERS.md
   - ✅ .gitignore
3. **Make sure repository is PUBLIC** (check Settings → scroll to Danger Zone → Visibility should be "Public")

---

## Step 5: Update Assignment PDF

Now that you have the repository URL, update the LaTeX document:

1. Open `CS3701_Assignment_1_MultiThreading.tex`
2. Find the line with the placeholder URL (around line 392)
3. Replace with your actual URL:
   ```latex
   Fork the starter repository from: \url{https://github.com/YOUR_USERNAME/OS-Assignment1-Starter}
   ```

4. Recompile the PDF:
   ```bash
   lualatex CS3701_Assignment_1_MultiThreading.tex,
   lualatex CS3701_Assignment_1_MultiThreading.tex  # Run twice for references
   ```

---

## Step 6: Test the Fork Process

**Important**: Test that students can fork successfully!

1. Log out of your GitHub account
2. (Optional) Use a different browser or incognito mode
3. Go to your repository URL
4. Verify you can see:
   - The **"Fork"** button is visible
   - README.md displays correctly
   - All files are accessible
5. If you have a test account, try forking it to verify the process works

---

## Step 7: Post on Blackboard

Once everything is ready, post these to Blackboard:

### Files to Upload:
1. **CS3701_Assignment_1_MultiThreading.pdf** (the compiled assignment)
2. **Announcement text** (see below)

### Example Announcement:

```
Subject: CS3701 Assignment 1: Multithreading - NOW AVAILABLE

Dear Students,

Assignment 1 is now available. This assignment covers multithreading concepts from Chapter 4.

📝 Assignment Details:
- Worth: 5 marks (5% of final grade)
- Due Date: April 15, 2026, 11:59 PM
- Late Penalty: -1 mark per day

🔗 Important Links:
- Assignment PDF: [Attached]
- Starter Repository: https://github.com/YOUR_USERNAME/OS-Assignment1-Starter

⚠️ Requirements:
1. Create GitHub account using your university email (@std.psau.edu.sa)
2. Fork the starter repository
3. Complete all 5 parts
4. Submit GitHub link + Video link on Blackboard

📚 Instructions:
- Read the entire README.md in the repository carefully
- Start early - don't wait until the last day
- Make commits as you work (minimum 3 commits)
- Create a 2-3 minute video demonstration

❓ Questions?
- Use the discussion forum
- Attend office hours: [Your office hours]
- Email: [Your email]

Good luck!
Dr. [Your Name]
```

---

## Repository Maintenance Tips

### If Students Report Issues:

**Issue**: "I can't fork the repository"
- Check repository is PUBLIC
- Verify the URL is correct
- Ask student to log in to GitHub first

**Issue**: "The code doesn't compile"
- Verify SchedulerSimulation.java compiles on your machine
- Check if student has JDK installed
- Ensure they haven't modified the code incorrectly

**Issue**: "I get different output than my classmate"
- This is EXPECTED - each student has a unique student ID
- The output should be different for each student

### Updating the Repository:

If you need to fix something **after students have forked**:

```bash
cd OS-Assignment1-Starter
# Make your changes
git add .
git commit -m "Fix: [describe what you fixed]"
git push origin main
```

**Note**: Students who already forked won't automatically get updates. You'll need to announce they should sync their fork or apply the fix manually.

---

## Grading Setup

Use the **SIMPLE_GRADING_CHECKLIST.md** file for grading. For each student:

1. Open their repository
2. Check each component using the checklist
3. Watch their video
4. Fill out the grading form
5. Time estimate: ~15-20 minutes per student

### Recommended Grading Order:

1. **Quick scan** (3 min):
   - Repository structure
   - Commit history
   - Files present

2. **Code review** (5 min):
   - Student ID set correctly
   - Features implemented
   - Code quality

3. **Documentation review** (4 min):
   - DEVELOPMENT_LOG.md
   - REFLECTION.md
   - ANSWERS.md

4. **Video review** (3 min):
   - Watch at 1.5x speed if clear
   - Verify student understands their code
   - Check all requirements covered

5. **Calculate grade** (1 min):
   - Add up scores
   - Apply penalties
   - Record in gradebook

---

## Student GitHub Email Verification

To verify students used university email:

1. Go to their GitHub profile
2. Their university email might not be publicly visible
3. Check their commit history - email shows in commits
4. Or ask them to screenshot their GitHub settings

**Command to check commit email**:
```bash
git log --format='%ae' | head -1
```

This shows the email address used for commits.

---

## FAQ - Instructor Edition

**Q: What if a student sets the wrong student ID?**
A: Their output will be incorrect. They should fix it and recommit. If submitted with wrong ID, apply penalty.

**Q: Can students work in pairs?**
A: No, this is individual work. Each student must have their own repository and unique output.

**Q: What if two students have identical code?**
A: Check their student IDs - outputs should differ. If IDs differ but code is identical in modifications, investigate for plagiarism.

**Q: A student made all commits in the last hour before deadline**
A: Apply the -0.5 marks penalty. The purpose is to show development progression.

**Q: How do I handle late submissions?**
A: Check the last commit timestamp before the deadline. -1 mark per day late (24-hour periods).

**Q: What if the video link doesn't work?**
A: Contact student immediately to fix. If not fixed within 24 hours, apply -0.5 marks penalty.

---

## Support Resources for Students

Share these resources if students struggle:

### Java Threading:
- Oracle Java Tutorials: https://docs.oracle.com/javase/tutorial/essential/concurrency/
- Textbook: Chapter 4

### Git & GitHub:
- GitHub Guides: https://guides.github.com/
- Git Cheat Sheet: https://education.github.com/git-cheat-sheet-education.pdf

### JDK Installation:
- Windows: https://www.oracle.com/java/technologies/downloads/
- Mac: `brew install openjdk@17`
- Linux: `sudo apt install openjdk-17-jdk`

---

## Troubleshooting Common Student Issues

### "javac is not recognized"
**Solution**: Install JDK and set PATH
- Windows: Add `C:\Program Files\Java\jdk-17\bin` to PATH
- Mac/Linux: Usually automatic with package manager

### "Permission denied" when pushing to Git
**Solution**: Set up authentication
- Use Personal Access Token (not password)
- Or set up SSH keys

### "My fork is behind the original"
**Solution**: This is OK - students don't need to sync
- Unless you've made critical fixes, they can ignore this

### "I can't make my repository public"
**Solution**: 
- Check GitHub account verification
- Free accounts can make unlimited public repos
- Student might need to verify email first

---

## Checklist Before Distributing Assignment

- [ ] Repository created on GitHub
- [ ] Repository is PUBLIC
- [ ] All files are present and correct
- [ ] SchedulerSimulation.java compiles successfully
- [ ] README.md displays correctly on GitHub
- [ ] Tested forking process
- [ ] Updated LaTeX document with actual repository URL
- [ ] Compiled PDF with correct URL
- [ ] Uploaded PDF to Blackboard
- [ ] Posted announcement with links
- [ ] Grading checklist printed/ready
- [ ] Calendar reminder set for deadline

---

## Contact Information

If you need help with this setup:
- GitHub Education: education@github.com
- GitHub Documentation: https://docs.github.com

---

**Repository URL**: `https://github.com/YOUR_USERNAME/OS-Assignment1-Starter`

Remember to replace `YOUR_USERNAME` with your actual GitHub username throughout this guide!
