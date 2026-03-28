## Neuromorphic Pattern Engine — Multi-Stream Sequence Prediction

Backdrop is at the front, runnable and sources are at the back.

Transformers trained on                      : `{t1, t2, ..., tn, *}` patterns to predict "next token".  
Some trained to predict "first" or "both"    : `{* , t2, ..., tn, *}`.  
Training on multiple "next tokens"           : `{t1, t2, ..., tn, *, *, ..., *}` - enables prediction in multiple time frames (trading stocks f.e.)  
Training on multiple "next tokens" with "skips" : `{t1, *, t2, *,..., tn, *, *, ..., *}` - enables prediction by subsequences (as opposed to substrings), which filters out a lot of noise, though computationally expensive.

Training on multiple "next tokens" and multiple input patterns:

```
{t1, *, t2, *,..., tn} \
{k1, *, k2, *,..., kn}  => {*, *, ..., *}
{p1, *, p2, *,..., pn} /
```

is ultimately best and ultimately expensive because of combinatorial explosion of input, output and combination patterns.

---

## Biological Neural Networks

Biological neural networks start solving intractability by employing huge fan-in dynamic synaptic fields.  
Huge means there are ~10K inputs - dendritic synapses waiting for the signal. Dynamic means a neuron fires with only a 10-300 synapses registering inputs.  
Then "tired" synapses get into short R&R cycle while remaining ones are ready to listen for new messages. Fields are switching ~50 times a second.  
Here is a demo clip of a "twinkling fields": https://youtu.be/T34rkIb7gEg

**Additionally** neurons operate redundant overlapping sensory fields - which adds to complexity of neural messaging.  
Some scientists find solace in looking at "spiking" protocols, but a simple experiment shows that the form of a signal is not important, the surface under the signal curve and timing are important to "leak, integrate and fire". Claude calls spikes "metabolic byproduct" I call them "contact chatter".  
Demo clip: https://youtu.be/3C40s4t4Biw

There are fast and slow, excitatory and inhibitory synapses (think hierarchical inference and feedback overexcitation [runaway] governing) - but we do not want to digress. There is a demo on fast and slow synapses though: https://youtu.be/3otQ2szNmXs

---

## Generation vs. Comparison

Containers like `{t1, ..., tn, *}` enable generation. Containers like `{t1, *,..., * tn}` enable comparison.  
I've got a comparison demo, of course: https://youtu.be/GQB2Q14yqzY

Comparison is founded on stochastic sampling (think dynamic sensory fields) and memorizing patterns combinations in hierarchical dictionaries (think layers of neurons) to reuse simple patterns. Such architecture effectively decomposes [very] complex patterns into sets of simpler ones.  
While comparison of long 10+K components binary vectors (HDC) deemed impossible, comparison of multiple decomposed discrete (text/numeric) sequences with millions of components (demo above) is very much computable. Decomposition is a good tool to search for MLCS also.

---

## Hierarchies

Building a single layer hierarchies is **very** simple: https://masteralgo.github.io/picoGPT/index.html (first/next token, static model) or just simple:  
https://youtu.be/soWw5_hYVDc (first/next/middle token, dynamic model: [up] training, explicit forgetting, generation(s) are simultaneous).

Building a multilayer hierarchies aka associative memory is conceptually simple but implementationally is a nightmare: irrelevant nodes got to gracefully locally decay/expire which affects both up- and downstream neighbours, independently decaying at the same time.

---

## The Trading Demo

Lot of ground to cover, but "talk is cheap, show me the code" (c) [now].

Anyways, just wanted to suggest my implementation of a single layer model, with multiple input streams, predicting a sequence of tokens. Training and trading[inferring] on minute candle OHLCV bars of 20+ years (get your own data... psst: https://www.kibot.com/free_historical_data.aspx).

How it works - 2.5 minutes clip of "trading then training" over a few millions datapoints: https://youtu.be/iEoLRHOzIHE

Would not make you rich... till you optimize... optimization space is huge, I gave up. My curiosity is fed, and greed is not a strong motivation. Medical applications would be interesting though.

Included with jar-zip the "profitable parameters manifold" is pretty narrow - make a step right or left - get yourself a loser. Stocks are just convenient stream of "ground truth".  
Implement your own "channels", include weather, news, indicators,... - Claude is there to help. Find new candles' patterns. Remember - behind every stock is a specific traders crowd - thus models must be stock specific.

### Downloads

- Runnable jar with properties: https://github.com/MasterAlgo/Demos/raw/main/Stocks_02_jar.zip  
- Sources to play with (Java): https://github.com/MasterAlgo/Demos/raw/main/Stocks_02_Sources.zip

I ran the app on a miniPC, allocated 30GB RAM to Java to accommodate 180 mils of "patterns". You can go higher or lower.

---

## Takeout

Implementation of biological machinery in silicon is intractable, implementation of bio-machinery purpose - collection and manipulation of symbolic patterns - is very much doable. And inter-communication of complex symbolic patterns defines our conversation here :-)
Important: in patterns' collections (trees, arrays, hashmaps) the *patterns* are keys with *values* are any association with classes, frequences, birth time, leak rate, rewards, etc. The key(pattern image) makes collections **symbolic** and inference **explainable**, because "names/images" and properties of voting constituents are always known.

Same "neuromorphic" engine powers online learning, classification, clusterization, prediction, generation apps.
