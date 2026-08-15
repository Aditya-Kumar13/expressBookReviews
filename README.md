# Express Book Review — IBM Capstone

## 1. Setup

```bash
npm install
npm start
```
Server runs on `http://localhost:5000`.

## 2. Task 1 — Fork confirmation

On GitHub: fork `ibm-developer-skills-network/expressBookReview` into your own
account (Fork button, top right of the repo page), then clone your fork and
run:

```bash
git remote -v
```

Expected output showing the fork lineage:
```
origin    https://github.com/<your-username>/expressBookReview.git (fetch)
origin    https://github.com/<your-username>/expressBookReview.git (push)
```
Screenshot the GitHub repo page too — it shows "forked from
ibm-developer-skills-network/expressBookReview" directly under the repo name.
Save this as `githubrepo`.

## 3. Task 2 — Get all books
```bash
curl -s http://localhost:5000/
```
Returns the full books object (all 10 books). Save as `getallbooks`.

## 4. Task 3 — Get book by ISBN
```bash
curl -s http://localhost:5000/isbn/1
```
Save as `getbooksbyISBN`.

## 5. Task 4 — Get books by author
```bash
curl -s http://localhost:5000/author/Homer
```
Save as `getbooksbyauthor`.

## 6. Task 5 — Get books by title
```bash
curl -s "http://localhost:5000/title/The%20Iliad"
```
Save as `getbooksbytitle`.

## 7. Task 6 — Get book review
```bash
curl -s http://localhost:5000/review/1
```
(Returns `{}` before any review is added — that's expected/correct.)
Save as `getbookreview`.

## 8. Task 7 — Register a new user
```bash
curl -s -X POST http://localhost:5000/register \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","password":"testpass"}'
```
Save as `register`.

## 9. Task 8 — Login
```bash
curl -s -c cookies.txt -X POST http://localhost:5000/customer/login \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","password":"testpass"}'
```
The `-c cookies.txt` saves the session cookie — you need it for tasks 9 & 10.
Save as `login`.

## 10. Task 9 — Add/modify a review
```bash
curl -s -b cookies.txt -X PUT \
  "http://localhost:5000/customer/auth/review/1?review=Amazing%20read,%20highly%20recommend!"
```
Save as `reviewadded`.

## 11. Task 10 — Delete a review
```bash
curl -s -b cookies.txt -X DELETE http://localhost:5000/customer/auth/review/1
```
Save as `deletereview`.

## 12. Task 11 — general.js with Axios

`router/general.js` includes, in addition to the Express route handlers,
four standalone functions at the bottom of the file that call those same
endpoints using **Axios** with **Promises / async-await**:

- `getAllBooks()` — async/await
- `getBookByISBN(isbn)` — `.then()/.catch()` promise chain
- `getBooksByAuthor(author)` — async/await
- `getBooksByTitle(title)` — async/await

Push this file to your forked repo and submit its GitHub URL, e.g.:
`https://github.com/<your-username>/expressBookReview/blob/main/router/general.js`

---

## Pushing to GitHub

```bash
git init
git remote add origin https://github.com/<your-username>/expressBookReview.git
git add .
git commit -m "Complete Express Book Review capstone"
git branch -M main
git push -u origin main
```
