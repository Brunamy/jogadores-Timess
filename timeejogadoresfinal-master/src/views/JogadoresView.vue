<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_times: "",
      jogadores: [
        { id: 1, name: "jogador 1", timeid: "1" },
        { id: 2, name: "jogador 2", timeid: "2" },
        { id: 3, name: "jogador 3", timeid: "3" },
        { id: 4, name: "jogador 4", timeid: "4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_jogador !=="") {
      const novo_id = uuid();
      this.novo_jogadores.push({
        id: novo_id,
        name: this.novo_jogador,
        name: this.novo_time,
      });
      this.novo_jogador = "";
      this.novo_time = "";
    }
  },
  excluir(jogador) {
    const indice = this.novo_jogadores.indexOf(jogador);
    this.novo_jogadores.splice(indice, 1);
  },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Jogadores</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" />
      <input type="text" placeholder="Time" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-itens">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Times</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="jogador in jogadores" :key="jogador.id">
            <td>{{ jogador.id }}</td>
            <td>{{ jogador.name }}</td>
            <td>{{ jogador.timeid }}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(jogador)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped></style>
