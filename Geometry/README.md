## 1. Find rectangles parallel with x and y

a. find p1 and p2, then p3 = (p1[x], p2[y]), p4 = (p2[x], p1[y])  
b. preprocess all vertical lines (y1, y2) and stores them into a hashTable, whose key is x, two same vertical lines with different x can form a rectangle, and value is list of vertical lines, then scan x from left to right, also use another hash table to store last x for each vertical line.

939 - https://leetcode.com/problems/minimum-area-rectangle/

## 2. Find rectangles can rotate

a. find p1 and p2, then use Pythagorean theorem to find p3, a^2 + b^2 = c^2, then use x1 + x3 = x2 + x4, y1 + y3 = y2 + y4 to find p4  
b. find center point and length of each diagonal line, find all combinations of two points, and calculate center point and length, use both as the key and store them into a hashTable, then loop though all the keys if there is more than two element in the value, then loop through all the values

963 - https://leetcode.com/problems/minimum-area-rectangle-ii/

## 3. Calculate angle between two points

```python

angle = math.atan2(p2[1]-p1[1], p2[0]-p1[0]) * (180 / math.pi)

if angle < 0:
  angle += 360

```
after rotating 360 degree, rotate 360 again to handle the range [315 - 45]  
1610 - https://leetcode.com/problems/maximum-number-of-visible-points/

## 4. when checking the points angle, don't forget to handle the point at the same location separately by creating a "same" variable because those points will always be on the same line of be seen 

## 5. how to get convex hell? need to find most clockwise point. How? check cross product of two vectors is greater than 0 or not

587 - https://leetcode.com/problems/erect-the-fence/
