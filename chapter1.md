---
title: 'Train/Test Split'
description: ""
---

## Splitting Data

```yaml
type: VideoExercise
key: 53f0bd0542
xp: 50
```

`@projector_key`
d12cf9b568130da37e9a5255e79049fc

---

## Splitting Data (exercise)

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
success_msg("Excellent! You are now a master of the Train/Test Split.")
```
