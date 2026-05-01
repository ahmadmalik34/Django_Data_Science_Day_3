# 📝 Blog Models & ORM

<div align="center">

**Master Django ORM and Database Relationships**

[![Django](https://img.shields.io/badge/Django-5.0%2B-darkgreen?style=flat-square&logo=django)](https://www.djangoproject.com/)
[![SQLite](https://img.shields.io/badge/Database-SQLite-blue?style=flat-square&logo=sqlite)](https://www.sqlite.org/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)](https://www.python.org/)

[Features](#-features) • [Installation](#-installation) • [Learn More](#-key-concepts)

</div>

---

## 🎯 Overview

Build a complete blog database with Author, Category, and Post models. Learn Django ORM fundamentals through pure CRUD operations in the Django shell.

**No admin panel yet. No web interface. Just models and queries.**

---

## ✨ Features

| Feature | Details |
|---------|---------|
| 👤 **Author Model** | User profiles with bio and profile image |
| 📂 **Category Model** | Blog post categories/tags |
| 📖 **Post Model** | Blog posts with relationships |
| 🔗 **Relationships** | ForeignKey and ManyToManyField |
| 💾 **Migrations** | Database schema versioning |
| 🐚 **Django Shell** | Interactive CRUD operations |

---

## 📦 Tech Stack

- **Framework:** Django 5.0+
- **Database:** SQLite3
- **ORM:** Django ORM
- **Language:** Python 3.8+

---

## 🚀 Quick Start

### Installation

```bash
# Create virtual environment
python -m venv venv

# Activate it
.\venv\Scripts\activate  # Windows
source venv/bin/activate  # macOS/Linux

# Install dependencies
pip install django python-decouple
```

### Create Models

```bash
python manage.py makemigrations
python manage.py migrate
```

### Access Django Shell

```bash
python manage.py shell
```

---

## 📚 CRUD Operations in Django Shell

### **Create**

```python
# Create an author
author = Author.objects.create(name="Ahmad", bio="Full-stack developer")

# Create categories
tech = Category.objects.create(name="Technology")
python = Category.objects.create(name="Python")

# Create a post
post = Post.objects.create(
    title="My First Django Post",
    content="Learning Django ORM...",
    author=author
)

# Add multiple categories (Many-to-Many)
post.categories.add(tech, python)
```

### **Read**

```python
# Get all posts
all_posts = Post.objects.all()

# Filter posts
python_posts = Post.objects.filter(categories__name="Python")

# Get single post
post = Post.objects.get(id=1)

# Count posts
post_count = Post.objects.count()
```

### **Update**

```python
# Update a post
post = Post.objects.get(id=1)
post.title = "Updated Title"
post.save()

# Bulk update
Post.objects.filter(author=author).update(published=True)
```

### **Delete**

```python
# Delete single post
post = Post.objects.get(id=1)
post.delete()

# Bulk delete
Post.objects.filter(author=author).delete()
```

---

## 🗄️ Database Models

### Author Model
```python
class Author(models.Model):
    name = CharField(max_length=100)
    bio = TextField()
    created_at = DateTimeField(auto_now_add=True)
```

### Category Model
```python
class Category(models.Model):
    name = CharField(max_length=50, unique=True)
    description = TextField(blank=True)
```

### Post Model
```python
class Post(models.Model):
    title = CharField(max_length=200)
    content = TextField()
    author = ForeignKey(Author, on_delete=models.CASCADE)
    categories = ManyToManyField(Category)
    created_at = DateTimeField(auto_now_add=True)
    updated_at = DateTimeField(auto_now=True)
```

---

## 🔑 Key Concepts

### ForeignKey
One-to-many relationship. A post belongs to one author.

### ManyToManyField
Many-to-many relationship. A post can have many categories, and a category can have many posts.

### Migrations
Django's version control for databases. `makemigrations` creates migration files, `migrate` applies them.

### QuerySet
Django's database query API. `Post.objects.all()` returns a QuerySet.

---

## 📖 What You'll Learn

✅ Define Django models with fields and relationships  
✅ Create migrations and apply them  
✅ Use QuerySet API for CRUD operations  
✅ Filter, exclude, and aggregate data  
✅ Understand ForeignKey and ManyToManyField  
✅ Access related objects  
✅ Use the Django shell for testing  

---

## 🔄 Next Steps

- **Day 4:** Create a Django admin panel to manage data
- **Day 5:** Build public-facing templates and views

---

<div align="center">

**Day 3 of 50 — Django × Data Science Challenge**

Learning Django ORM and database design.

</div>