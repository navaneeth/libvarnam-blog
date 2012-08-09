---
layout: post
title: "Introducing varnam_train()"
date: 2012-08-09 16:33
comments: true
categories: [libvarnam, API, Varnam]
---
Today we introduced a new API to `libvarnam`.

```c
int
varnam_train(varnam *handle, const char *pattern, const char *word);
```

This function trains varnam to resolve `word` as a match when `pattern` is given. `libvarnam` has got a learning sub-system which is good at learning possible patterns from words. But sometimes, it won't get all the possibilities right. Consider the below case.

```bash
$ ./varnamc -s ml --learn ലണ്ടൻ
Learned ലണ്ടൻ
```

Now let us try to transliterate `london`.

```bash
$ ./varnamc -s ml -t london
Transliterating 'london'
ലൊന്ദൊൻ
```

This is happening because `london` won't read as ലണ്ടൻ phonetically. To correct this, you can train varnam like,

```bash
$ ./varnamc -s ml --train london=ലണ്ടൻ
Success. london will resolve to ലണ്ടൻ
$
$ ./varnamc -s ml -t london
Transliterating 'london'
  ലണ്ടൻ
  ലൊന്ദൊൻ
```
Even this will work.

```bash
$ ./varnamc -s ml -t londonil
Transliterating 'londonil'
  ലണ്ടനിൽ
  ലൊന്ദൊനിൽ
```

Have a great day!
