---
title: 'Creating a Model'
description: ""
---

## Splitting data into train and test sets

```yaml
type: NormalExercise
key: c909bf2ad1
lang: python
xp: 100
skills: 2
```

This is the assignment text. It should help provide students with the background information needed.
The instructions that follow should be in bullet point form with clear guidance for what is expected.

`@instructions`
- Instruction 1
- Instruction 2
- Instruction 3

`@hint`
- Here is the hint for this setup problem. 
- It should get students 50% of the way to the correct answer.
- So don't provide the answer, but don't just reiterate the instructions.
- Typically one hint per instruction is a sensible amount.

`@pre_exercise_code`
```{python}
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler

pima = spark.read.csv('pima-indians.csv', sep=';', header=True, inferSchema=True)

assembler = VectorAssembler(inputCols = ['temperature', 'vacuum', 'pressure', 'humidity'], outputCol = 'features')
pima = assembler.transform(pima).select(['features', 'power'])
```

`@sample_code`
```{python}
# Your
# sample
# code
# should
# be
# ideally
# 10 lines or less,
# with a max
# of 16 lines.
```

`@solution`
```{python}
# Answer goes here
# Make sure to match the comments with your sample code
# to help students see the differences from solution
# to given.
```

`@sct`
```{python}
# Update this to something more informative.
success_msg("Some praise! Then reinforce a learning objective from the exercise.")
```

---

## Insert exercise title here

```yaml
type: VideoExercise
key: 53f0bd0542
xp: 50
```

`@projector_key`
d12cf9b568130da37e9a5255e79049fc

---

## Insert exercise title here

```yaml
type: NormalExercise
key: 6cad38cf21
xp: 100
```

You'll be splitting the Height/Mass/Age data into training and testing sets.

`@instructions`
- Check that there are a reasonable number of records available for splitting.
- Split the data in a 70:30 ratio, setting the random seed to 17.
- Check the number of records in each of the resulting data sets.

`@hint`
- Use the method which counts the number of records in a DataFrame.
- The randomSplit() method accepts two arguments: the proportions for the split (as a list) and a random seed.
- Use the same method as before. Present the results as a tuple.

`@pre_exercise_code`
```{python}
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler

baseball = spark.read.csv('baseball-height-weight-age.csv', sep=';', header=True, inferSchema=True)

assembler = VectorAssembler(inputCols = ['height', 'age'], outputCol = 'features')
baseball = assembler.transform(baseball).select(['features', 'mass'])
```

`@sample_code`
```{python}
baseball.______()

train, test = power.______(______, ______)

(train.______(), test.______())
```

`@solution`
```{python}
baseball.count()

train, test = power.randomSplit([0.7, 0.3], seed=17)

(train.count(), test.count())
```

`@sct`
```{python}

```
