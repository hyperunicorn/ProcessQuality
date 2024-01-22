# ProcessQuality
My solution to a recent kaggle problem found here: https://www.kaggle.com/competitions/linking-writing-processes-to-writing-quality
Forked from https://www.kaggle.com/code/snnclsr/581-3-models-optimized-weights-165-features
Approximate testing score lies between 0.49 and 0.53 (depending on the seed used) compared to a top leaderboard score of 0.55.

The main innovations I introduced here were as follows:

- The use of a technique I call functional entropy. This technique takes a time series, say the sequence of pause lengths over the course of an essay, takes the fast fourier transform of this time series, takes the power of this transform, normalises it  and then takes the classical shannon entropy of the resulting series. The basic idea is to provide a generalised measure of the disorder of a time series.

- Engineering a feature which looks at the (normalised) mean of each column and then calculates the euclidean distance of each row in the dataframe from the mean vector of that dataframe.

- An intermediate prediction step where an array of standard predictors estimates whether a given essay will have a score within aproximately one standard deviation of the mean score which is then aggregated into a probabilistic estimate
- A technique which I call jittering. Jittering simply involves adding a column of random ones and zeroes to the dataframe. This was initially an accident but it actually seemed to reduce overfitting quite substantially for ensemble algorithms like LightGBM and such.

Unfortunately, I missed the (deceptive deadline) for this competition due to work commitments but I believe that passed on the demonstrated performance on the publically available dataset, that this notebook would have been a strong contender for first place.

