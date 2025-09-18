# Developing

This repository contains a directory per course site we host.

It mostly pulls in content from https://github.com/CodeYourFuture/curriculum/tree/main/common-content

You probably want to read [the upstream developing instructions](https://github.com/CodeYourFuture/curriculum/blob/clean-up-contributing/CONTRIBUTING.md#developing-the-source-website) to get started.

In order to locally develop the site:
1. In the root directory, create a file named `.env` based on `example.env` containing a GitHub token, as per the upstream instructions.
2. `cd` into the directory of the site you want to run. Run `npm i`.
3. While still in the directory of the site you want to run, run `npm run start:dev`.

## Editing upstream content

If you need to edit/add upstream content, the easiest way to do this is to clone it locally, and then edit the `go.mod` file for the site you're editing.

Add a line which reads:

```
replace github.com/CodeYourFuture/curriculum/common-content => /path/to/upstream/common-content
```

e.g.

```
replace github.com/CodeYourFuture/curriculum/common-content => /Users/me/github.com/CodeYourFuture/curriculum/common-content
```

Your site will now read shared content from your local copy (which you can edit locally) rather than upstream.

You should PR and merge your changes upstream, then remove this line and run `go mod get -u` to pull in the newly committed changes.
