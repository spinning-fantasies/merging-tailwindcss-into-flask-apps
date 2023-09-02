# merging-tailwindcss-into-flask-apps

> Code from https://geekpython.in/merging-tailwindcss-into-flask-apps

## Step by step

1. Install Flask :

```
python -m pip install flask
```

2. Install Tailwind :

```
npm install tailwindcss
```

3. Creating a configuration file ``tailwind.config.js`` :

```
npx tailwindcss init
```

4. Update the configuration file

```
module.exports = {
  mode: 'jit',
  content: ["./templates/**/*.{html,htm}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

5. Creating CSS files and adding tailwind directives

```
mkdir -p static/{src,css}
```

6. Starting the build process

```
npx tailwindcss -i ./static/src/input.css -o ./static/css/main.css --watch
```

7. Update ``package.json``

```
{
  "dependencies": {
    "tailwindcss": "^3.1.8"
  },
 
  "scripts": {
    "create-css": "npx tailwindcss -i ./static/src/input.css -o ./static/css/main.css --watch"
  }
}
```

```
npm run create-css
```

8. Creating frontend with TailwindCSS

Link the css/main.css file in the Head tag inside the ``base.html``.
XHTML

```
<link href="{{url_for('static',filename='css/main.css')}}" rel="stylesheet">
```

