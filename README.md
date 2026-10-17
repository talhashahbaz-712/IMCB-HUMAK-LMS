Firebase backend deployment notes

1. Use a TEST Firebase project first. Never run this against the live project until rules and user flows have been verified.
2. Install Firebase CLI, authenticate, and select the test project: firebase use --add
3. From this folder run: npm install --prefix functions
4. Deploy backend only after tests: firebase deploy --only functions,firestore:rules,firestore:indexes
5. Cloud Functions may require the Blaze billing plan. Get project owner/guardian approval before enabling billing, and configure budget alerts.
6. The app calls startLectureQuiz and submitLectureQuiz in the default us-central1 region.
7. Do not deploy only the static site if you want timed quiz auto-grading to work. Netlify does not deploy Firebase Cloud Functions or Firestore rules.
8. Firestore rules have not been emulator-validated in this package. Test role access, legacy records, OTP/signup, approvals, tasks, materials, attendance, submissions, and notification read receipts before production.
