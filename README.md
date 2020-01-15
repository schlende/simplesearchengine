# Walt's amazing simple search engine

Let's make a search engine!

A search engine sorts stuff so that I don't have to. BOOM! I always wanted to build one of em, and the day has finally come. My simple search engine helps me find stuff similar to other stuff that's on my desk.

## Methodology

1. Get stuff (on my desk)
2. Mesaure stuff (no ruler... erm... who needs one! I'll just guestimate with my HAND!! 🖐💪💪💪🚀🚀)
3. Do math (cosine similarity).
4. Display sorted list.


```python
import math

items = {
    'phone': [1, 1/2, 1/12],
    'mouse': [3/4, 1/3, 1/4],
    'kindle': [13/12, 10/12, 1/12],
    'water': [1/2, 1/2, 7/4],
    'pen': [1, 1/20, 1/20]
}

def similarities(item):
    results = []
    for theitem in items:
        a = items[item]
        b = items[theitem]
        
        simscore = cosinesim(a, b)
        results.append((theitem, simscore))
    
    results.sort(key=lambda tup: tup[1], reverse = True)
    for result in results:
        print(result)
    
    
def cosinesim(vec1, vec2):
    vec1mag = magnitude(vec1)
    vec2mag = magnitude(vec2)
    dotprod = 0
    
    for i in range(len(vec1)):
        dotprod = dotprod + vec1[i] * vec2[i]
        
    return dotprod / (vec1mag * vec2mag)


def magnitude(vec):
    mag = 0
    for i in range(len(vec)):
        mag = mag + vec[i] * vec[i]
    mag = math.sqrt(mag)
    return mag

similarities('phone')
```

    ('phone', 1.0)
    ('kindle', 0.9816090739462485)
    ('mouse', 0.9746339793607601)
    ('pen', 0.9156819201892902)
    ('water', 0.42334237343420567)



```python
similarities('pen')
```

    ('pen', 1.0)
    ('phone', 0.9156819201892902)
    ('mouse', 0.9058903792082271)
    ('kindle', 0.8225728713106082)
    ('water', 0.3237021810765124)



```python
similarities('water')
```

    ('water', 1.0)
    ('mouse', 0.6046547897464497)
    ('kindle', 0.42722490284256237)
    ('phone', 0.42334237343420567)
    ('pen', 0.3237021810765124)



```python
similarities('kindle')
```

    ('kindle', 0.9999999999999999)
    ('phone', 0.9816090739462485)
    ('mouse', 0.9457692028425447)
    ('pen', 0.8225728713106082)
    ('water', 0.42722490284256237)


## Results

Numbers make sense! 

My kindle and phone are sorta similarish... who knew???

My pen is definitely not like my water bottle. ✅

### Useful? I think so!!! 💪💪💪🚀🚀


```python

```
