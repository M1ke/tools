# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a suite of client-side browser-based developer tools, hosted on GitHub Pages. All tools are self-contained single HTML files with embedded CSS and JavaScript - no build process, no dependencies, no backend servers. All processing happens entirely in the user's browser.

## Architecture

**Single-File Design Pattern**: Each tool is a standalone HTML file containing:
- Inline CSS in `<style>` tags for styling
- Vanilla JavaScript in `<script>` tags for functionality
- No external dependencies or frameworks

**Data Privacy**: A core principle is that no data leaves the user's browser. Each tool includes a notice stating "All processing for this is done in your browser; no data is sent to any remote server."

## Current Tools

### jwt.html - JWT Parser and Editor
Decodes JWT tokens into header/payload/signature components, allows editing, and reconstructs tokens.
- Uses base64url encoding/decoding functions
- Real-time validation with error messages
- Does NOT sign tokens (user must provide signatures)

### sql-csv.html - SQL CLI to CSV Converter
Converts SQL CLI table output (the ASCII art format with `+--+` borders) into CSV format.
- Extracts specific columns by name
- Wrap feature: replaces `%%` placeholders with column values
- Example input format:
  ```
  +---------+--------------+
  | user_id | name         |
  +---------+--------------+
  |       1 | Tim Fish     |
  ```

### sql-insert.html - SQL Insert Generator
Converts SQL `SELECT ... \G` output (vertical format) into INSERT statements.
- Requires table name input
- Optional "skip empty" checkbox to exclude null/zero/empty date values
- Handles field escaping and type detection (numeric vs string)

## Development Guidelines

### Adding New Tools
1. Create a new `.html` file in the root directory
2. Follow the single-file pattern: inline all CSS and JavaScript
3. Include the privacy notice about client-side processing
4. Add an example section to help users understand the expected input
5. Update README.md with a link to the new tool

### Modifying Existing Tools
- Preserve the self-contained nature - no external dependencies
- Maintain the privacy principle - all processing must remain client-side
- Keep the UI simple and functional
- Test thoroughly since there's no build/test pipeline

## Deployment

The repository is deployed to GitHub Pages at `https://m1ke.github.io/tools/`

No build, compilation, or deployment process is needed - HTML files are served directly. To publish changes, simply commit to the repository.
