## Meeting Minutes Skill

This skill file was created as a means to help provide a sense of standardization to meeting minutes generated as part of my day job.
The skill expects to be given a transcript file that it will then process to generate the minutes from.
It instructs the model to create, by default, terse minutes, but you have the option increase the verbosity using the switches: `standard` or `verbose`.
The switches do not alter the factual information of the minutes, but instead reduce the amount of text produced to convey the information.
The rendered meeting minutes are output as both PDF and Markdown files.

By default, the skill file will turn a sentence like `The problem with Q1's forecast is that it excludes key information.` into `Q1's forecast excludes key information.`

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

## License

This skill file is licensed under the MIT license.
For the full license text, refer to [LICENSE](./LICENSE).
