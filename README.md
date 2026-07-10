## Meeting Minutes Skill

This skill file was created as a means to help provide a sense of standardization to meeting minutes generated as part of my day job.
The skill expects to be given a transcript file that it will then process to generate the minutes from.
It instructs the model to create, by default, terse minutes, but you have the option increase the verbosity using the switches: `standard` or `verbose`.
The switches do not alter the factual information of the minutes, but instead reduce the amount of text produced to convey the information.
The rendered meeting minutes are output as both PDF and Markdown files.

By default, the skill file will turn a sentence like `The problem with Q1's forecast is that it excludes key information.` into `Q1's forecast excludes key information.`

## Document Mode

This skill allows for you to generate two types of meeting-related documents:

1. `minutes`
2. `summary`

Minutes is the default document mode and it best suited for high-level meetings.
Summary is a special document mode that strips out unnecessary sections and forces the document to be brief.

In summary mode, the document is forced to use `terse` verbosity, but the rest of the options available in **Customization** are still selectable.
The document length in `summary` mode, uses the rule of thumb of 1 page per 30 minutes (making use of timestamps in `.vtt` files, if available).
If the meeting length is unknown, the document is capped to 3 pages under the assumption that the majority of meetings do not exceed 90 minutes.

## Document Structure

The generated document has the following sections:

| Section                   |   Minutes |   Summary |
| :---:                     | :---:     | :---:     |
| Title Page                | Yes       | Yes       |
| Key Points                | Yes       | Yes       |
| Supporting Data           | Yes*      | No        |
| Questions and Concerns    | Yes*      | No        |
| Action Items              | Yes       | Yes       |
| Motions and Resolutions   | Yes*      | No        |
| Decisions                 | Yes       | Yes       |
| Follow-Up & Next Meeting  | Yes       | Yes       |

*: Optional section the user can opt to exclude.

## Accepted Transcript File Formats

This skill file works with the following transcript document formats:

- `.doc`
- `.docx`
- `.md`
- `.pdf`
- `.txt`
- `.vtt`

## Customization

For the PDF files, glyph-friendly font options are used with the default being `DejaVu Serif`.
You have the option to change between the other font options:

- `Liberation Serif`
- `Noto Serif`

> [!NOTE]
> Serif fonts were chosen to aid readability.

You also have the option to to modify the font size to anything from `10pt` to `20pt`.
For the page size, the default is set to `Letter`, but you have the option to use the following other page sizes:

- `A4`
- `Legal`
- `Tabloid/Ledger`

## Example Content

Examples of the generated `minutes` and `summary` document styles can be found in [docs/](./docs)
For the examples, all sections are shown with the default options used.

> [!NOTE]
> These documents were generated randomly by Claude Sonnet 5. All similarity to actual events is purely coincidental.

## License

This skill file is licensed under the MIT license.
For the full license text, refer to [LICENSE](./LICENSE).
