
# Point Addition on a Curve


```python
# Example where x1 != x2

from ecc import FieldElement, Point

prime = 137
a = FieldElement(0, prime)
b = FieldElement(7, prime)
p1 = Point(FieldElement(73, prime), FieldElement(128, prime), a, b)
p2 = Point(FieldElement(46, prime), FieldElement(22, prime), a, b)

print(p1+p2)
```

### Try it

#### Find the following point additions on the curve  \\( y^2 = x^3 + 7: F_{223} \\)
```
(192,105) + (17,56), (47,71) + (117,141), (143,98) + (76,66)
```


```python
from ecc import FieldElement, Point

prime = 223
a = FieldElement(0, prime)
b = FieldElement(7, prime)

additions = ((192, 105, 17, 56), (47, 71, 117, 141), (143, 98, 76, 66))

# iterate over the additions to be done
for x1_raw, y1_raw, x2_raw, y2_raw in additions:
    # Initialize points this way:
    # x1 = FieldElement(x1_raw, prime)
    # y1 = FieldElement(y1_raw, prime)
    # p1 = Point(x1, y1, a, b)
    # x2 = FieldElement(x2_raw, prime)
    # y2 = FieldElement(y2_raw, prime)
    # p2 = Point(x2, y2, a, b)
    x1 = FieldElement(x1_raw, prime)
    y1 = FieldElement(y1_raw, prime)
    p1 = Point(x1, y1, a, b)
    x2 = FieldElement(x2_raw, prime)
    y2 = FieldElement(y2_raw, prime)
    p2 = Point(x2, y2, a, b)
    print('{} + {} = {}'.format(p1, p2, p1+p2))
```

### Test Driven Exercise

It's your turn to write some tests now. Write a test below using the comments as a guide.


```python
from helper import run_test
from unittest import TestCase
from ecc import FieldElement, Point

class ECCTest(TestCase):

    def test_add1(self):
        # tests the following additions on curve y^2=x^3-7 over F_223:
        # (192,105) + (17,56)
        # (47,71) + (117,141)
        # (143,98) + (76,66)
        prime = 223
        a = FieldElement(0, prime)
        b = FieldElement(7, prime)

        additions = (
            # (x1, y1, x2, y2, x3, y3)         
            (192, 105, 17, 56, 170, 142),
            (47, 71, 117, 141, 60, 139),
            (143, 98, 76, 66, 47, 71),
        )
        # iterate over the additions
        for x1_raw, y1_raw, x2_raw, y2_raw, x3_raw, y3_raw in additions:
            # Initialize points this way:
            # x1 = FieldElement(x1_raw, prime)
            # y1 = FieldElement(y1_raw, prime)
            # p1 = Point(x1, y1, a, b)
            # x2 = FieldElement(x2_raw, prime)
            # y2 = FieldElement(y2_raw, prime)
            # p2 = Point(x2, y2, a, b)
            # x3 = FieldElement(x3_raw, prime)
            # y3 = FieldElement(y3_raw, prime)
            # p3 = Point(x3, y3, a, b)
            x1 = FieldElement(x1_raw, prime)
            y1 = FieldElement(y1_raw, prime)
            p1 = Point(x1, y1, a, b)
            x2 = FieldElement(x2_raw, prime)
            y2 = FieldElement(y2_raw, prime)
            p2 = Point(x2, y2, a, b)
            x3 = FieldElement(x3_raw, prime)
            y3 = FieldElement(y3_raw, prime)
            p3 = Point(x3, y3, a, b)
            # check that p1 + p2 == p3
            self.assertEqual(p1+p2, p3)
```

### Run your tests!

Be sure to run the above cell and now see whether your test works by running the cell below.


```python
run_test(ECCTest('test_add1'))
```
