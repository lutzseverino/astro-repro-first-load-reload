# Astro 7.4.4: first page after a fresh `astro dev` start reloads once

Minimal reproduction: one content collection (glob loader, one Markdown entry)
and one page that reads it. No integrations, default config.

## Steps

1. `npm install`
2. Make sure `.astro/` does not exist (it does not in a fresh clone).
3. `npx astro dev`
4. With no other tab connected to the dev server, open http://localhost:4321/

## Result

The page counts its own loads in `sessionStorage` and prints them to the
console and to the page. After a fresh start it shows `page load #2`: the
first load is followed immediately by a Vite `full-reload`.

Stop the server and start it again with `.astro/` left in place: the first
page now shows `page load #1`. Delete `.astro/` and it reloads again.
