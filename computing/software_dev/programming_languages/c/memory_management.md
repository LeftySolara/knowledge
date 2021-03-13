# Memory Management Tips

These are random tips about memory management that I've come across over time.

## Allocate Memory for a Struct
```
struct mystruct *st = malloc(sizeof(*st));
```