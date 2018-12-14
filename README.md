Here is the multivariate polynomial parser developed as part of [CGAL](https://www.cgal.org/ "The Computational Geometry Algorithms Library")
library (namely its [Polynomial](https://doc.cgal.org/latest/Polynomial/index.html "CGAL's Polynomial package") package).
Note that, despite its well-thought generic and flexible design, Polynomial's package integrated parser (aka. input operator >>)
is quite rudimental and supports only polynomials given in ASCII machine-readable format, e.g.:

`P[8(0,P[8(0,P[8(0,2)(2,-16)(4,80)(6,-128)(8,64)])(2,P[0(0,-16)])(4,P[0(0,80)])(6,P[0(0,-128)])(8,P[0(0,64)])])(2,P[0(0,P[0(0,-16)])])(4,P[0(0,P[0(0,80)])])(6,P[0(0,P[0(0,-128)])])(8,P[0(0,P[0(0,64)])])]`

Our parser, in contrast, can parse arbitrary polynomial expressions in any number of variables with arbitrary coefficient types, e.g., trivariate polynomial expression
with large rational coefficients:
$$((723647287346823/817239817928378127381273y-1)^4 - x*y^3)^5 + (x + z)^2 - (2123234523*x^2 - 2*y*y*x + 3^{100}*x*132123)^{13}$$

This parser has been widely adopted internally by several CGAL projects but has never been properly integrated into CGAL
despite a number of attempts. The reason for this is because CGAL's editors and the author of this code went through countless
discussions concerning the code structure, clarity, documentation (and what else CGAL is known for) which never came to a fruitful end..
On this sad note, I took the liberty of publishing the code "as is" leaving it to the judgement of the reader:
[Polynomial parser on GitHub](https://github.com/workasm/CGAL_Polynomial_parser "CGAL::Polynomial_parser_d on GitHub").

Here is also short inroduction to the parser: {{% staticref "https://workasm.github.io/pdf/poly_parser_2012.pdf" "newtab" %}}Parser Manual{{% /staticref %}}.
