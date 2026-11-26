# Review cards: setup guide

Three files make the tool. Keep them together in one folder:

- `index.html` is the tool. You only edit the title and intro text near the top of its `<script>` section (`SETTINGS`).
- `topics.csv` is the topic deck (one column, `topic`).
- `tasks.csv` is the task deck (two columns, `front` and `back`).

## 1. Put it online (GitHub Pages)

1. Sign in at github.com and create a new **public** repository (for example `review-cards`).
2. Click **Add file > Upload files**, drag in the three files, and click **Commit changes**.
3. Go to **Settings > Pages**. Under "Build and deployment," choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. After a minute or two your tool is live at `https://YOUR-USERNAME.github.io/review-cards/`.

Cloudflare Pages works too: **Workers & Pages > Create > Pages > Upload assets**, then drag in the folder.

## 2. Embed it in Canvas

Edit a Canvas Page, switch to the **raw HTML editor** (the `</>` icon), and paste:

```html
<iframe src="https://YOUR-USERNAME.github.io/review-cards/"
        width="100%" height="780" style="border:0;"
        title="Precalculus review cards"></iframe>
<p><a href="https://YOUR-USERNAME.github.io/review-cards/" target="_blank" rel="noopener">Open the review cards in a new tab</a></p>
```

Keep the "open in a new tab" link. It is the easiest way for students on phones, and it is your backup if your school's Canvas blocks outside iframes (if the frame shows up blank, ask your Canvas admin to allow `github.io`).

## 3. Edit the cards

Open the CSV files in Excel or Google Sheets, edit, then export as **CSV (UTF-8)** and replace the file in your repository (**Add file > Upload files**, same file name). Changes show up within a few minutes.

- Keep the header row (`topic` in topics.csv; `front,back` in tasks.csv).
- One card per row. Add as many rows as you like.
- A task with an empty `back` shows no flip button.
- Line breaks inside a cell are kept on the card.

## 4. Typing math

Put LaTeX between dollar signs, and it displays as typeset math:

| You type | Students see |
| --- | --- |
| `$\dfrac{f(x+h)-f(x)}{h}$` | the difference quotient as a stacked fraction |
| `$\lim_{x\to\infty}f(x)$` | a limit with the arrow under "lim" |
| `$$y=A\sin(B(x-C))+D$$` | the same idea centered on its own line (double dollar signs) |

`\( ... \)` also works. Math works on topic cards, task fronts, and task backs. Avoid using a dollar sign for money on a card (write "5 dollars"), since `$` starts math.

## Testing tip

If you double-click `index.html` on your computer, the browser blocks it from reading the CSV files, so you will see a small built-in sample and a yellow note. That is normal. Test on the hosted link instead, or run `python3 -m http.server` in the folder and visit `http://localhost:8000`.

## How the dealing works

- Two topic cards and two task cards are on the table at once.
- Students tap one topic and one task to choose them, and can flip any task card to read the back.
- "Done: replace these cards" replaces only the two chosen cards. The other two stay.
- Used cards go to a discard pile. When a deck runs out, the discards are reshuffled, and a card is never replaced by the one just used.
- "Start over" reshuffles everything and clears the list of pairs.
