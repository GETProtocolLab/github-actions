# Desription
Repository of guts actions and helpers. 

guts-cd are the actions that combines the individual steps but they can also be used indepently.

## How to use
### guts-cd
We will create 2 action files (one for pr and one for push).
for the PR one use:
```yaml
example
```
for the push one use:
```yaml
example
```

## Lint
```bash
docker run --rm -v $(pwd):/work tmknom/prettier --write .
```