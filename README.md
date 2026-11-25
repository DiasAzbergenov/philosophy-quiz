# Philosophy Midterm Practice Test

An interactive multiple-choice quiz for preparing for a university Philosophy midterm (Lectures 1–6). It runs entirely in the browser from a single `index.html` file: no server, no build step, no dependencies to install.

> Краткое описание по-русски: интерактивный тест по философии (лекции 1–6), 235 вопросов с 5 вариантами ответа, как на экзамене. Открывается одним файлом `index.html`, интерфейс на русском, вопросы на английском.

## Features

- **Exam mode.** 30 random questions with five answer options each. About half come from Lectures 5 and 6. Answers are shown only at the end. Includes a timer and a question navigator.
- **Practice mode.** Pick any lectures, the source of questions (past exams, lecture slides, or both) and the number of questions (10, 20, 30 or all). Optionally show the correct answer and a short explanation right after each choice.
- **Mistakes review.** Questions you answered wrong are collected automatically; a correct answer removes a question from the list.
- **Results screen.** Score, time, per-lecture breakdown and a review of every mistake with the correct answer.
- **Keyboard support.** Keys `1`–`5` choose an answer; arrow keys and `Enter` move between questions.
- **Light and dark themes**, following the system setting. Works on phones.

## Question bank

235 questions in total.

| Source | Questions |
| --- | --- |
| Past exam papers (unique questions, original wording and distractors) | 83 |
| Lecture slides (written for this project) | 152 |

| Lecture | Topic | Questions |
| --- | --- | --- |
| 1 | Introduction to philosophy | 26 |
| 2.1 | Ancient Indian philosophy | 23 |
| 2.2 | Ancient Chinese philosophy | 15 |
| 3 | Ancient Greek-Roman philosophy | 33 |
| 4.1 | Medieval European philosophy | 26 |
| 4.2 | Medieval Islamic philosophy | 20 |
| 5 | Philosophy of the Renaissance | 39 |
| 6 | Early Modern philosophy | 53 |

## Run locally

Download `index.html` and open it in any modern browser. That is all.

## Host it on GitHub Pages

1. Create a public repository, for example `philosophy-quiz`.
2. Upload `index.html` (and this `README.md`) to the repository root.
3. Open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then save.
4. After a minute or two the quiz is available at `https://<your-username>.github.io/<repository-name>/`.

Other static hosts such as Netlify, Cloudflare Pages or Vercel work the same way: upload the file and you get a link.

## Project structure

```
index.html   the whole app: markup, styles, script and question data
README.md    this file
```

The question data is a JSON array inside `index.html` (`const BANK = [...]`). Each question has:

| Field | Meaning |
| --- | --- |
| `id` | unique number |
| `l` | lecture code: `1`, `2.1`, `2.2`, `3`, `4.1`, `4.2`, `5` or `6` |
| `q` | question text |
| `a` | the correct answer |
| `w` | the four wrong answers |
| `e` | short explanation (Russian, may be empty) |
| `s` | source: `p` for past exams, `s` for slides |

The five options are shuffled every time a question is shown.

## Adding or editing questions

Edit the `BANK` array in `index.html`. Keep exactly four wrong answers in `w`, and make sure no option repeats the correct answer. To change the 30-question exam mix, edit the `quota` object in the `startExam` function.

## Data and privacy

Nothing is sent anywhere. The list of mistakes and the answer statistics are stored in the browser's `localStorage` on the user's own device. If the browser blocks storage, the quiz still works, but progress is lost when the page is closed.

## Known caveats

- **Chinese Legism.** Past exam keys give 9 basic principles, while the current lecture slides list 12. The quiz uses 12 and says so in the explanation. Check with your instructor.
- **Unofficial study aid.** The slide-based questions were written from the lecture slides and may contain mistakes. Always check against your own course materials.
- **Past-exam content.** Questions marked as coming from past exams originate from student-collected exam papers. If your university restricts sharing exam material, remove those questions (`"s":"p"`) before publishing the quiz publicly.

## Fonts

Headings use Manrope and body text uses IBM Plex Sans, both loaded from Google Fonts. If the fonts cannot be loaded, the page falls back to system fonts.

## License

Add a license of your choice before publishing, for example MIT.
