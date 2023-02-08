Task 1

Frontend:

import React, { useState } from "react";
import { useDispatch } from "react-redux";
import { navigateInsect } from "./actions";

const NavigateForm = () => {
  const [x, setX] = useState(0);
  const [y, setY] = useState(0);
  const [heading, setHeading] = useState("N");
  const [commands, setCommands] = useState("");
  const dispatch = useDispatch();

  const handleSubmit = (e) => {
    e.preventDefault();
    dispatch(navigateInsect(x, y, heading, commands.split("")));
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        X:
        <input type="number" value={x} onChange={(e) => setX(e.target.value)} />
      </label>
      <label>
        Y:
        <input type="number" value={y} onChange={(e) => setY(e.target.value)} />
Backend:

class Insect {
  constructor(x, y, heading) {
    this.x = x;
    this.y = y;
    this.heading = heading;
  }

  turnLeft() {
    switch (this.heading) {
      case "N":
        this.heading = "W";
        break;
      case "W":
        this.heading = "S";
        break;
      case "S":
        this.heading = "E";
        break;
      case "E":
        this.heading = "N";
        break;
      default:
        break;
    }
  }

  turnRight() {
    switch (this.heading) {
      case "N":
        this.heading = "E";
        break;
      case "E":
        this.heading = "S";
        break;
      case "S":
        this.heading = "W";
        break;
      case "W":
        this.heading = "N";
        break;
      default:
        break;
    }
  }

  moveForward() {
    switch (this.heading) {
      case "N":
        this.y += 1;
        break;
      case "E":
        this.x += 1;
        break;
      case "S":
        this.y -= 1;
        break;
      case "W":
        this.x -= 1;
         break;
      default:
        break;
    }
  }

  navigate(commands) {
    for (let i = 0; i < commands.length; i++) {
      switch (commands[i]) {
        case "L":
          this.turnLeft();
          break;
        case "R":
          this.turnRight();
          break;
        case "F":
          this.moveForward();
          break;
        default:
          break;
      }
    }
  }
}

module.exports = Insect;




Working of Insect:

def final_position(x, y, dir, cmds):
    directions = ['N', 'E', 'S', 'W']
    moves = {'N': (0, 1), 'E': (1, 0), 'S': (0, -1), 'W': (-1, 0)}
    for cmd in cmds:
        if cmd == 'L':
            dir = directions[(directions.index(dir) - 1) % 4]
        elif cmd == 'R':
            dir = directions[(directions.index(dir) + 1) % 4]
        else:
            dx, dy = moves[dir]
            x += dx
            y += dy
    return (x, y, dir)


Task 2

E-commerce platform working code:

<!DOCTPE html> 
	<html lang="en"> 
	
	<head> 
	<meta charset="utf-8" /> 
	<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no"> 
	<meta name="csrf-token" content="EbDbzkMch3gSQYdt8GhMOqKej4dWnSqJrd2maggi"> 
	<title>eStore-Shop</title> 
	
	<link rel="shortcut icon" type="image" href="/storage/settings\June2020\d6B3M8TN1HAiO77fbSpB.png"> 

	
	<link rel="stylesheet" type="text/css" href="https://estore.srxwebdesign.com/vendor/mckenziearts/laravel-notify/css/notify.css"/> <!-- Fontawesome --> 

	<link type="text/css" href="/frontend/vendor/@fortawesome/fontawesome-free/css/all.min.css" rel="stylesheet"> 

	
	<!-- Prism --> 
	<link type="text/css" href="/frontend/vendor/prismjs/themes/prism.css" rel="stylesheet"> 
	
	<!-- Front CSS --> 
	<link type="text/css" href="/frontend/css/front.css" rel="stylesheet"> 

	<!-- Owl CSS --> 
	<link type="text/css" href="/frontend/css/owl.carousel.min.css" rel="stylesheet"> 
	<!-- Custom CSS --> 
	<link type="text/css" href="/frontend/css/custom.css" rel="stylesheet"> 

	<!-- Star CSS --> 
	<link type="text/css" href="/frontend/css/star-rating-svg.css" rel="stylesheet"> 

	
	<!-- datatable CSS --> 
	<link type="text/css" href="/frontend/css/DataTables/css/jquery.dataTables.min.css" rel="stylesheet"> 

	
	</head> 
	
	<body> 
	<script>
	
	var notify = {
	timeout: "5000",
	animatedIn: "bounceInRight",
	animatedOut: "bounceOutRight",
	position: "top-right"
	}
	
	</script>
	<header class="header-global"> 
	<nav id="navbar-main" class="navbar navbar-main navbar-expand-lg headroom py-lg-3 px-lg-6 navbar-dark navbar-theme-primary"> 
	<div class="container"> 
	<a class="text-white" href="/"> 

	<h2>eStore</h2> 
	</a> 
	<div class="navbar-collapse collapse" id="navbar_global"> 
	<div class="navbar-collapse-header"> 
	<div class="row"> 
	<div class="col-6 collapse-brand"> 
	<a href="/"> 

	<h2>eStore</h2> 
	</a> 
	</div> 
	<div class="col-6 collapse-close"> 
	<a href="#navbar_global" role="button" class="fas fa-times" data-toggle="collapse" 
	data-target="#navbar_global" aria-controls="navbar_global" aria-expanded="false" 
	aria-label="Toggle navigation"></a> 
	</div> 
	</div> 
	</div> 
	<ul class="navbar-nav navbar-nav-hover navbar-nav ml-lg-auto"> 
	<li class="nav-item"><a class="nav-link" href="/">Home</a></li> 

	<li class="nav-item"><a class="nav-link" href="/shop">Shop</a></li> 

	<li class="nav-item"><a class="nav-link" href="/about">About</a></li> 

	<li class="nav-item"><a class="nav-link" href="/posts">News</a></li> 

	<li class="nav-item"><a class="nav-link" href="/contact">Contact</a></li> 

	
	<li class="nav-item dropdown"> 
	<a href="#" class="nav-link" data-toggle="dropdown" aria-controls="pages_submenu" aria-expanded="false" aria-label="Toggle pages menu item"> 
	<span class="nav-link-inner-text">My account</span> 
	<span class="fas fa-angle-down nav-link-arrow ml-2"></span> 
	</a> 
	<ul class="dropdown-menu" id="pages_submenu"> 
	<li><a class="dropdown-item" href="/login">Login</a></li> 

	<li><a class="dropdown-item" href="/register">Register</a></li> 

	</ul> 
	</li> 
	</ul> 
	
	</div> 
	
	<div class="d-none d-lg-block"> 
	<a href="/cart" class="text-white"><i class="fas fa-shopping-cart"></i> 

	<span class="badge badge-danger"> 
	1 
	</span> 
	</a> 
	</div> 
	
	<div class="d-flex d-lg-none align-items-center"> 
	<a href="/cart" class="text-white"><i class="fas fa-shopping-cart"></i> 

	<span class="badge badge-danger"> 
	1 
	</span> 
	</a> 
	<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbar_global" 
	aria-controls="navbar_global" aria-expanded="false" aria-label="Toggle navigation"><span 
	class="navbar-toggler-icon"></span> 
	</button> 
	</div> 
	</div> 
	</nav> 
	</header> 
	
	<main> 
	
	<div class="preloader bg-soft flex-column justify-content-center align-items-center"> 
	<div class="loader-element"> 
	<span class="loader-animated-dot"></span> 
	<h1>eStore</h1> 
	</div> 
	</div> 
	
	
	<!-- Hero --> 
	<section class="section-header bg-primary text-white"> 
	<div class="container"> 
	<div class="row justify-content-center"> 
	<div class="col-12 col-md-8 text-center"> 
	<h1 class="display-2 mb-3">Shop</h1> 
	
	</div> 
	</div> 
	</div> 
	</section> 
	
	<section class="bg-soft py-5"> 
	<div class="container"> 
	
	
	
	
	
	<div class="row"> 
	<div class="col-lg-9 push-md-3"> 
	<div class="row"> 
	<div class="col-lg-12"> 
	<div class="row"> 
	<div class="col-md-4"> 
	<div class="card card-product card-plain"> 
	<div class="card-image"> 
	<a href="/product/black-light"> 

	<img src="https://estore.srxwebdesign.com/storage/products/July2020/icIOFlJ3mny1lA0bSt9R.jpg" /> 

	</a> 
	</div> 
	<div class="card-body p-0 m-0"> 
	
	<h4 class="mt-3"><a href="/product/black-light">Black light</a></h4> 

	<p class="text-muted">Children</p> 
	<p> 
	<del>$200</del> $100 
	</p> 
	<div class="d-flex mb-4"> 
	
	
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star-half-alt text-warning"> </i> 
	
	<i class="far fa-star text-warning"> </i> 
	
	<i class="far fa-star text-warning"> </i> 
	
	</div> 
	</div> 
	</div> 
	<!-- end card --> 
	</div> 
	<div class="col-md-4"> 
	<div class="card card-product card-plain"> 
	<div class="card-image"> 
	<a href="/product/bin"> 

	<img src="https://estore.srxwebdesign.com/storage/products/July2020/BstVMVNBN42Vuvnd140D.jpg" /> 

	</a> 
	</div> 
	<div class="card-body p-0 m-0"> 
	
	<h4 class="mt-3"><a href="/product/bin">Bin</a></h4> 

	<p class="text-muted">Clothes</p> 
	<p> 
	<del>$200</del> $62 
	</p> 
	<div class="d-flex mb-4"> 
	
	
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star-half-alt text-warning"> </i> 
	
	<i class="far fa-star text-warning"> </i> 
	
	</div> 
	</div> 
	</div> 
	<!-- end card --> 
	</div> 
	<div class="col-md-4"> 
	<div class="card card-product card-plain"> 
	<div class="card-image"> 
	<a href="/product/bathroom-lamp"> 

	<img src="https://estore.srxwebdesign.com/storage/products/July2020/wbZ3Thr88J6KMjDioqil.jpg" /> 

	</a> 
	</div> 
	<div class="card-body p-0 m-0"> 
	
	<h4 class="mt-3"><a href="/product/bathroom-lamp">Bathroom Lamp</a></h4> 
	<p class="text-muted">Children</p> 
	<p> 
	<del>$234</del> $200 
	</p> 
	<div class="d-flex mb-4"> 
	
	
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star-half-alt text-warning"> </i> 
	
	<i class="far fa-star text-warning"> </i> 
	
	</div> 
	</div> 
	</div> 
	<!-- end card --> 
	</div> 
	<div class="col-md-4"> 
	<div class="card card-product card-plain"> 
	<div class="card-image"> 
	<a href="/product/black-clock"> 

	<img src="https://estore.srxwebdesign.com/storage/products/July2020/GaVU5lP5eJwWgWZRhsWb.jpg" /> 

	</a> 
	</div> 
	<div class="card-body p-0 m-0"> 
	
	<h4 class="mt-3"><a href="/product/black-clock">Black clock</a></h4> 

	<p class="text-muted">Men</p> 
	<p> 
	<del>$200.76</del> $100.66 
	</p> 
	<div class="d-flex mb-4"> 
	
	
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star text-warning"> </i> 
	
	<i class="fas fa-star-half-alt text-warning"> </i> 
	
	<i class="far fa-star text-warning"> </i> 
	
	</div> 
	</div> 
	</div> 
	<!-- end card --> 
	</div> 
	
	</div> 
	</div> 
	
	</div> 
	
	<div class="mt-3 text-center"> 
	
	</div> 
	</div> 
	<div class="col-lg-3 pull-md-9"> 
	<form class="form-inline" action="https://estore.srxwebdesign.com/shop/search"> 
	<div class="md-form my-0"> 
	<input class="form-control mr-sm-2" name="query" value="" type="text" placeholder="Search" aria-label="Search"> 
	</div> 
	</form> 
	<div class="ml-1"> 
	<h4 class="mt-3">Category</h4> 
	
	<ul class="list-unstyled"> 
	
	<li><a href="https://estore.srxwebdesign.com/shop/category?category=men">Men</a></li> 
	
	<li><a href="https://estore.srxwebdesign.com/shop/category?category=children">Children</a></li> 
	
	<li><a href="https://estore.srxwebdesign.com/shop/category?category=clothes">Clothes</a></li> 
	</ul> 
	</div> 
	
	</div> 
	</div> 
	</div> 
	</section> 
	
	<footer class="footer section pt-6 pt-md-8 pt-lg-10 pb-3 bg-primary text-white overflow-hidden"> 
	<div class="pattern pattern-soft top"></div> 
	<div class="container"> 
	<div class="row"> 
	<div class="col-lg-6 mb-4 mb-lg-0"> 
	<a class="footer-brand mr-lg-5 d-flex" href="/"> 

	<h2>eStore</h2> 
	</a> 
	<p class="my-4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus et dolor blanditiis consequuntur ex voluptates perspiciatis omnis unde minima expedita.</p> 
	</div> 
	<div class="col-6 col-sm-3 col-lg-2 mb-4 mb-lg-0"> 
	<h4>Navigation</h4> 
	<ul class="links-vertical"> 
	<li><a href="/">Home</a></li> 

	<li><a href="/projects">Projects</a></li> 

	<li><a href="/services">Services</a></li> 

	<li><a href="/about">About</a></li> 

	</ul> 
	</div> 
	<div class="col-6 col-sm-3 col-lg-2 mb-4 mb-lg-0"> 
	<h4>Useful Pages</h4> 
	<ul class="links-vertical"> 
	<li><a href="/page/privacy-policy">Privacy Policy</a></li> 

	<li><a href="/page/terms-condition">Terms &amp; Condition</a></li> 

	<li><a href="#">Terms of Service</a></li> 

	<li><a href="/contact">Contact</a></li> 

	
	</ul> 
	</div> 
	<div class="col-12 col-sm-3 col-lg-2"> 
	<h4>Social</h4> 
	<ul class="links-vertical"> 
	<li><a href="//facebook.com" target="_blank">Facebook</a></li> 

	<li><a href="//" target="_blank">Twitter</a></li> 

	<li><a href="//linkedin.com" target="_blank">LinkedIn</a></li> 

	<li><a href="//youtube.com" target="_blank">Youtube</a></li> 

	</ul> 
	</div> 
	</div> 
	<hr class="my-4 my-lg-5"> 
	<div class="row"> 
	<div class="col pb-4 mb-md-0"> 
	<div class="d-flex text-center justify-content-center align-items-center"> 
	<p class="font-weight-normal mb-0">© eStore <span class="current-year"></span>. All rights reserved.</p> 
	</div> 
	</div> 
	</div> 
	</div> 
	</footer> 
	</main> 
	<!-- Core --> 
	<script src="/frontend/vendor/jquery/dist/jquery.min.js"></script> 

	<!-- Datatables JS --> 
	<script src="/frontend/assets/js/datatables.min.js"></script> 

	
	<script src="/frontend/vendor/popper.js/dist/umd/popper.min.js"></script> 

	<script src="/frontend/vendor/bootstrap/dist/js/bootstrap.min.js"></script> 

	<script src="/frontend/vendor/headroom.js/dist/headroom.min.js"></script> 

	
	<!-- Vendor JS --> 
	<script src="/frontend/vendor/onscreen/dist/on-screen.umd.min.js"></script> 

	<script src="/frontend/vendor/waypoints/lib/jquery.waypoints.min.js"></script> 

	<script src="/frontend/vendor/jarallax/dist/jarallax.min.js"></script> 

	<script src="/frontend/vendor/smooth-scroll/dist/smooth-scroll.polyfills.min.js"></script> 

	
	<!-- Button Js --> 
	<script async defer src="/frontend/assets/js/button.js"></script> 

	
	<!-- Impact JS --> 
	<script src="/frontend/assets/js/front.js"></script> 

	<!-- Star JS --> 
	<script src="/frontend/assets/js/jquery.star-rating-svg.js"></script> 

	<!-- Owl JS --> 
	<script src="/frontend/assets/js/owl.carousel.min.js"></script> 

	<!-- Select2 JS --> 
	<script src="/frontend/assets/js/select2.min.js"></script> 

	<!-- Custom JS --> 
	<script src="/frontend/assets/js/custom.js"></script> 

	
	<script type="text/javascript" src="https://estore.srxwebdesign.com/vendor/mckenziearts/laravel-notify/js/notify.js"></script> </body> 

	
	</html> 


	
1.	With the help of XAMPP server we can view this application
https://estore.srxwebdesign.com/login

2.	The login page
3.	The products list page 
4.	Cart page

 

