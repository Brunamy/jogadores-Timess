<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_time: "",
      times: [
        { id: "c09cc3cc-e7fa-11ec-8fea-0242ac120002", name: "Time 1" },
        { id: "b742b4f6-99b0-4eda-b2ca-c354b5301c53", name: "Time 2" },
        { id: "db3b45dc-e7fa-11ec-8fea-0242ac120002", name: "Time 3" },
        { id: "03ff2fce-e7fb-11ec-8fea-0242ac120002", name: "Time 4" },
      ],
    };
  },
  methods: {
    salvar() {
    if (this.novo_time !=="") {
      const novo_id = uuid();
      this.times.push( {
        id: novo_id,
        name: this.novo_time,
      });
      this.novo_time="";
      
    }
    },
  excluir(time) {
    const indice = this.times.indexOf(time);
    this.times.splice(indice, 1);
  },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Times</h2>
    </div>
    <div class="form-input">
      <input type="text" required v-model="novo_time" @keyup.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-itens">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="time in times" :key="time.id">
            <td>{{ time.id }}</td>
            <td>{{ time.name }}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(time)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style></style>
