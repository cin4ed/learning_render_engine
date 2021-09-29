# Vectors
A vector is a quantity that has a magnitude and a direction. Examples of this
are:
- Displacement
- Velocity
- Acceleration
- Force

Vectors are graphically represented by a pointed line segment with the length of
the line denoting the magnitude of the vector and the pointing arrow showing the
direction of the vector.

Two vectors are said to be equal if they both have the same magnitude and
direction even if they are in different locations.

## Vector operations
Just like scalar information, vectors can also be added, substracted and
multiplied with each other.

Suppose you have two vectors:

```
- A = (a.x, a.y, a.z)
- B = (b.x, b.y, b.z)
```

### Adding
When adding the vectors, we add the components individually to give a new
vector:

```
C = A + B

C = ((a.x + b.x), (a.y + b.y), (a.z + b.z))
```

Vectors are also commutative, meaning A + B will give the same result as B + A.

### Subtraction

In subtraction we subtract the individual components of the vectors to give a new vector:

```
C = A - B
C = ((a.x - b.x), (a.y - b.y), (a.z - b.z))
```

If vectors A and B are equal, the result will be a zero vector with all three components being zero.

### Multiplication

We can multiply a scalar with a vector. The result is again a vector with each component of the vector mutiplied by the scalar.

For example, if A is multiplied by a single value S we will have teh following result:

```
C = S * A
C = S * (a.x, a.y, a.z)
C = (S * a.x, S * a.y, S * a.z)
```

## Vector magnitude

The magnitude of a vector is equal to the length of the vector itself.  But how do we calculate it?

The magnitude is given by the Pythagorean theorem, which specifies that in a right triangle, the square of lenght of a diagonal is equal to the sum ot the squares of the adjacent sides. So when we look at the right triangle as follows:

```
C^2 = X^2 + Y^2
```

This can be extended to three dimensions with:

```
C^2 = X^2 + Y^2 + Z^2
```

The magnitude is always greater than or equal to zero.

## Vector magnitude

In some cases, we don't care about the magnitude of the vector, we just want to know the direction of it. To find this out, we want the length (magnitude) of the vector in the X, Y and Z direction to be equal to 1. Such vectors are called unit vectors or normalized vectors.

In unit vectors, the X, Y and Z components of the vector are divided by the magnitude to create a vector of unit length. 

```
A.unit = ((A.x / A.m), (A.y / A.m), (A.z / A.m))
```

When a vector is converted into a unit vector, it is said to be normalized. Meaning the value is always between `0.0` and `1.0`. The original value has been rescaled to be in this range.

## Dot product

A dot product is a type of vector multiplication in which the resultant vector is a **scalar**. It is also referred to as a scalar product for the same reason. Scalar product of two vectors is the sum of the products of the corresponding components.

```
A ⋅ B = A.x * B.x + A.y * B.y + A.z * B.z
```

The dot product of two vectors is also equal to the cosine of the angle between the vectors multiplied by the mmagnitudes of both vectors.

```
A ⋅ B = A.m * B.m * cos(θ)
```

θ is always between 0 and π. By putting an equation of 1 and 2 together, we can figure out the angle between 2 vectors:

```
A.m * B.m * cos(θ) = A.x * B.x + A.y * B.y + A.z * B.z
cos(θ) = (A.x * B.x + A.y * B.y + A.z * B.z) / (A.m * B.m)
```

Consequently:

```
θ = cos - 1((A.x * B.x + A.y * B.y + A.z * B.z) / (A.m * B.m))
```

## Cross Product

Cross product is the other vector multiplication form is which the resultant product of the multiplication is another **vector**. Taking the cross product between A and B vectors will result in a third vector that it is perpendicular to both vectors.

```
C = A * B = ((A.y * B.z - A.z * B.y), (A.z * b.x - A.x * B.z), (A.x * B.y - A.y * B.x))
```

