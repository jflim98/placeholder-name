---
config:
  chapter: SOURCE_4
  variant: default
env:
  testEnv:
    chapter: SOURCE_4
    variant: default
---

# SOURCE BLOCK TEST DEMO
this is some stuff

## this is a header 2

```
this is a normal code block
multiline test
multiline test
```

```source-autorun-hidden
// this is a autorun and hidden source code block
const incr_three = (x) => x + 3;
```

```source
// this is a source code block
const incr_one = (x) => x + 1;
const incr_two = (x) => x + 2;
```

```source
// this is another source code block
incr_one(7);
```

i can add things

```
this is another normal code block
multiline test
```

```source
1+1;
```

```source
// this is the third source code bock
incr_two(7);
```
eeeee
