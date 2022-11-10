# tailwind-watch-issue
- Issue: https://github.com/tailwindlabs/tailwindcss/issues/7759#issuecomment-1310158881
- Fixed by: https://github.com/tailwindlabs/tailwindcss/pull/9796
- Works with `tailwind@insiders` as of 2022-11-11

## Environment
```
OS: Ubuntu 22.04
Node: v16.18.1
npm: 8.19.2
```

## Reproduce
```bash
git clone https://github.com/carderne/tailwind-watch-issue.git
cd tailwind-watch-issue
echo 'text-red-700' > index.html
npx tailwindcss@3.2.3 -i input.css -o output.css --watch
```

In a separate terminal:
```bash
grep 'red-' output.css
# prints '.text-red-700 {'

sed -i 's/red/blue/g' index.html
grep 'blue-' output.css
# prints nothing
```
