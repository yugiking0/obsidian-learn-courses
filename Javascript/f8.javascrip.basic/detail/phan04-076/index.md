# Attribute node & Text node

---

![Document](Javascript/f8.javascrip.basic/detail/phan04-076/images/001.png 'Document')

- 1. Element
- 2. Attribute
- 3. Text

---

## 1. Element

![Element](Javascript/f8.javascrip.basic/detail/phan04-076/images/003.png 'Console')
![Element](Javascript/f8.javascrip.basic/detail/phan04-076/images/002.png 'Console')
![Element](Javascript/f8.javascrip.basic/detail/phan04-076/images/004.png 'Element')

-

## 2. Attribute node

- Trong một Element sẽ có những thuộc tính Attribute
  ![Attribute](Javascript/f8.javascrip.basic/detail/phan04-076/images/005.png 'Attribute')
  ![Attribute](Javascript/f8.javascrip.basic/detail/phan04-076/images/006.png 'Attribute')
  ![Attribute](Javascript/f8.javascrip.basic/detail/phan04-076/images/007.png 'Attribute')

- Ví dụ: Ta có 1 file html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>F8 - Javascript Basic</title>
  </head>

  <body>
    <h1 class="heading" id="heading" title="heading">Heading Text</h1>
  </body>
</html>
```

- `Element` sẽ là `<h1>Heading</h1>`
- Các `Attribute` sẽ là: class, id, title

## 3. Text node

- Là phần chữ của Element

![Text node](Javascript/f8.javascrip.basic/detail/phan04-076/images/008.png 'Text node')

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>My Web Page</title>
  </head>

  <body>
    <h1 class="headingClass">Welcome To My Web Page</h1>
  </body>
</html>
```

- `Text node` ở đây là `My Web Page` và `Welcome To My Web Page` tương ứng với 2 Elements có Tag `<title>` và `<h1>`
