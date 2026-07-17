# 1) HTML CSS JS

## Fresher Frontend Portfolio — 3 Projects

Build each project twice:
1. **Phase 1 — HTML, CSS, JS (vanilla).** Get the logic and UI states right without a framework.
2. **Phase 2 — React + Tailwind.** Rebuild the same project as a React app styled with Tailwind, reusing what you learned about state and edge cases in Phase 1.

Two versions of the same project is a strong portfolio signal — it shows you understand *why* React/Tailwind help, not just how to use them.

For every project (both phases), ship:
- A deployed link (Vercel/Netlify/GitHub Pages)
- A public GitHub repo with clean commit history
- A README (what it does, tech used, how to run it)
- A short project note (template at the end of each section)

**Suggested repo structure:**
```
project-name/
  vanilla/     -> HTML, CSS, JS version
  react/       -> React + Tailwind version
  README.md    -> links to both, notes on what changed between versions
```

---

## Project 1: Job Application Form

A multi-step job application form that feels like a small product workflow.

### Required Features (both phases)
- 3–4 steps
- Required fields
- Inline validation
- Review step
- Back and Next buttons
- Disabled submit while invalid
- Success state
- Responsive layout
- Accessible labels
- Error text that helps the user fix the issue

### Review Details That Matter
- Error text should be next to the field or summarized clearly.
- The Back button should not erase earlier answers.
- The Review step should show the same values the user entered.
- The form should work without relying only on placeholder text.

### Phase 1 — HTML, CSS, JS
- Use plain JS objects to hold form state (e.g. `let formData = {}`).
- Show/hide steps by toggling a CSS class (e.g. `.step.active`).
- Validate with plain functions run on Next click and on blur.
- Store progress in `localStorage` manually with `JSON.stringify`/`parse`.

### Phase 2 — React + Tailwind
- Move form state into a single `useState` object or `useReducer`.
- Render steps conditionally based on a `currentStep` state value.
- Style with Tailwind utility classes; use `focus:`, `disabled:`, `aria-invalid:`-driven classes for states.
- Extract a reusable `<FormField>` component (label + input + error message).
- Compare: how much boilerplate did React remove for step-switching and re-renders?

### Project Note Template
```
What I built:
A three-step job application form with validation and review — built once in vanilla JS, then rebuilt in React + Tailwind.

Frontend decisions:
I kept all form values in one state object so the review screen could read them easily.
I validate each step before moving forward.

What changed between versions:
[e.g. "React let me derive the review screen straight from state instead of re-reading the DOM."]

What I learned:
Form UX is not only inputs. Disabled states, error messages, and review screens matter.

What I would improve:
I would add server-side validation and better autosave.
```

---

## Project 2: GitHub Profile Finder

An API-backed search page using the GitHub REST API.

### Required Features (both phases)
- Search or filter
- Loading state
- Empty state
- Error state
- Retry button
- Details view
- Responsive layout

### Review Details That Matter
- Loading, empty, and error states should be visually different.
- Failed requests should not leave old results in a confusing state.
- The details view should have a clear way back to the results.
- If search is debounced, the README should mention why.

### Phase 1 — HTML, CSS, JS
- Use `fetch` + `async/await` directly in an event handler.
- Track a simple `let isLoading` flag and toggle DOM elements manually.
- Write your own debounce with `setTimeout`/`clearTimeout`.
- Render results by building HTML strings or DOM nodes and injecting into a container.

### Phase 2 — React + Tailwind
- Move fetch logic into a `useEffect` (or a custom `useGitHubSearch` hook).
- Use `useState` for `query`, `results`, `status` (`idle`/`loading`/`success`/`error`).
- Handle race conditions with an `AbortController` or a "latest request wins" check inside `useEffect`'s cleanup.
- Style loading/empty/error states with conditional Tailwind classes.
- Compare: how did moving to a custom hook change how easy it was to cancel stale requests?

### Project Note Template
```
What I built:
A GitHub profile finder with search, filters, and a details view — built once in vanilla JS, then rebuilt in React + Tailwind.

Frontend decisions:
I separated the search input from the submitted query so the API is not called on every keypress.

What changed between versions:
[e.g. "The vanilla version needed manual cleanup for stale fetches; React's useEffect cleanup made that explicit."]

What I learned:
The empty state and error state need different messages.

What I would improve:
I would add pagination and cache repeated searches.
```

---

## Project 3: Expense Tracker

An app where user actions change state and totals update automatically.

### Required Features (both phases)
- Add item
- Edit or remove item
- Derived total or summary
- Empty state
- Confirmation for destructive action
- Local persistence
- Mobile layout

### Review Details That Matter
- Totals should be derived from items, not stored separately without a reason.
- Delete actions should be recoverable or confirmed.
- Local storage should handle empty or outdated data safely.
- Empty states should tell the user what action to take next.

### Phase 1 — HTML, CSS, JS
- Store expenses in a JS array; re-render the list by clearing and rebuilding the DOM.
- Calculate the total by looping over the array on every render.
- Read/write the array to `localStorage`, with a `try/catch` for corrupted data.
- Use a plain `confirm()` or a custom modal for delete confirmation.

### Phase 2 — React + Tailwind
- Store expenses in `useState` (array of objects); render with `.map()`.
- Calculate the total with a derived value (or `useMemo` if the list gets large) instead of a separate state variable.
- Sync to `localStorage` in a `useEffect` that runs on state change; guard `JSON.parse` on load.
- Build a small confirm dialog component instead of `window.confirm`.
- Compare: where did React make "total goes out of sync with items" harder to accidentally cause?

