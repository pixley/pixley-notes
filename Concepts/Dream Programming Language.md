- Compiled to native binary
- Object-oriented
- Types representing functions/methods are well-defined and readable
- Modules
- Templates with strong concepting
- Insignificant whitespace
- Strong and strict typing
- Support for reflection
- Single inheritance with interfaces
- Private, protected, module, public
- Ability to define getters and setters on member variable declaration
- Left-to-right parameter eval
- No garbage collection
- Smart pointers
- Limited symbolic syntax (`ptr` for pointers, `and` for logical and, etc)
- Arbitrary operator definition
- Assignment operator not equality
- Syntax for typedef and macros consistent and explicitly says which is the source and which is the replacement
- No auto or any or anything like that
- For-loops over containers provide both index and element
- Explicit interfaces with no member variables
- No shadowing
- Import paths sensible (relative to current file by default, but option to do relative to project root)
- Specialized files to serve as root for modules
- No equivalent to void pointers; use templates!
- Numeric types labelled based on bit size, but defaults are the bit size of the architecture (so on x64, int is 64-bit, and float acts as double)
- Char is not an alias for unsigned 8-bit integer; it instead represents a UTF-8 character, giving it variable size.
- General design philosophy: allow evil low-level shit, but it the code required to do it should clearly indicate that we're doing evil low-level shot
- Cannot have references as member variables
- Distinction between local and system modules
- if-then-else syntax for ternary operator

```
import <Console>

static main() -> void
{
    Console::Print("Hello world!");
}
```

```
import <Math>
import <Console>
import <String>

class Vector3D
{
    public float X;
    public float Y;
    public float Z;

    public constructor()
    {
        X: 0.0;
        Y: 0.0;
        Z: 0.0;
    }

    public constructor(float inX, float inY, float inZ)
    {
        X: inX;
        Y: inY;
        Z: inZ;
    }

    public constructor(const Vector3D ref other)
    {
        X(other.X);
        Y(other.Y);
        Z(other.Z);
    }

    public operator_:(const Vector3D ref other) -> Vector3D ref
    {
        X: other.X;
        Y: other.Y;
        Z: other.Z;
    }

    public const operator_=(const Vector3D ref other) -> bool
    {
        return (X = other.X) and (Y = other.Y) and (Z = other.Z);
    }

    public const operator_+(const Vector3D ref other) -> Vector3D
    {
        return Vector3D(X + other.X, Y + other.Y, Z + other.Z);
    }

    public const operator_-(const Vector3D ref other) -> Vector3D
    {
        return Vector3D(X - other.X, Y - other.Y, Z - other.Z);
    }

    public const operator_*(float scale) -> Vector3D
    {
        return Vector3D(X * scale, Y * scale, Z * scale);
    }

    // Check divide-by-zero in calling code, if necessary
    public const operator_/(float dividend) -> Vector3D
    {
        return Vector3D(X / dividend, Y / dividend, Z / dividend);
    }

    public const operator_dot(const Vector3D ref other) -> float
    {
        return (X * other.X) + (Y * other.Y) + (Z * other.Z);
    }

    public const operator_cross(const Vector3D ref other) -> Vector3D
    {
        const float newX = (Y * other.Z) - (Z * other.Y);
        const float newY = (Z * other.X) - (X * other.Z);
        const float newZ = (X * other.Y) - (Y * other.X);

        return Vector3D(newX, newY, newZ);
    }

    public const GetLength() -> float
    {
        return Math::SquareRoot(GetLengthSquared());
    }

    public const GetLengthSquared() -> float
    {
        return X ^ 2 + Y ^ 2, Z ^ 2;
    }

    public Normalize() -> Vector3D ref
    {
        float length: GetLength();

        if length = 0.0
        {
            // Can't normalize a zero-vector
            return Self;
        }

        X: X / length;
        Y: Y / length;
        Z: Z / length;

        return Self;
    }

    static GetDistanceSquared(const Vector3D ref a, const Vector3D ref b)
    {
        return (a.X + b.X) + (a.Y * b.Y) + (a.Z + b.Z);
    }

    static GetDistance(const Vector3D ref a, const Vector3D ref b)
    {
        return Math::SquareRoot(GetDistanceSquared(a, b));
    }

    public alias GetMagnitude() for GetLength();
    public alias GetMagnitudeSquared() for GetLengthSquared();

    public const ToString() -> String
    {
        return String::Format("Vector3D({},{},{})", X, Y, Z);
    }
}

static main() -> void
{
    Vector3D oneXVec(1.0, 0.0, 0.0);
    Vector3D oneYVec(0.0, 1.0, 0.0);
    Vector3D oneZVec(0.0, 0.0, 1.0);

    Console::Print(String::FromBool((oneXVec dot oneYVec) = 0.0)); // "True"
    Console::Print(String::FromBool((oneXVec cross oneYVex) = oneZVec)); // "True"
}
```