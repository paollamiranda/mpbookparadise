<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      editoras: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "Seguinte",site:"www.nomedosite" },
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "Record",site:"www.nomedosite" },
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "Companhia da Letras",site:"www.nomedosite" },
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "Rocco",site:"www.nomedosite"},
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "Darkside Books" ,site:"www.nomedosite"},
      ],
      nova_editora: "",
      novo_site:"",
    };
  },

  methods: {
    salvar() {
      if (this.nova_editora !== "") {
        const novo_id = uuidv4();
        this.editoras.push({
          id: novo_id,
          nome: this.nova_editora,
          site: this.novo_site,
        });
        this.nova_editora = "";
        this.novo_site = "";
      }
    },
    excluir(editora) {
      const indice = this.editoras.indexOf(editora);
      this.editoras.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Editora" v-model="nova_editora" />
      <input type="text" placeholder="WWW.site" v-model="novo_site" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-editoras">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Site</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editora in editoras" :key="editora.id">
            <td>{{ editora.id }}</td>
            <td>{{ editora.nome }}</td>
            <td>{{ editora.site}}</td>
            <td>
              <button class="excluir" @click="excluir(editora)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
.title {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}
.form-input {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}

.form-input input {
  width: 60%;
  height: 40px;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 0 10px;
}

.form-input button {
  margin-left: 1%;
  width: 20%;
  height: 40px;
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  background-color: rgb(0, 0, 0);
  color: white;
  font-weight: bold;
  cursor: pointer;
}

.list-editoras {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  margin: 2% auto;
  border-collapse: collapse;
}

table tr th {
  border: 1px solid #ccc;
  padding: 10px;
  font-weight: bold;
}

table tr td {
  border: 1px solid #ccc;
  padding: 10px;
}

table tr:nth-child(odd) {
    background-color: aliceblue;
}
.excluir{
  background-color: black;
  color: white;
  border:white;
  border-radius: 20px;
  width: 93%;
  height: 30px;
}
</style>
