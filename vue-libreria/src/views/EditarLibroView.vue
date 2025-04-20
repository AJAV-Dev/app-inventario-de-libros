<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import { useRouter, useRoute } from 'vue-router';

export default {   
    setup() {

        const router = useRouter();

        const editarLibro = ref({
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
    
    const cargarLibro = async () => {
            const libroId = useRoute.params.id;
            try {
               // Obtener los datos del libro desde el backend
                const response = await axios.get(`http://localhost:3000/libros/${libroId}`);
                editarLibro.value = response.data;
            } catch (error) {
                console.error("Error al cargar el libro:", error);
            }
    };

    const actualizarLibro = async () => {
        try {
            // Enviar los datos del nuevo libro al backend
            await axios.put(`http://localhost:3000/libros/${editarLibro.value.id}`, editarLibro.value);

            // Mostrar mensaje de éxito
            setTimeout(() => {
                alert("Libro actualizado exitosamente");
            }, 200);

               // Redirigir a la vista de libros
            router.push('/');    
        } catch (error) {
            console.error("Error al actualizar el libro:", error);
        }   
    };

    onMounted(() => {
        cargarLibro();
    });

    return {
        editarLibro,
        actualizarLibro,
        cargarLibro
    };
    }
};
</script>


<template>
    <main>
        <form @submit.prevent="actualizarLibro">
            <div>
                <label for="title">Título del libro</label>
                <input name="title" type="text" placeholder="Título del libro" v-model="actualizarLibro.title" required>
            </div>
            <div>
                <label for="author">Autor del libro</label>
                <input name="author" type="text" placeholder="Autor del libro" v-model="actualizarLibro.author" required>
            </div>
            <div>
                <label for="editorial">Editorial del libro</label>
                <input name="editorial" type="text" placeholder="Editorial del libro" v-model="actualizarLibro.editorial" required>
            </div>
            <div>
                <label for="year">Año de publicación</label>
                <input name="year" type="number" placeholder="Año de publicación" v-model="actualizarLibro.year" required>
            </div>
            <div>
                <label for="price">Precio del libro</label>
                <input name="price" type="text" placeholder="Precio del libro" v-model="actualizarLibro.price" required>
            </div>
            <div>
                <label for="stock">Número de ejemplares</label>
                <input name="stock" type="number" placeholder="Número de ejemplares" v-model="actualizarLibro.stock" required>
            </div>
            <div>
                <label for="description">Descripción del libro</label>
                <input name="description" type="text" placeholder="Descripción del libro" v-model="actualizarLibro.description" required>
            </div>
            <div>
                <label for="category">Género del libro</label>
                <input name="category" type="text" placeholder="Género del libro" v-model="actualizarLibro.category" required>
            </div>
            <div>
                <label for="ISBN">ISBN del libro</label>
                <input name="ISBN" type="text" placeholder="ISBN del libro" v-model="actualizarLibro.ISBN" required>
            </div>
            <div>
                <label for="rating">Valoración del libro</label>
                <input name="rating" type="text" placeholder="Imagen del libro" v-model="actualizarLibro.rating" required>
            </div>
            <div>
                <label for="image">Imagen del libro</label>
                <input name="image" type="text" placeholder="Imagen del libro" v-model="actualizarLibro.image" required>
            </div>
            <button type="submit">Guardar cambios</button>
        </form>
    </main>
</template>


<style>

</style>