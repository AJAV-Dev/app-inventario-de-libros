<script>
import axios from "axios";
import { ref, onMounted } from "vue";

export default {
    setup() {
    const libros = ref([]);

    const listarLibros = async () => {
        try {
        const response = await axios.get("https://app-inventario-de-libros.onrender.com/libros");
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
        await axios.delete(`https://app-inventario-de-libros.onrender.com/libros/${id}`);
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
        <td class="alinear" >{{ libro.id }}</td>
        <td>{{ libro.title }}</td>
        <td>{{ libro.author }}</td>
        <td>{{ libro.ISBN }}</td>
        <td>{{ libro.editorial }}</td>
        <td>{{ libro.year }}</td>
        <td>{{ libro.description }}</td>
        <td><img :src="libro.image" alt="Imagen del libro" /></td>
        <td class="alinear" >{{ libro.price }}</td>
        <td>{{ libro.stock }}</td>
        <td>{{ libro.category }}</td>
        <td>{{ libro.rating }}</td>
        <div class ="botones" >
        <button class="btn eliminar" @click="eliminarLibro(libro.id, libro.title)">Eliminar</button>
        <router-link class="btn editar" :to="{path:'editarLibro/' + libro.id}">Editar</router-link>
        </div>
        </tr>
</tbody>
        </table>
    </main>
</template>


<style scoped>
table {
    width: 100%;
    border-collapse: collapse;
    margin: 25px auto;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
}

td, th {
    border: 1px solid #575252;
    padding: 10px;
}

th {
    background-color: rgb(6, 105, 187);
    color: white;
}

.alinear {
    text-align: center;
}

img {
    width: 50px;
    height: 50px;
    object-fit: cover;
}

.botones {
    display: flex;
    justify-content: space-around;  
    border: solid 1px #575252;  
    padding: 10px;
    border-radius: 5px;
    background-color: #f0f0f0;
    margin: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s ease-in-out;
}


.btn {
    background-color: transparent;
    border: none;
    text-decoration: none;
    padding: 5px 10px;
    font-family: 'Roboto', sans-serif;
    color: black;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out;
    margin: 5px;
}

.eliminar {
    background-color: #ff4d4d;
    color: white;
    border-radius: 5px;
}

.eliminar:hover {
    background-color: #b40303;
    transition: background-color 0.3s ease-in-out;
}


.editar {
    background-color: orange;
    color: white;
    border-radius: 5px;
}

.editar:hover {
    background-color: #ff8c00;
    transition: background-color 0.3s ease-in-out;
}

</style>
