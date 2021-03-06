# Profile Flame

A javascript lib renders profile flame graph based on d3.js.

Find more details about flame in brendangregg's [FlameGraph](https://github.com/brendangregg/FlameGraph).

[![npm version](https://badge.fury.io/js/profile_flame.svg)](https://badge.fury.io/js/profile_flame)

## A Quick View

![profileFlameExample](profileFlameExample.gif)

## How To Use

A general flame:

```
var profileFlame = d3.profileFlame();

d3.select(container)
    .datum(exampleData1)
    .call(profileFlame);
```

Or a compare flame:

```
var profileFlame = d3.profileFlame()
    .compare(true);

d3.select(container)
    .datum([exampleData1, exampleData2])
    .call(profileFlame);
```

provide data like this:

```
var exampleData1 = {
    flame: {
      "height": 2, // total height of stacks
      "tree": {
        "oneEntry": [ // [subTree, samples of this entry]
          {
            "oneSubEntry": [
              {},
              36
            ]
          },
          37
        ],
        "anotherEntry": [
          {},
          22
        ],
      }
    }
}
```

## API Refs

**compare(compareBool)**

compare switcher, when in compare mode, data passed by d3 must be an array with two items;


**width([width])**


**height([height])**


**cutoff([cutoff])**

set/get cutoff threshold, entry with lower percent will be ignored. useful for those huge profiles.


**maxDepth([maxDepth])**

set/get max depth of stacks


**specifiedEntries(entriesArray)**

set/get array of specified entries, will only render stacks with these entries.


**search(kw)**

set search keyword, those entries matched will be render in purple.


**reset()**

reset flame to origin state


**reverseCompare()**

reverse the two data items comparing


**compareMethod([method])**

set/get compare method, allowed mode:

* cumulative
* internal


**backward()**

go backward on focus histories


**forward()**

go forward on focus histories


