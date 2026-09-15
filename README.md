# Coding refresher: R and GitHub

First-class activity for **Data Science for Environmental Policy (DSEP)** at
ETH Zurich. This is a short, hands-on refresher rather than a comprehensive module.

## Learning goals

By the end of the activity, students can:

- distinguish R, R packages, and R projects;
- work with objects, vectors, data frames, and missing values;
- filter, summarize, and visualize a small environmental dataset;
- define a simple function; and
- review, commit, and push a change to GitHub.

## Before class

All students use RStudio throughout the course. Choose one of two ways to run
the same lesson:

- **RStudio in GitHub Codespaces:** use the prepared browser-based environment.
	R, RStudio Server, Quarto, Pandoc, and the lesson packages are installed
	automatically.
- **RStudio on your computer:** install
	[R](https://cran.r-project.org/),
	[RStudio Desktop](https://posit.co/download/rstudio-desktop/), and
	[Git](https://git-scm.com/downloads).

### Open RStudio in Codespaces

1. Open this repository on GitHub.
2. Select **Code > Codespaces > Create codespace on main**.
3. Wait for the container to finish building. The first build installs the
	 course software and can take several minutes.
4. In the Codespaces editor, open the **Ports** panel, find the private port
	`8787` labeled **RStudio IDE**, and select its globe icon to open it in the
	same browser where you are signed in to GitHub.
5. In RStudio, open `coding-intro.Rproj`, then open `coding-intro.qmd`.

Codespaces authenticates access to the forwarded RStudio page. The configured
single-user RStudio session should not require a separate RStudio password.
Keep port `8787` **Private** because RStudio's own login is disabled inside the
single-user Codespace.

#### If RStudio shows HTTP ERROR 401

A `401` page means that RStudio is running, but GitHub did not authenticate the
request to the private forwarded port. It is not an R error. Try these steps in
order:

1. Close the tab showing the `401` error. Do not reuse its URL or an old
	bookmark.
2. Open [github.com](https://github.com/) and confirm that you are signed in to
	the same GitHub account that owns the Codespace.
3. Return to the Codespaces editor and open the **Ports** panel.
4. Right-click port `8787` and confirm **Port Visibility > Private**.
5. Right-click port `8787` again and select **Open in Browser**, or select its
	globe icon. Open it in the same non-private browser window where you are
	signed in to GitHub.
6. If the error remains, reload the Codespaces editor and open the port from
	the **Ports** panel again.

If GitHub's saved browser data is stale, reset it and sign in again:

- **Chrome or Edge:** select the site-controls icon beside the address bar,
  open **Cookies and site data > Manage on-device site data**, and remove saved
  data for `github.dev` and `app.github.dev`. If those controls are unavailable,
  open the browser's privacy settings and search its site-data list for
  `github`. Close private or Incognito windows before retrying.
- **Safari:** open **Safari > Settings > Privacy > Manage Website Data**,
  search for `github`, remove entries for `github.dev` and `app.github.dev`,
  then sign in to GitHub again. If Safari continues to reject the authorization
  redirect, try Chrome in a normal window.
- **Firefox:** open the Codespaces editor, select the shield beside the address
  bar, disable **Enhanced Tracking Protection** for that site, reload, and open
  port `8787` from the **Ports** panel again.

Do not change port `8787` to **Public**. The single-user RStudio session has no
separate RStudio password and relies on Codespaces' private-port authentication.

If this repository was already open in a Codespace before the container setup
changed, rebuild it from the Codespaces editor with **Command Palette >
Codespaces: Rebuild Container**, then reopen port `8787`.

### Open RStudio locally

Clone or download the repository, then open `coding-intro.Rproj` in RStudio.
Install the lesson packages once from the R Console:

```r
install.packages(c("dplyr", "ggplot2", "knitr"))
```

### Work through the lesson

In either environment, open `coding-intro.qmd`. Use the green triangle on a
code chunk to run it. RStudio displays output and plots directly below the
chunk. Run chunks from top to bottom because later examples use objects created
earlier.

Select **Render** to create the complete HTML workbook, or run this command in
RStudio's terminal:

```bash
quarto render coding-intro.qmd
```

Current versions of RStudio Desktop include Quarto. The Codespace installs
Quarto and Pandoc automatically. If **Render** is unavailable locally, install
the [Quarto CLI](https://quarto.org/docs/get-started/).

Package versions installed from CRAN may change over time. If exact
reproducibility between local computers and Codespaces becomes necessary, use
`renv` to record and restore package versions.

## Suggested 45-minute sequence

| Time | Activity |
|---:|---|
| 0-5 min | Open the repository; distinguish the editor, R Console, files, Git, and GitHub |
| 5-10 min | Install versus load a package; find help |
| 10-20 min | Objects, vectors, data frames, and missing values |
| 20-30 min | Filter, summarize, and plot the `airquality` data |
| 30-35 min | Functions and reading an error message |
| 35-45 min | Make a change, inspect the diff, commit, and push |

For mixed-experience groups, ask students to work in pairs with one person
driving and the other explaining what each line should do. Switch roles before
the plotting section. The practice chunks do not run automatically, so the
starter workbook renders before students complete them.

## GitHub workflow

Students use RStudio's terminal for the Git workflow. Open it with **Tools >
Terminal > New Terminal**, then have them run
one command at a time and inspect the output before continuing:

```bash
git pull
git status
git diff
git add coding-intro.qmd
git status
git diff --staged
git commit -m "Complete R coding refresher"
git push
```

If `git push` is rejected, first check that the student is working in their
assigned repository and is signed in to the correct GitHub account. Do not put
access tokens, passwords, private data, or credentials in the repository.

## Files

- `coding-intro.qmd`: student-facing lesson, practice prompts, and solutions
- `coding-intro.Rproj`: opens the repository as an RStudio project
- `.devcontainer/devcontainer.json`: reproducible RStudio Codespaces setup
- `README.md`: setup and facilitation notes

The activity uses R's built-in `airquality` data, so it does not require a data
download or an internet connection after packages are installed.