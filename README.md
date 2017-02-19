# SimplePCHIP

| **Build Status**                                              |
|:-------------------------------------------------------------:|
| [![][travis-img]][travis-url] [![][codecov-img]][codecov-url] |


[travis-img]: https://travis-ci.org/slabanja/SimplePCHIP.svg?branch=master
[travis-url]: https://travis-ci.org/slabanja/SimplePCHIP

[codecov-img]: https://codecov.io/gh/slabanja/SimplePCHIP/branch/master/graph/badge.svg
[codecov-url]: https://codecov.io/gh/slabanja/SimplePCHIP/

This package provide functionality to perform piecewise cubic hermite interpolating polynomial (PCHIP)
interpolation of arbitrarily spaced 1-dimensional data.


## Summary
The basic use of SimplePCHIP can be illustrated with the following snippet
```jl
using SimplePCHIP
using Gadfly

xs = [0.0  1.2  2.0  5.0 10.0 11.0]
ys = [2.0  2.1  1.0  0.0  0.0  3.0]
itp = interpolate(xs, ys)

xrange = linspace(xs[1], xs[end], 100)
yinterpolated = [itp(x) for x ∈ xrange]

plot(layer(x=xrange, y=yinterpolated, Geom.line), 
     layer(x=xs, y=ys, Geom.point))
```


## Why PCHIP?
PCHIP interpolation preserves monotonicity.
E.g., if input data point are monotonically increasing, so will the interpolated points.
Also, the interpolated points will not overshoot


## See also

SimplePCHIP was created to provide interpolation similar to SciPy's 
[PchipInterpolation](http://scipy.github.io/devdocs/generated/scipy.interpolate.PchipInterpolator.html).

For further details on PCHIP interpolation, there is of course a wikipedia article about [Monotone cubic interpolation](https://en.wikipedia.org/wiki/Monotone_cubic_interpolation), also [this pdf about interpolation](https://www.mathworks.com/content/dam/mathworks/mathworks-dot-com/moler/interp.pdf) (with a focus on Matlab) provides details on PCHIP interpolation.
