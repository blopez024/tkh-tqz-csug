# Git Case Study: In-Class Exercise

## Feature-A: Team Member "Eric"

### Objective: Greet the user and ask for their name.

1.  Switch to the Correct Branch:

    ```bash
    git branch
    git switch develop
    ```

2.  Create a Feature Branch:

    ```bash
    git checkout -b feature-a
    ```

3.  Create Files: Create two new files, `welcome.js` and `getName.js`, and add the following code:

    `welcome.js`:

    ```javascript
    import { verifyName } from './getName.js';
    console.log('='.repeat(35));
    console.log('Welcome to eligibility check');
    console.log('='.repeat(35));
    console.log('\n');
    const userName = verifyName(username);
    console.log(`Hello ${userName}!\n`);
    ```

    `getName.js`:

    ```javascript
    export function verifyName() {
      const input = prompt('Enter your name: ');
      return input;
    }
    ```

4.  Add Changes to the Local Repository:

        ```bash
        git add welcome.js getName.js
        git status
        ```

5.  Commit the Changes:

        ```bash
        git commit -m "(Eric E) Feature-A: Show a greeting message to user and ask for their name"
        ```

6.  Push to Remote Repository:

    ```bash
    git push --set-upstream origin feature-a
    ```

7.  Create a Pull Request:

    - On GitHub, create a pull request (PR) from feature-a to develop.

8.  Approve the Pull Request:

    - After creating the pull request, switch the base branch from main to develop and merge the changes.

<br>

## Feature-B: Team Member "Lucy"

### Objective: Verify the user's age and eligibility to vote.

1.  Create and Switch to Feature-B:

    ```bash
    git checkout -b feature-b
    ```

2.  Create Files: Create two new files, `welcome.js` and `validateAge.js`, and add the following code:

    `welcome.js`:

    ```javascript
    import { validateAge } from './validateAge.js';
    const age = validateAge(age);
    ```

    `validateAge.js:`

    ```javascript
    export function validateAge(age) {
      age = parseInt(prompt('Enter your age: '), age);
      if (age < 18) {
        console.log('Not eligible for voting\n\n');
      } else {
        console.log('Eligible for voting\n\n');
      }
    }
    ```

3.  Commit the Changes:

    ```bash
    git add welcome.js validateAge.js
    git commit -m "(Lucy L) Feature-B: Ask the user for their age. A user is only eligible to vote if their age is greater than or equal to 18"
    ```

4.  Push Changes and Create a Pull Request:

    ```bash
    git push --set-upstream origin feature-b
    ```

5.  Resolve Merge Conflicts:

    - Upon checking for merge conflicts, you’ll likely encounter a conflict with `welcome.js`.
    - Edit the file to merge the changes from both branches, as shown below:

      `welcome.js`:

      ```javascript
      import { validateAge } from './validateAge.js';
      import { verifyName } from './getName.js';

      console.log('='.repeat(35));
      console.log('Welcome to eligibility check');
      console.log('='.repeat(35));
      console.log('\n');

      const age = validateAge(age);
      const userName = verifyName(username);
      console.log(`Hello ${userName}!\n`);
      ```

6.  Commit the Merge:

    - Mark the conflict as resolved and commit the changes.

7.  Complete the Pull Request.

<br>

## Feature-C: Team Member "Adam"

### Objective: Add a survey to the user experience.

1. Pull Changes from Develop:

   ```bash
   git pull origin develop
   ```

2. Create Files: Create deliverSurvey.js and update welcome.js:

   `deliverSurvey.js`:

   ```javascript
   export function deliverSurvey() {
     const input = prompt(
       'Would you like to participate in our survey (Y/N): ',
     );
     return input;
   }
   ```

   `welcome.js`:

   ```javascript
   import { validateAge } from './validateAge.js';
   import { verifyName } from './getName.js';
   import { deliverSurvey } from './survey.js';

   console.log('='.repeat(35));
   console.log('Welcome to eligibility check');
   console.log('='.repeat(35));
   console.log('\n');

   const age = validateAge(age);
   const userName = verifyName(username);
   console.log(`Hello ${userName}!\n`);

   const survey_flag = prompt(
     'Would you like to participate in our survey (Y/N): ',
   );
   if (survey_flag == 'Y') deliverSurvey();
   ```

3. Commit and Push Changes:

   ```bash
   git add deliverSurvey.js welcome.js
   git commit -m "(Adam A) Feature-C: Ask the user to participate in a survey about their experience"
   git push --set-upstream origin feature-c
   ```

4. Create and Complete the Pull Request:

   - Review any merge conflicts and resolve them as needed.
   - After testing, merge the `feature-c` branch into `develop`.

5. Merge Develop into Main:

   - Once the `develop` branch is complete and tested, merge it into the `main` branch.
