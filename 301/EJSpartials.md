### EJS Partials

- handy when reusing same HTML across multiple views (nav bar, header, footer → stuff that stays static)
- define reusable code in a file and include it wherever needed
- any JS or non-html syntax is surrounded by <% %> delimiters
- `<%- include( 'foldername/filename' ) %>`
    - partial file is relative to the template you use it in
- partials are native to EJS