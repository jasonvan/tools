# Document Size Convertor

## Description
A simple HTML/CSS/JavaScript tool that converts PDFs between common page sizes with automatic detection and aspect-ratio-preserving scaling.

## Supported Page Sizes
- **Letter**: 8.5"×11" (612×792pt) - North American standard
- **Legal**: 8.5"×14" (612×1008pt) - Legal documents
- **Tabloid**: 11"×17" (792×1224pt) - Presentations, posters
- **A4**: 8.27"×11.69" (595×842pt) - International standard
- **A3**: 11.69"×16.54" (842×1191pt) - Large format, double A4
- **A5**: 5.83"×8.27" (420×595pt) - Small format, half A4

## Prompt History
1. Initial request: "I'd like to make a simple HTML, CSS, JS app that takes a PDF and converts it to/from letter to A4. No react. Don't call this pdf-converter because it is really just converting any letter-sized document to A4 and vice-versa. I will add additional size conversions later. How about document-size-convertor."
2. Enhancement: "Add Legal, A3, A5, tabloid" - Added 4 additional page sizes and implemented dynamic radio button generation with grid layout.
3. UI improvements:
   - Made all 6 format options visible from the start (no longer hidden until file upload)
   - Moved format descriptions to radio buttons as separate italic lines with lighter color
   - Replaced JavaScript alert() dialogs with visual error messages (red banner with auto-dismiss and close button)
   - Simplified info section by removing redundant page size grid

## Technical Details
- **Library**: pdf-lib v1.17.1 (loaded from CDN)
- **Processing**: Client-side only (no server uploads)
- **Features**:
  - Automatic page size detection
  - Drag & drop file upload
  - All 6 format options visible upfront
  - Aspect ratio preservation
  - Content centering
  - Scale preview showing percentage
  - Progress indicator for multi-page PDFs
  - File size validation (50MB limit)
  - Visual error messages with auto-dismiss

## Source/Inspiration
Inspired by [Useful patterns for building HTML tools](https://simonwillison.net/2025/Dec/10/html-tools/)

## Model Used
Claude Sonnet 4.5 (claude-sonnet-4-5-20250929)

## Known Limitations
- Form fillable PDFs: form fields may get adjusted or misaligned when the PDF is scaled
- Encrypted/password-protected PDFs are not supported
- Maximum file size is 50MB
- Mixed page sizes in a single PDF will be converted uniformly
- Output files may be larger than originals (no compression applied)

## Future Enhancements
- Additional paper sizes (B series, Folio, Executive, etc.)
- Batch conversion support (multiple files at once)
- Custom page size input
- PDF compression option
