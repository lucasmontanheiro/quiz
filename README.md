# 📘 Simple Quiz App

A straightforward, single-page quiz application built with vanilla JavaScript, HTML, and Bootstrap. It dynamically loads quizzes from local JSON files, presents a set of questions to the user, and provides immediate feedback on their score and answers.

## ✨ Features

- **Dynamic Subject Loading**: Quizzes are loaded from a list of subjects defined in `quizzes/subjects.json`.
- **Randomized Questions**: A random subset of 10 questions is selected from the chosen subject for each attempt.
- **Interactive UI**: Clean and responsive interface using Bootstrap.
- **Instant Results**: Users see their score and a detailed breakdown of correct/incorrect answers upon submission.
- **Easily Extensible**: Adding new quizzes is as simple as creating a new JSON file and updating one configuration file.

## 🚀 How to Run

This application is designed to be deployed on static hosting services like GitHub Pages.

### GitHub Pages Deployment

To deploy this quiz application on GitHub Pages:

1.  Push your code to a GitHub repository.
2.  Go to your repository settings on GitHub.
3.  Navigate to the "Pages" section.
4.  Choose your deployment source (e.g., `main` branch, `/docs` folder).
5.  Your site will be deployed to `https://<username>.github.io/<repository-name>/`.

**Best Practices for GitHub Pages:**
*   **Relative Paths:** Ensure all your asset paths (CSS, JS, images, JSON data) are relative to your project root or use absolute paths starting with `/` if your site is deployed to a subpath (e.g., `/your-repo-name/css/style.css`). This project uses relative paths for simplicity.
*   **Case Sensitivity:** GitHub Pages serves files with case sensitivity. Ensure your file names and references match exactly (e.g., `quizzes/subjects.json` is not the same as `Quizzes/Subjects.json`).

This is a simple front-end application with no build step. However, due to browser security policies (CORS), you cannot open `index.html` directly from the file system if you want to fetch the quiz data.

You need to serve the project files from a local web server.

1.  Navigate to the project's root directory in your terminal.
2.  Start a simple local server. If you have Python installed, you can use one of the following commands:

    ```bash
    # For Python 3
    python3 -m http.server
    
    # For Python 2
    python -m SimpleHTTPServer
    ```

3.  Open your web browser and go to `http://localhost:8000`.

## 📝 How to Add a New Quiz

Adding a new quiz subject is designed to be very simple:

### 1. Create the Quiz File

- In the `quizzes/` directory, create a new JSON file (e.g., `my_new_quiz.json`).
- The file must contain a JSON array of question objects. Each object must follow this structure:

  ```json
  [
    {
      "id": "q1",
      "question": "What is the capital of France?",
      "options": {
        "a": "London",
        "b": "Berlin",
        "c": "Paris",
        "d": "Madrid"
      },
      "correct": "c"
    },
    {
      "id": "q2",
      "question": "...",
      "options": { ... },
      "correct": "..."
    }
  ]
  ```
  - The `id` for each question should be unique within that file.
  - The `correct` value must match one of the keys in the `options` object (`a`, `b`, `c`, or `d`).

### 2. Update the Subjects List

- Open the `quizzes/subjects.json` file.
- Add the filename of your new quiz ( **without** the `.json` extension) to the array.

  ```json
  [
    "system_design",
    "caching",
    "my_new_quiz"
  ]
  ```

That's it! The new quiz will now automatically appear in the subject dropdown on the web page.