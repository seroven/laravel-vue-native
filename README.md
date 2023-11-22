# Creación del Proyecto

## Configuración Vue
1. Instalar dependencias
```
npm install vue@next
npm install vue-loader@next
npm install --save-dev @vitejs/plugin-vue
```
2. Configurar `vite.config.js` utilizando el plugin de vue para laravel.
```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
    plugins: [
        vue(),
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});

```
3. Crear componente App.vue para luego montarlo en la configuración del `app.js`.
4. Borrar la vista blade `welcome.blade.php` por defecto y crear `app.blade.php`. Dentro colocar una etiqueta div con el id `#app` y la configuración del vite.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Vue with laravel</title>
</head>
<body>
    <div id="app"></div>
    @vite('resources/js/app.js')
</body>
</html>
```
5. Crear la app con vue usando el componente App.vue y montar la vista blade base.
```
import './bootstrap';
import App from './App.vue';
import { createApp } from 'vue';

const app = createApp(App);
app.mount('#app');
```
6. Cambiar vista inicial en el `web.php` y que apunte a la vista blade `app`.