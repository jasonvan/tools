# Markdown to PDF Converter

A sophisticated single-file web application that converts Markdown documents into beautifully formatted PDF files with live preview and customizable export options.

## Description

This tool allows users to write or paste Markdown content, see a live preview of the rendered output, and export it as a professional PDF document. Perfect for creating reports, documentation, articles, or any printable content from Markdown.

## Key Features

- **Live Markdown Preview**: Real-time rendering of Markdown as you type
- **PDF Export**: Generate high-quality PDF files from your Markdown content
- **Customizable Output**: Configure page size (A4, Letter, Legal), orientation (Portrait, Landscape), and filename
- **localStorage Persistence**: Automatically saves your work to localStorage for recovery between sessions
- **Sample Template**: Load a pre-formatted sample to explore Markdown capabilities
- **Full Markdown Support**: Tables, code blocks, blockquotes, lists, headings, links, images, and more
- **Professional Typography**: Distinctive fonts and styling optimized for print
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices

## Prompt History

### Initial Request
User requested: "Create a new tool called markdown to PDF that can take a markdown file and turn it into a PDF file that can be printed. Use standard HTML, CSS, and vanilla JavaScript with external CDN if required. No React. Create this as a single HTML file."

### Design Direction
Chose a **Modern Publishing House** aesthetic:
- Sophisticated editorial design with emphasis on typography
- Color palette: Deep ink blues, cream paper tones, and gold accents
- Professional, print-ready appearance
- Clean, hierarchical layout

## Technical Details

### External Libraries (CDN)
- **marked.js** (v11.1.1): Markdown parser - converts Markdown syntax to HTML
- **html2pdf.js** (v0.10.1): PDF generation library - converts HTML content to downloadable PDF

### Typography
- **Display Font**: Cormorant Garamond (elegant serif for headings)
- **Body Font**: Work Sans (clean sans-serif for body text and UI)
- Both fonts loaded from Google Fonts

### Color System
```css
--ink-dark: #1a1a2e        /* Primary text, headers */
--ink-medium: #2d3748      /* Secondary text */
--paper-cream: #faf8f3     /* Background accents */
--paper-white: #ffffff     /* Main backgrounds */
--accent-gold: #d4af37     /* Accent borders, highlights */
--accent-burgundy: #8b2635 /* CTAs, links */
--border-light: #e2dfd9    /* Subtle borders */
--text-muted: #6b7280      /* Footer, less important text */
```

### Data Persistence
- **localStorage Key**: `markdownToPdf`
- **Stored Data**:
  - Markdown content
  - Page size setting
  - Orientation setting
  - Filename preference

### PDF Generation Process
1. User enters Markdown in the editor (left panel)
2. Markdown is parsed to HTML using marked.js and shown in preview (right panel)
3. When "Generate PDF" is clicked:
   - HTML is created with inline styles for proper formatting
   - html2pdf.js renders the styled HTML to a PDF
   - PDF is downloaded with the specified filename

### Supported Markdown Features
- Headings (H1-H6)
- Paragraphs
- Bold and italic text
- Links
- Unordered and ordered lists
- Nested lists
- Code blocks with syntax highlighting styles
- Inline code
- Blockquotes
- Tables
- Horizontal rules
- Images (via URL)

## Architecture

Single-file implementation following the project's architectural pattern:
- All HTML structure in the main document body
- All CSS in embedded `<style>` tag
- All JavaScript in embedded `<script>` tag
- External dependencies loaded from CDN
- No build process required

## Design System

### Layout
- **Header**: Dark background with gold accent border, large serif title
- **Controls Panel**: White card with grid layout for settings and action buttons
- **Workspace**: Two-column layout (editor | preview) on desktop, stacked on mobile
- **Panels**: White cards with dark headers and gold accent borders

### Typography Scale
- H1: 3rem (Cormorant Garamond) - Main title
- H2: 2rem - Section headings in preview
- H3: 1.5rem - Subsection headings
- Body: 1rem (Work Sans) - Base text
- Small: 0.875rem - Labels, footer

### Interactive Elements
- **Primary Button**: Burgundy background, white text - main action (Generate PDF)
- **Secondary Button**: White with dark border - alternative actions
- **Tertiary Button**: Cream background - less prominent actions
- Hover states with subtle transforms and shadow changes
- Focus states with gold border highlights

### Responsive Breakpoints
- Mobile: < 640px (single column, full-width buttons)
- Tablet: 640px - 1024px (single column workspace)
- Desktop: > 1024px (two-column workspace)

## Model Used

Created with **Claude Sonnet 4.5** (claude-sonnet-4-5-20250929)

## Known Limitations

1. **Image Handling**: Images must be accessible via URL; local file paths won't work in PDF export due to browser security restrictions
2. **Font Embedding**: PDF uses web-safe fonts for compatibility; Google Fonts may not embed perfectly in all PDF viewers
3. **Large Documents**: Very large documents (>50 pages) may take longer to generate or could cause performance issues
4. **Browser Dependency**: Requires modern browser with localStorage and JavaScript enabled
5. **No File Upload**: Currently accepts only pasted/typed content, not direct .md file upload
6. **Syntax Highlighting**: Code blocks have styling but not language-specific syntax highlighting in PDF

## Future Enhancements

Potential improvements for future versions:
- File upload support for .md files
- Dark mode toggle for the editor interface
- Export settings presets (save custom configurations)
- Syntax highlighting for code blocks using highlight.js or Prism
- Custom CSS injection for advanced PDF styling
- Page break controls for multi-page documents
- Table of contents auto-generation
- Word count and reading time statistics
- Export to other formats (HTML, DOCX)
- Collaborative features (share via URL)
- Template library for common document types

## Usage Tips

1. **Getting Started**: Click "Load Sample" to see example Markdown and explore features
2. **Auto-save**: Your content is automatically saved to localStorage as you type
3. **Filename**: Change the filename before generating PDF to organize your exports
4. **Page Size**: Choose A4 for international standard, Letter for US standard
5. **Orientation**: Use Landscape for wide tables or diagrams
6. **Preview First**: Always check the live preview before generating PDF to ensure formatting is correct

## Browser Compatibility

Tested and working in:
- Chrome/Edge (v90+)
- Firefox (v88+)
- Safari (v14+)

Requires:
- localStorage support
- ES6 JavaScript features
- CSS Grid and Flexbox
- Async/await support
