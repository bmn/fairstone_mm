Technical changes on index.html
===
* [L4,14] The Bootstrap and Popper JS frameworks are already provided by `bootstrap.bundle`, but have been linked to in their own right. Popper also isn't used anywhere in the current page.
  * remove link to those frameworks so `bootstrap.bundle` is the only used JS framework
* [L24] Nav section is in the `<head>` section
  * move it to the `<body>` section
* [L24] Nav section has doubled class attribute. It has no unique classes, so while it is ignored, it does not cause any problems.
  * remove second class attribute
* [L24,69] Nav section, and section containing button for model, have ID `#alignment` when it should be class `.alignment`
  * change to `class="alignment"`
* [L26] Nav link to About page links to `abou.html`
  * change to `about.html`
* [L26] Nav link to About page has `aria-current="page"` when it's not the current page (accessibility)
  * remove `aria-current="page"`
* [L35] Carousel section has doubled class attribute (again, no unique classes)
  * remove second class attribute
* [L46,53] Headers for 2nd/3rd carousel items are `h6` (smaller) rather than `h1` established by the first item
  * change to `<h1>`
* [L51] Carousel attempts to load (image2 > image1 > image4) when image4 is not available, image3 available but not used
  * change to `image3.jpg`
  * no change to order (assume 2 > 1 is intentional)
* [L78] Modal content image uses inline `style="width:100%"` instead of Bootstrap class (nitpick)
  * change to `class="w-100"`
* [L89] JS script is placed after the end of the `body` section, when it should be in either the `head` or `body`
  * move `</body>` to after script
* [L95] `.title` class `font-size` misspelled `fontsize`
  * change to `font-size`
* [L114] `.carousel-caption` class `color` misspelled `colour`
  * change to `color`
* [L128] Modal style has duplicate `background-color` line
  * remove first instance of `background-color`
* [L156] JS searches for modal popup at ID `#myModals` when ID is `#myModal` (modal popup fails)
  * change to `#myModal`
* [L166] JS sets modal display to `none` when it should be displayed (modal popup fails)
  * change to `block`
* `img/image3.jpg`, while pretty, has both a very high resolution and very high filesize
  * reduce resolution to better match the other carousel images
* `msh.jpg` is in root directory
  * move to `img` directory
* CSS on page is not reusable
  * move CSS to new file `css/style.css` and link in page

Stylistic changes
===
* Nav bar links and main title are too close together
  * separate main title (to left) and links (to right) by use of containers and `.ms-auto` class
  * collapse nav bar links into toggleable menu when width below medium
* Carousel images are of varying sizes, causing page flow to change on each transition
  * crop larger images (image1/image3) to match aspect ratio of smallest image (image2)
  * add `.ratio` class and `--bs-aspect-ratio` definition to carousel wrapper to ensure items cut off their images if necessary to maintain aspect ratio in the future
* Carousel caption text is black against mostly-dark backgrounds, causing poor readability
  * add translucent white background to aid contrast
* Carousel caption paragraph text is overly small
  * change from `<p>` to `<h5>` - CSS probably better for good practice, but `h5` fits the layout well
* Main content section (containing modal button) is squashed between other sections
  * add `.main-section` class to add padding to section
* Footer text is misaligned to top of section
  * use `div.main-section` instead of `p`

Won't Fix
===
* Carousel images have alt text set to "..." rather than a description of the image
  * assume intentional for simplicity
* Captions for carousel items are hidden at client widths below medium
  * assume intentional for simplicity
* Modal functionality could be achieved without any JS code using Bootstrap modal attributes, and only supports a single use per page
  * assume intentional for purpose of task

Wouldn't Fix If You Asked Me To
===
* Burlywood is a brilliant name for a colour


Approach for new website
===
MM's initial need is a like-for-like replacement for their simple HTML promotional site, with perhaps the ability to add new informational/blog pages. For that need, any lightweight CMS system (e.g. WordPress) would be suitable and the outright use of a pagebuilding framework (e.g. Laravel) likely an overcomplication. MM foresees the possibility of having product listings in the future though. That would be achievable without the need for an e-commerce solution, by having (ideally custom-templated) categories within the CMS to add each product or set of products as a page within that category.

However, given that this is a new-build site, it would make sense to consider potential future business direction if it wouldn't greatly increase the workload. Should MM have a significant number of products (say, more than 20), there may be value in using a low-complexity integrated e-commerce solution (e.g. WooCommerce on top of WordPress) even if there's no intention to sell on the platform. That would simplify the addition and maintenance of larger numbers of products and keep things more consistent. If MM then decides to go in the direction of e-commerce in the future, they already have a site and dataset that would need minimal work to achieve it, along with working experience of an e-commerce platform that would help inform the organisation of their product lineup.
