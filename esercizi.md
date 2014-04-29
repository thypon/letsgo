# Esercizi

---

    package main

    import (
	"fmt"
    )

    func Sqrt(x float64) float64 {
	z := float64(1)

	for i := 0; i < 10; i++ {
	    z = z - (z*z - x) / (2 * z)
	}
	
	return z
    }

    func main() {
	fmt.Println(Sqrt(2))
    }

---

    package main

    import "code.google.com/p/go-tour/pic"

    func Pic(dx, dy int) [][]uint8 {
	ar := make([][]uint8, dx)
	
	for i := 0; i < dx; i++ {
	    ar[i] = make([]uint8, dy)
	    
	    for j := 0; j < dy; j++ {
		ar[i][j] = uint8(i * j)
	    }
	}
	
	return ar
    }

---

    package main

    import "fmt"

    // fibonacci is a function that returns
    // a function that returns an int.
    func fibonacci() func() int {
	i := 1
	pre := 0
	return func() int {
	    i, pre = i + pre, i
	    return i
	}
    }

    func main() {
	f := fibonacci()
	for i := 0; i < 10; i++ {
	    fmt.Println(f())
	}
    }


    func main() {
	pic.Show(Pic)
    }

---

    package main

    import (
	"fmt"
	"math/cmplx"
    )

    func Cbrt(x complex128) complex128 {
	var z complex128 = 1
	    
	for i := 0; i < 10; i++ {
	    z = z - (cmplx.Pow(z, 3) - x) / (3 * cmplx.Pow(z, 2))
	}
	
	return z
    }

    func main() {
	fmt.Println(Cbrt(2))
    }
---

    package main

    import (
	"fmt"
    )

    type ErrNegativeSqrt float64

    func (e ErrNegativeSqrt) Error() string {
	return "Negative value"
    }


    func Sqrt(f float64) (float64, error) {
	if f < 0.0 {
	    return 0, ErrNegativeSqrt(f)
	}
	
	z := float64(1)

	for i := 0; i < 10; i++ {
	    z = z - (z*z - f) / (2 * z)
	}
	
	return z, nil
    }

    func main() {
	fmt.Println(Sqrt(2))
	fmt.Println(Sqrt(-2))
    }

---

    package main

    import (
	"net/http"
    )

    type String string

    type Struct struct {
	Greeting string
	Punct string
	Who string
    }

    func (s String) ServeHTTP(w ResponseWriter, r *Request) {
      // Write the response, based on the request
    }

    func (s *Struct) ServeHTTP(w ResponseWriter, r *Request) {
      // Write the response, based on the request  
    }

    func main() {
	// your http.Handle calls here
	http.Handle("/string", String("I'm a frayed knot."))
	http.Handle("/struct", &Struct{"Hello", ":", "Gophers!"})
	http.ListenAndServe("localhost:4000", nil)
    }

---

    package main

    import (
	"code.google.com/p/go-tour/pic"
	"image"
	"image/color"
    )

    type Image struct{
      c color.Model
      rec image.Rectangle
      rep [][]color.Color
    }

    func (img Image) ColorModel() color.Model {
      return img.c  
    }

    func (img Image) Bounds() image.Rectangle {
      return img.rec  
    }
    func (img Image) At(x, y int) color.Color {
      return img.rep[x][y]  
    }

    func generate(dx, dy int) Image {
	ar := make([][]color.Color, dx)
	
	for i := 0; i < dx; i++ {
	    ar[i] = make([]color.Color, dy)
	    
	    for j := 0; j < dy; j++ {
		ar[i][j] = color.Gray{uint8(i * j)}
	    }
	}
	
	img := Image{color.GrayModel, image.Rect(0,0,dx,dy), ar}
	
	return img
    }


    func main() {
	pic.ShowImage(generate(100, 100))
    }

---

(Equivalent binary trees)[https://stackoverflow.com/questions/12224042/go-tour-exercise-equivalent-binary-trees]
