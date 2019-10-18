<template>
  <div id="app">
    <div class="text-center">
      <h1>Namegator</h1>
      <br />
      <h6 class="text-secondary">Gerador de nomes com vue, node, boostrap, grahpQl</h6>
    </div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos
              <span class="badge badge-info">0</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="prefix in prefixes" :key="prefix">{{prefix}}</li>
                </ul>
                <br />
                <div class="input-group">
                  <input class="form-control" type="text" @keyup.enter="addPrefix(prefix)" placeholder="Digite o prefixo" v-model="prefix" />
                  <div class="input-group-append">
                    <button class="btn btn-info" @click="addPrefix(prefix)"><span class="fa fa-plus"></span></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <span class="badge badge-info">0</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="sufix in sufixes" :key="sufix">{{sufix}}</li>
                </ul>
                <br />
                <div class="input-group">
                  <input class="form-control" type="text" @keyup.enter="addSufix(sufix)" placeholder="Digite o sufixo" v-model="sufix" />
                  <div class="input-group-append">
                    <button class="btn btn-info" @click="addSufix(sufix)"><span class="fa fa-plus"></span></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>
          Domains
          <span class="badge badge-info">{{domains.length}}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" :key="domain">{{domain}}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "app",
	data() {
		return {
			prefix: "",
			sufix: "",
			prefixes: ["Air", "Jet", "Flight"],
			sufixes: ["Hub", "Station", "Mart"],
			domains: [
				"AirHub",
				"AirStation",
				"AirMart",
				"JetHub",
				"JetStation",
				"JetMart",
				"FlightHub",
				"FlightStation",
				"FlightMart"
			]
		};
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix);
			this.prefix = "";
			this.generate();
		},
		addSufix(sufix) {
			this.sufixes.push(sufix);
			this.sufix = "";
			this.generate();
		},
		generate() {
			this.domains = [];
			for (const prefix of this.prefixes) {
				for (const sufix of this.sufixes) {
					this.domains.push(`${prefix}${sufix}`);
				}
			}
		}
	}
};
</script>

<style>
#app {
  margin: 30px 0;
}
#main {
  background-color: #f1f1f1;
  padding: 30px 0;
}
</style>
