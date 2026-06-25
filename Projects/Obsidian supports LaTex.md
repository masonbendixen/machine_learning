---
fileClass: Project
Category: Planning
Status: Active
Course:
Author: Mason Bendixen
Last Updated: 6/25/2026
Version: 0.1
tags:
---
# Overview
- This is a cheat sheet for LaTex support in Obsidian for machine learning purposes.

# Inline LaTex
- You just put \${LaTex expression}\$

# LaTex on it's own line(s)
```
$$  
f_{w,b}(x) = wx + b  
$$
```

# Simple constructs
- Variables
	- \$a\$ produces $a$
- Bold vectors
	- \$\mathbf{x}\$ produces $\mathbf{x}$
	- \$\mathbf{w}\$ produces $\mathbf{w}$
	- \$\mathbf{X}\$ produces $\mathbf{X}$
- Subscripts
	- \$x_1\$ produces $x_1$
	- \$f_{w,b}\$ produces $f_{w,b}$
- Superscripts
	- \$x^2\$ produces $x^2$
	- \$x^{i+2}\$ produces $x^{i+2}$
	- \$x^{(i)}\$ produces $x^{(i)}$
- Function notation
	- \$f_{w,b}(x^{(i)}))\$ produces $f_{w,b}(x^{(i)}))$
- Greek letters
	- \\alpha is $\alpha$
	- \\beta is $\beta$
	- \\gamma is $\gamma$
	- \\delta is $\delta$
	- \\epsilon is $\epsilon$
	- \\theta is $\theta$
	- \\lambda is $\lambda$
	- \\mu is $\mu$
	- \\sigma is $\sigma$
	- \\phi is $\phi$
	- \\pi is $\pi$
	- \\omega is $\omega$
- You can capitalize greek letters by capitalizing the first English letter description
	- \\Pi is $\Pi$
	- \\Lambda is $\Lambda$
- Fractions
	- \$\frac{1}{2}\$ produces $\frac{1}{2}$
- Square root
	- \$\sqrt{x}\$ produces $\sqrt{x}$
- Summation
	- \$\sum_{i=1}^{m}x^{(i)}\$ produces $\sum_{i=1}^{m}x^{(i)}$
	- $\sum_{i=1}^{m} x^{(i)}$
	- 