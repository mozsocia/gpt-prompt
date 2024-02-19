give me html form for below "Product" model , using given html form template
- give every model field html from input, do not skip any 


-----------------------------------

give me html form for below "Product" model , using given html form template
- give every model field html from input, do not skip any, give full code , do not say to do any code myself




```
class Product(models.Model):
    title = models.CharField(max_length=200, null=False)
    short_desc = models.CharField(max_length=500, null=False)
    price = models.CharField(max_length=50, null=False)
    points = models.IntegerField(null=False, default=0)
    discount = models.BooleanField(blank=True, null=True)
    discount_price = models.CharField(max_length=50, blank=True, null=True)
    image = models.ImageField(upload_to='product_images/', null=False) 
    stock = models.BooleanField(null=False, default=0)
    star = models.FloatField(null=False, default=4.5)
    remark = models.CharField(max_length=10, choices=[('popular', 'Popular'), ('new', 'New'), ('top', 'Top'), ('special', 'Special'), ('trending', 'Trending'), ('regular', 'Regular')], null=False)
    category = models.ForeignKey(Category, on_delete=models.RESTRICT, null=True)
    brand = models.ForeignKey(Brand, on_delete=models.RESTRICT, null=True)

    img1 = models.ImageField(upload_to='product_images/', blank=True, null=True)  
    img2 = models.ImageField(upload_to='product_images/', blank=True, null=True)
    img3 = models.ImageField(upload_to='product_images/', blank=True, null=True)
    img4 = models.ImageField(upload_to='product_images/', blank=True, null=True)
    desc = models.TextField(blank=True, null=True)
    color = models.CharField(max_length=200, blank=True, null=True)
    size = models.CharField(max_length=200, blank=True, null=True)

    variations = models.JSONField(blank=True, null=True) 

    additional_info = models.JSONField(blank=True, null=True)  
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```


```
<form class="row g-3 mt-0">
    <div class="col-md-6">
        <label class="form-label">First Name</label>
        <input type="text" class="form-control" placeholder="First name"
            aria-label="First name">
    </div>
    <div class="col-md-6">
        <label class="form-label">Last Name</label>
        <input type="text" class="form-control" placeholder="Last name"
            aria-label="Last name">
    </div>
    <div class="col-md-6">
        <label for="inputEmail4" class="form-label">Email</label>
        <input type="email" class="form-control" id="inputEmail4">
    </div>
    <div class="col-md-6">
        <label for="inputPassword4" class="form-label">Password</label>
        <input type="password" class="form-control" id="inputPassword4">
    </div>
    <div class="col-12">
        <label for="inputAddress" class="form-label">Address</label>
        <input type="text" class="form-control" id="inputAddress"
            placeholder="1234 Main St">
    </div>
    <div class="col-12">
        <label for="inputAddress2" class="form-label">Address 2</label>
        <input type="text" class="form-control" id="inputAddress2"
            placeholder="Apartment, studio, or floor">
    </div>
    <div class="col-md-6">
        <label for="inputCity" class="form-label">City</label>
        <input type="text" class="form-control" id="inputCity">
    </div>
    <div class="col-md-4">
        <label for="inputState" class="form-label">State</label>
        <select id="inputState" class="form-select">
            <option selected>Choose...</option>
            <option>...</option>
        </select>
    </div>
    <div class="col-md-2">
        <label for="inputZip" class="form-label">Zip</label>
        <input type="text" class="form-control" id="inputZip">
    </div>
    <div class="col-12">
        <div class="form-check">
            <input class="form-check-input" type="checkbox" id="gridCheck3">
            <label class="form-check-label" for="gridCheck3">
                Check me out
            </label>
        </div>
    </div>
    <div class="col-12">
        <button type="submit" class="btn btn-primary">Sign in</button>
    </div>
</form>
