<template>
  <ListModel
    title="Ejercicios"
    :table_info="{
      columns: [
        { query: 'id', verbose: 'ID' },
        { query: 'name', verbose: 'Nombre' },
        { query: 'description', verbose: 'Descripción' },
        { query: 'status', verbose: 'Estado' },
      ],
      actions: ['detail', 'update', 'delete'],
      api_endpoint: '/exercises/',
      sorting_column: 'id',
    }"
    @go-to-create="$router.push({ name: 'new_exercise' })"
    @go-to-update="goToUpdate"
    @go-to-delete="goToDelete"
    @go-to-detail="goToDetail"
  />
</template>

<script>
import ListModel from "../../../components/listModel";
export default {
  name: "Exercises",
  components: {
    ListModel,
  },
  methods: {
    goToUpdate(exercise_id) {
      this.$router.push({
        name: "edit_exercise",
        params: { exercise_id },
      });
    },
    goToDelete(id) {
      console.log("Delete the element", id);
    },
    goToDetail(exercise_id) {
      this.$router.push({
        name: "view_exercise",
        params: { exercise_id },
      });
    },
  },
};
</script>
