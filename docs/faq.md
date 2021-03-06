---
layout: default
title: FAQ
nav_order: 4
---

# Frequently Asked Questions

## What do I do if I: found a bug? am getting an error? have a suggestion?

Please search through [the existing issue list](https://github.com/ljhopkins2/broadcastify-archtk/issues) to look for resolutions (or vote up an existing unresolved issue), and submit a new issue if necessary.


## What does the WebDriverException mean?

```python
WebDriverException: Message: 'chromedriver' executable needs to be in PATH.
```

This error message means that the WebDriver for your browser is not in your operating system's `PATH` environment variable, so Selenium can't find a driver to use for scraping. The easiest solution is to specify the path to the WebDriver in the `webdriver_path` argument when [instantiating](/broadcastify-archtk/user-guide/creating-an-archive.html) a `BroadcastifyArchive` object. A cleaner solution is to [move the driver](/broadcastify-archtk/user-guide/installation.html#place-it-in-the-os-path) into a directory in the `PATH`.

## What does the TimeoutException mean?

```python
TimeoutException: Message:
```

This error message means that Selenium timed out waiting for a particular page element to load. The toolkit uses these elements to determine when the archive navigation page (either the calendar or the archive times table) has refreshed, since the data are loaded asynchronously. I've tried to catch the most common reasons for this error and raise a more meaningful exception.

If you see this error, it could mean that (1) something interrupted the refresh of the navigation page (e.g. network issues) or (2) I missed an opportunity to catch and raise a more specific exception. If you're able to replicate the issue after reinstantiating your archive and re-running your code, please take a look at [the issues list](https://github.com/ljhopkins2/broadcastify-archtk/issues) and log one if you don't see a duplicate.