### Project Note Template
```
What I built:
An expense tracker with add, edit, delete, and a running total — built once in vanilla JS, then rebuilt in React + Tailwind.

Frontend decisions:
I derived the total from the current list of expenses instead of storing it separately, to avoid it going out of sync.

What changed between versions:
[e.g. "In React, deriving the total from state each render removed a whole class of sync bugs I had in the vanilla version."]

What I learned:
Local storage needs guards for missing or malformed data.

What I would improve:
I would add categories and an undo option for deletes.
```

---


For a **fresher frontend developer (HTML + CSS + JavaScript) machine coding round**, you should prioritize problems that are repeatedly asked because they test practical frontend skills.

I have ranked them based on:

* Interview frequency
* Real-world frontend usage
* Concepts covered
* Difficulty suitable for fresher/SDE-1

# 🔥 Top 30 Most Important Machine Coding Problems (Fresher Level)

| Rank | Problem                                      | Main Concepts Tested                                   |
| ---- | -------------------------------------------- | ------------------------------------------------------ |
| 1    | **Todo List (CRUD)**                         | DOM manipulation, events, localStorage, state handling |
| 2    | **Autocomplete / Typeahead**                 | Debounce, API calls, filtering, async JS               |
| 3    | **Debounced Search (Flipkart/Amazon style)** | Debouncing, fetch API, optimization                    |
| 4    | **Modal Component**                          | DOM, events, reusable UI, accessibility                |
| 5    | **Dropdown Component**                       | Click events, outside click detection                  |
| 6    | **Accordion**                                | State handling, DOM updates                            |
| 7    | **Tabs Component**                           | Component logic, event handling                        |
| 8    | **Form Validation**                          | Input handling, regex, errors                          |
| 9    | **Multi Step Form**                          | Form state, validation flow                            |
| 10   | **Pagination**                               | Data rendering, page management                        |
| 11   | **Infinite Scroll**                          | Intersection Observer, lazy loading                    |
| 12   | **Data Table**                               | Sorting, filtering, pagination                         |
| 13   | **Image Carousel**                           | Timers, DOM updates, CSS transitions                   |
| 14   | **Image Gallery with Search + Pagination**   | API, filtering, pagination                             |
| 15   | **Stopwatch**                                | setInterval, clearInterval                             |
| 16   | **Countdown Timer**                          | Date calculations, timers                              |
| 17   | **Progress Bar**                             | Animation, async updates                               |
| 18   | **Star Rating Component**                    | Mouse events, dynamic UI                               |
| 19   | **Drag and Drop**                            | Drag events, DOM manipulation                          |
| 20   | **Kanban Board**                             | Drag/drop, complex state handling                      |
| 21   | **Nested Comments System**                   | Recursion, tree data                                   |
| 22   | **Job Board**                                | API integration, cards, filtering                      |
| 23   | **OTP Input Component**                      | Keyboard events, focus management                      |
| 24   | **Password Generator**                       | Randomization, DOM updates                             |
| 25   | **Calculator**                               | JavaScript logic, events                               |
| 26   | **Digital Clock**                            | Date API, timers                                       |
| 27   | **Responsive Navbar**                        | HTML/CSS, responsive design                            |
| 28   | **Holy Grail Layout**                        | Flexbox/Grid                                           |
| 29   | **File Explorer**                            | Recursive rendering                                    |
| 30   | **Transfer List**                            | Array manipulation, moving items                       |

---

# ⚡ Next 20 Important Problems (After Top 30)

These are valuable but slightly lower priority.

| Rank | Problem               | Main Concepts Tested       |
| ---- | --------------------- | -------------------------- |
| 31   | Like Button           | State toggle               |
| 32   | Poll Widget           | Dynamic updates            |
| 33   | Quiz App              | State management, timers   |
| 34   | Traffic Light         | setTimeout, state cycle    |
| 35   | Analog Clock          | CSS transform, Date API    |
| 36   | Grid Lights           | Matrix logic, events       |
| 37   | Memory Game           | Arrays, game state         |
| 38   | Tic Tac Toe           | Game logic                 |
| 39   | Snake Game            | Animation, keyboard events |
| 40   | Connect Four          | Complex game logic         |
| 41   | Mortgage Calculator   | Forms, calculations        |
| 42   | Temperature Converter | Input handling             |
| 43   | Flight Booker         | Date handling, forms       |
| 44   | Generate Table        | DOM generation             |
| 45   | Chat Application UI   | Message rendering          |
| 46   | Notification System   | Timers, queues             |
| 47   | Search Filters Panel  | Filtering logic            |
| 48   | Image Lazy Loading    | Performance optimization   |
| 49   | Custom Event Emitter  | JavaScript internals       |
| 50   | Selectable Grid       | Mouse events, coordinates  |

---

# If You Are Applying for Fresher Frontend Roles, Master These 15 First

If you have limited time, do these before anything else:

1. Todo List
2. Autocomplete
3. Debounced Search
4. Modal
5. Dropdown
6. Accordion
7. Tabs
8. Form Validation
9. Pagination
10. Infinite Scroll
11. Data Table
12. Carousel
13. Stopwatch
14. Drag & Drop
15. Kanban Board

These 15 alone cover most **frontend machine coding rounds for 0–2 years experience**.

After completing them, add:

* Nested Comments
* File Explorer
* Job Board
* Image Gallery
* OTP Input

These will make you comfortable with almost any fresher-level frontend machine coding interview.

