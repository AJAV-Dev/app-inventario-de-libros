<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
    setup() {
        const nuevoLibro = ref({
            title: '',
                    author: '',
                    editorial: '',
                    year: '',
                    price: '',
                    stock: '',
                    description: '',
                    category: '',
                    ISBN: '',
                    image: '',
                    rating: ''
        });

        const agregarLibro = async () => {
            try {
                // Enviar los datos del nuevo libro al backend
                const response = await axios.post("https://app-inventario-de-libros.onrender.com/libros", nuevoLibro.value);

                // Mostrar mensaje de éxito
                setTimeout(() => {
                    alert("Libro agregado exitosamente");
                }, 200);

                // Limpiar los campos del formulario
                nuevoLibro.value = {
                    title: '',
                    author: '',
                    editorial: '',
                    year: '',
                    price: '',
                    stock: '',
                    description: '',
                    category: '',
                    ISBN: '',
                    image: '',
                    rating: ''
                };

                console.log("Libro agregado exitosamente:", response.data);
            } catch (error) {
                console.error("Error al agregar el libro:", error);
            }
        };

        return {
            nuevoLibro,
            agregarLibro
        };
    }
};
</script>

<template>
    <main>
        <form @submit.prevent="agregarLibro">
            <div>
                <label for="title">Título del libro</label>
                <input name="title" type="text" placeholder="Título del libro" v-model="nuevoLibro.title" required>
            </div>
            <div>
                <label for="author">Autor del libro</label>
                <input name="author" type="text" placeholder="Autor del libro" v-model="nuevoLibro.author" required>
            </div>
            <div>
                <label for="editorial">Editorial del libro</label>
                <input name="editorial" type="text" placeholder="Editorial del libro" v-model="nuevoLibro.editorial" required>
            </div>
            <div>
                <label for="year">Año de publicación</label>
                <input name="year" type="number" placeholder="Año de publicación" v-model="nuevoLibro.year" required>
            </div>
            <div>
                <label for="price">Precio del libro</label>
                <input name="price" type="text" placeholder="Precio del libro" v-model="nuevoLibro.price" required>
            </div>
            <div>
                <label for="stock">Número de ejemplares</label>
                <input name="stock" type="number" placeholder="Número de ejemplares" v-model="nuevoLibro.stock" required>
            </div>
            <div>
                <label for="description">Descripción del libro</label>
                <input name="description" type="text" placeholder="Descripción del libro" v-model="nuevoLibro.description" required>
            </div>
            <div>
                <label for="category">Género del libro</label>
                <input name="category" type="text" placeholder="Género del libro" v-model="nuevoLibro.category" required>
            </div>
            <div>
                <label for="ISBN">ISBN del libro</label>
                <input name="ISBN" type="text" placeholder="ISBN del libro" v-model="nuevoLibro.ISBN" required>
            </div>
            <div>
                <label for="rating">Valoración del libro</label>
                <input name="rating" type="text" placeholder="Imagen del libro" v-model="nuevoLibro.rating" required>
            </div>
            <div>
                <label for="image">Imagen del libro</label>
                <input name="image" type="text" placeholder="Imagen del libro" v-model="nuevoLibro.image" required>
            </div>
            <button type="submit">Crear libro</button>
        </form>
    </main>
</template>

<style>
/* Agrega estilos si es necesario */
</style>