
---

### What is a Branch in Git?

>A branch is a copy of your code where you can make changes **without affecting the 
>main project**.

### Why use branches?

- Work on features or bug fixes **separately**
- Keep the main branch (usually `main`) **clean and working**
- Collaborate with teams safely

---
## Project: College Website for an Event

1. You start with your `main` branch:
```sh
git init
git add .
git commit -m "Initial homepage"
```

2. You want to add a **new gallery page**, but don’t want to break the homepage:
```sh
git checkout -b add-gallery
```
✅ You are now in a **new branch** called `add-gallery`

3. Add new files like `gallery.html` and commit them:
```sh
git add gallery.html
git commit -m "Add gallery page"
```

4. Switch back to the main branch:
```sh
git checkout main
```

5. Merge the gallery work into main:
```sh
git merge add-gallery
```
>After merging locally: `git push origin main`
>GitHub will now have your updated project **with the new gallery**.

### Diagram:
```sql 
main ───●────●────●──────────────▶
         \             ↑
      add-gallery ──●──●── Merge
```
###  Commands Summary:

|Action|Command|
|---|---|
|Create new branch|`git branch branch-name`|
|Switch to branch|`git checkout branch-name`|
|Create & switch|`git checkout -b branch-name`|
|See all branches|`git branch`|
|Merge to current|`git merge branch-name`|
|Delete branch|`git branch -d branch-name`|