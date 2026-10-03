@'
# Patch Notes

## Summary

I reviewed the React frontend, Spring Boot API, and H2 query layer and focused on correctness issues that could produce incorrect results or server errors.

## Changes

- Fixed task search/status filtering in `TaskRepository.java` by grouping the title/description `OR` conditions so the status filter applies consistently.
- Added pagination validation in `TaskController.java`. Invalid page numbers and page sizes now return HTTP 400 instead of causing server errors or meaningless empty responses.

## Not Changed

I did not rewrite the application or change the Oracle reference SQL because the running H2-backed application was the priority within the assessment timebox. I also did not remove the controller's artificial delay because my measurements did not show a clear user-visible difference.

## Biggest Remaining Risk

The controller still performs pagination after loading all matching tasks into memory, which may become inefficient as the dataset grows.

## Tools / AI

I used ChatGPT to help inspect the code, identify test cases, and reason about SQL operator precedence and pagination validation. I reproduced the issues locally, verified the fixes manually, and reviewed the final changes before committing them.
'@ | Set-Content -Path .\NOTES.md -Encoding UTF8