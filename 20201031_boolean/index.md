
class: center, middle






# Bool, rational number and complex number






### Julia Study Group






#### Yueh-Hua Tu






#### 2020.10.31


---






# Outline


  * Bool
  * Rational number
  * Complex number


---






# Bool


```julia
julia> true
true

julia> false
false
```


--


```julia
julia> Bool <: Integer
true
```


--


```julia
julia> sizeof(false)
1
```


> Currently, only sizes that are multiples of 8 bits are supported and you are likely to experience LLVM bugs with sizes other than those used above. Therefore, boolean values, although they really need just a single bit, cannot be declared to be any smaller than eight bits. [Ref](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)



--






### Try


  * `typemax(Bool)`
  * `typemin(Bool)`


---






# Logical operations


  * `~false`
  * `true & false`
  * `true | false`
  * `true ⊻ false`


--


  * `~Int8(127)`
  * `Int8(4) & Int8(127)`
  * `Int8(4) | Int8(127)`
  * `Int8(4) ⊻ Int8(127)`


--






### Bit shift


  * `Int8(127) >> 1`
  * `Int8(127) >>> 1`
  * `Int8(-128) >> 1`
  * `Int8(-128) >>> 1`
  * `Int8(127) << 1`


---






# Conversion of integer and bool


```julia
julia> Int64(false)
0
```


--


```julia
julia> Int64(true)
1
```


--


```julia
julia> Bool(1)
true
```


--


```julia
julia> Bool(0)
false
```


--




### Try


  * `Bool(2)`
  * `Bool(2.)`


---






# Literal zero and one


```julia
julia> zero(Float64)
0.0

julia> one(Float64)
1.0
```


--




### Try


  * `zero(1.)`
  * `one(32.0)`


---






# Rational number


```julia
julia> 1//3
1//3

julia> 3//9
1//3

julia> -3//9
-1//3

julia> 3//-9
-1//3
```


--


```julia
julia> r = 1//3
1//3

julia> numerator(r)
1

julia> denominator(r)
3
```


--


  * `1//3 == 3//9`
  * `2//4 + 1//6`
  * `7//9 * 11//14`


---






# Conversion of rational number and floating point


  * `float(3//4)`


--






### Denominator can be zero


```julia
julia> 5//0
1//0

julia> -2//0
-1//0
```


--






### Rational number and complex number


```julia
julia> 3//7 * (3 + 4im)
9//7 + 12//7*im

julia> 3//7 / (3 + 4im)
9//175 - 12//175*im
```


---






# Complex number


```julia
julia> typeof(3+4im)
Complex{Int64}

julia> typeof(3. + 4im)
Complex{Float64}
```


--


  * `z = 3+4im`
  * `(3+4im)*(1+2im)`
  * `(3+4im)+(1+2im)`
  * `(3+4im)^2`
  * `(3+4im)^2.5`


--


```julia
julia> real(z)
3

julia> imag(z)
4
```


--


```julia
julia> conj(z)
3 - 4im

julia> abs2(z)
25
```


---






# Polar coordiantes


```julia
julia> angle(3+4im)
0.9272952180016122

julia> abs(3+4im)
5.0
```


--


```julia
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```


--






### Composite of complex number and rational number


```julia
julia> z = 1 + 2//3im
1//1 - 2//3*im

julia> typeof(z)
Complex{Rational{Int64}}
```


---


class: middle






# Thank you for attention


--






### Read the code


  * [rational.jl](https://github.com/JuliaLang/julia/blob/master/base/rational.jl)
  * [complex.jl](https://github.com/JuliaLang/julia/blob/master/base/complex.jl)

