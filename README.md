## Vec3

A single-file Rust library for f32 based 3D vectors. I built this while getting started with Rust as a way to learn. It's really small and has no dependencies. It's built for you to be able to read it in entirety, copy paste it into your own project, and pretty quickly and feel like it is your own as opposed to building your own vector class from scratch.

That said, there are significantly fuller-featured Rust vector math libraries out there if you need more than just simple 3D Vectors...

 - [vecmath](https://github.com/PistonDevelopers/vecmath)
 - [cgmath](https://github.com/rustgd/cgmath)

## Example use

The API purposefully works with both values and borrowed references. My goal was to make working with vectors feel as much as possible like working with native Rust numbers.

```
let x = Vec3::new(0.0, 1.0, 2.0);
let y = Vec3::new(0.1, 2.3, 3.4);
let mut z = Vec3::ZERO;

x + y;
x + &y;
&x + y;
&x + &y;
z += x;
z += &x;

x - y;
x - &y;
&x - y;
&x - &y;
z -= x;
z -= &x;
- x;
- &x;

x * y;
x * &y;
&x * y;
&x * &y;
z *= x;
z *= &x;

x / y;
x / &y;
&x / y;
&x / &y;
z /= x;
z /= &x;
```

Other conveniences that you might care about...

```
// To create (1.0, 1.0, 1.0)
let ones = Vec3::ONE;

// To create (0.0, 0.0, 0.0)
let zeros = Vec3::ZERO;

// To create (0.1, 0.1, 0.1)
let value = Vec3::from_float(0.1);

// You can override a component of a vector like so...
let value = Vec3::ZERO.with_z(1.0);

// Returns the cartesian length of the vector `value`
value.length();

// Returns a new normalized vector
let normalized = value.normalize();

// To dot two vectors
let a = Vec3::dot(&ones, &zeros);

// To cross two vectors
let a = Vec3::cross(&ones, &zeros);

// To access the component of a vector dynamically
let a = some_vector.component(Axis::X);

// To set the component of a vector dynamically
some_vector.set_component(Axis::X, 3.0);
```

Note that Eq is not defined on Vec3 because co-ordinates are stored
as f32 which does not implement Eq. This is... annoying but is
consistent with Rust's design goal of safety since NaNs interact
weirdly with equality.

## Licence

MIT