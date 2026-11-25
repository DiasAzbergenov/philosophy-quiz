# Philosophy Midterm Practice Test

> **Disclaimer / Дисклеймер.** This is an unofficial, student-created study tool containing original practice questions. It is not affiliated with, endorsed by, or approved by the university or the course instructors, and it does not contain actual exam questions or instructor-provided test items. Questions were drafted with the help of an AI model (Claude, Anthropic) and may contain mistakes; always check against your own course materials.
> Неофициальный учебный инструмент, созданный студентом. Вопросы — оригинальные тренировочные; проект не связан с университетом и преподавателями курса и не содержит настоящих экзаменационных вопросов.


An interactive multiple-choice quiz for preparing for a university Philosophy midterm (Lectures 1–6). It runs entirely in the browser from a single `index.html` file: no server, no build step, no dependencies to install.

> Краткое описание по-русски: интерактивный тест по философии (лекции 1–6), 296 вопросов (4–5 вариантов ответа). Все вопросы составлены по слайдам лекций. Открывается одним файлом `index.html`, интерфейс на русском, вопросы на английском.

## AI disclaimer

All materials in this project were created by AI: the quiz application, the question bank, the answer explanations and this README were written by Claude (Claude Sonnet 5.5, a model by Anthropic) at the request of a student. The questions are based only on the course's lecture slides. They have not been reviewed or approved by any instructor or by the university, and they may contain errors or simplifications. Use the quiz only as a practice aid and verify facts against your official course materials.

> Дисклеймер по-русски: все материалы проекта (приложение, банк вопросов, пояснения к ответам и этот README) созданы искусственным интеллектом Claude (модель Claude Sonnet 5.5, Anthropic) по запросу студента. Они основаны только на слайдах лекций, не проверялись преподавателем или университетом и могут содержать ошибки. Используйте тест только для тренировки и сверяйте факты с официальными материалами курса.

## Features

- **Exam mode.** 30 random questions with five answer options each. About half come from Lectures 5 and 6. Answers are shown only at the end. Includes a timer and a question navigator.
- **Practice mode.** Pick any lectures and the number of questions (10, 20, 30 or all). Optionally show the correct answer and a short explanation right after each choice.
- **Mistakes review.** Questions you answered wrong are collected automatically; a correct answer removes a question from the list.
- **Results screen.** Score, time, per-lecture breakdown and a review of every mistake with the correct answer.
- **Keyboard support.** Keys `1`–`5` choose an answer; arrow keys and `Enter` move between questions.
- **Light and dark themes**, following the system setting. Works on phones.

## Question bank

296 practice questions in total. Every question has an explanation.

| Lecture | Topic | Questions |
| --- | --- | --- |
| 1 | Introduction to philosophy | 28 |
| 2.1 | Ancient Indian philosophy | 26 |
| 2.2 | Ancient Chinese philosophy | 19 |
| 3 | Ancient Greek-Roman philosophy | 32 |
| 4.1 | Medieval European philosophy | 23 |
| 4.2 | Medieval Islamic philosophy | 24 |
| 5 | Philosophy of the Renaissance | 52 |
| 6 | Early Modern philosophy | 92 |

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
| `s` | origin marker (`s` or `o`), informational only |

The five options are shuffled every time a question is shown.

## Adding or editing questions

Edit the `BANK` array in `index.html`. Keep exactly four wrong answers in `w`, and make sure no option repeats the correct answer. To change the 30-question exam mix, edit the `quota` object in the `startExam` function.

## Data and privacy

Nothing is sent anywhere. The list of mistakes and the answer statistics are stored in the browser's `localStorage` on the user's own device. If the browser blocks storage, the quiz still works, but progress is lost when the page is closed.

## Known caveats

- **Unofficial, AI-generated study aid.** The questions were written by an AI from the lecture slides and may contain mistakes. Always check against your own course materials (see the AI disclaimer above).

## Fonts

Headings use Manrope and body text uses IBM Plex Sans, both loaded from Google Fonts. If the fonts cannot be loaded, the page falls back to system fonts.

## License

Add a license of your choice before publishing, for example MIT.


## Exam lock

To disable the quiz during an exam window, build with the lock flag:

```bash
python3 build.py              # normal build
EXAM_LOCK=1 python3 build.py  # shows a maintenance notice; the question bank is NOT embedded in index.html
```

Deploy the locked `index.html`, then rebuild without the flag afterwards. `build.py` reads `lect_*.py` and `template.html`; the generated `index.html` and `bank.json` can be committed.
