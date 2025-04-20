<script>
import axios from "axios";
import { ref, onMounted } from "vue";

export default {
    setup() {
    const libros = ref([]);

    const listarLibros = async () => {
        try {
        const response = await axios.get("http://localhost:3000/libros");
        libros.value = response.data;
        console.log(libros.value);
        } catch (error) {
        console.log("Error al obtener los libros desde el endpoint:", error);
}
    };

    const eliminarLibro = async (id, title) => {
        const confirmDelete = window.confirm(`¿Estás seguro de que deseas eliminar el libro: "${title}"?`);
        if (!confirmDelete) {
        return; // Si el usuario cancela, no hacemos nada
        }
        try {
        await axios.delete(`http://localhost:3000/libros/${id}`);
        console.log("Libro eliminado:", id);
        listarLibros(); // Actualiza la lista después de eliminar
        } catch (error) {
        console.log("Error al eliminar el libro:", error);
        }
    };

    onMounted(() => {
        listarLibros();
    });

    return {
        libros,
        listarLibros,
        eliminarLibro,
    };
    },
};

</script>


<template>
    <main>
        <table>
            <thead>
                <tr>
                    <th>id</th>
                    <th>Titulo</th>
                    <th>Autor</th>
                    <th>ISBN</th>
                    <th>Editorial</th>
                    <th>Año</th>
                    <th>Descripción</th>
                    <th>Imagen</th>
                    <th>Precio</th>
                    <th>Stock</th>
                    <th>Categoría</th>
                    <th>Valoración</th>
                    <th>Acciones</th>
                </tr>
            </thead>
            <tbody>
        <tr v-for="libro in libros" :key="libro.id">
        <td>{{ libro.id }}</td>
        <td>{{ libro.title }}</td>
        <td>{{ libro.author }}</td>
        <td>{{ libro.ISBN }}</td>
        <td>{{ libro.editorial }}</td>
        <td>{{ libro.year }}</td>
        <td>{{ libro.description }}</td>
        <td><img :src="libro.image" alt="Imagen del libro" /></td>
        <td>{{ libro.price }}</td>
        <td>{{ libro.stock }}</td>
        <td>{{ libro.category }}</td>
        <td>{{ libro.rating }}</td>
        <div>
        <button @click="eliminarLibro(libro.id, libro.title)">Eliminar</button>
        <router-link :to="{path:'editarLibro/' + libro.id}">Editar</router-link>
        </div>
        </tr>
</tbody>
        </table>
    </main>
</template>


<style >

</style>
