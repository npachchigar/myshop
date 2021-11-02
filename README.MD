MyShop
# create vertual env
python -m venv /c/users/name/envs/myshop
source /c/users/name/envs/myshop/Scripts/activate

# Create product catalog models
Edit the models.py file of the shop application
- add class Category(models.Model):
- add class Product(models.Model):

# deal with images in models
pip install Pillow

# create initial migrations for project
- python manage.py makemigrations
- python manage.py migrate 

# Register catalog models on the administration site
Edit the admin.py file of the shop application
- from .models import Category, Product
- @admin.register(Category)
- @admin.register(Product)

# create a superuser
python manage.py createsuperuser

- Start the development server with the command python manage.py runserver.
Open http://127.0.0.1:8000/admin/shop/product/add/

# Building catalog views
Edit the views.py file of the shop application
- def product_list(request, category_slug=None):
then add
- def product_detail(request, id, slug):

Create a new file inside the shop application directory and name it urls.py.
- app_name = 'shop'
  urlpatterns = []

Edit the urls.py file of the myshop project
- path('', include('shop.urls', namespace='shop')),

Edit the models.py file of the shop application, import the reverse() function,
and add a get_absolute_url() method to the Category and Product models.

# Create catalog templates
Create directory and file structure inside the shop application
templates/
   shop/
        base.html
        product/
            list.html
            detail.html

Include the CSS styles, which are located in the static/ directory of the
shop application            