<template>
	<v-app>
		<v-toolbar>
			<v-toolbar-title v-if="pelloso">Jokenpô Do Pelloso</v-toolbar-title>
			<v-toolbar-title v-else>Jokenpô</v-toolbar-title>
			<v-spacer></v-spacer>
			<v-toolbar-items>
				<strong><v-checkbox class="mt-3" label="Você é o Mateus Pelloso?" v-model="pelloso"></v-checkbox></strong>
			</v-toolbar-items>
		</v-toolbar>
	
		<v-container fluid grid-list-lg style="min-height: 434px">
			<v-fade-transition mode="out-in">
				<v-layout v-if="show" key="0" wrap>
	
					<v-flex xs4 @click="(pelloso) ? pellosoFunc() : pedra()">
						<v-card>
							<v-img src="public/pedra.jpg" contain height="150"></v-img>
							<v-card-title class="title">Pedra</v-card-title>
						</v-card>
					</v-flex>
					<v-flex xs4 @click="(pelloso) ? pellosoFunc() : papel()">
						<v-card>
							<v-img src="public/papel.jpg" contain height="150"></v-img>
							<v-card-title class="title">Papel</v-card-title>
						</v-card>
					</v-flex>
					<v-flex xs4 @click="(pelloso) ? pellosoFunc() : tesoura()">
						<v-card>
							<v-img src="public/tesoura.jpg" contain height="150"></v-img>
							<v-card-title class="title">Tesoura</v-card-title>
						</v-card>
					</v-flex>
				</v-layout>
				<v-layout v-else key="1" justify-center>
					<v-btn flat @click="show = true" class="subheading"><strong>Jogar</strong></v-btn>
				</v-layout>
			</v-fade-transition>
		</v-container>
	
		<div class="text-xs-center">
			<v-dialog v-model="dialog" width="270">
				<v-card>
					<v-card-title class="headline grey lighten-2" primary-title>
						{{ title }}
					</v-card-title>
					<v-card-text>
						{{ content }}
					</v-card-text>
					<v-divider></v-divider>
					<v-card-actions>
						<v-spacer></v-spacer>
						<v-btn color="primary" flat @click="dialog = false, show = false">
							Sair
						</v-btn>
						<v-btn color="primary" flat @click="dialog = false">
							Jogar novamente
						</v-btn>
					</v-card-actions>
				</v-card>
			</v-dialog>
		</div>
	
		<div class="text-xs-center">
			<v-dialog v-model="dialog2" width="270">
				<v-card>
					<v-card-title class="headline grey lighten-2" primary-title>
						<v-avatar>
							<img src="public/pelloso.jpg" alt="John">
						</v-avatar>
						⠀Ganhou!
					</v-card-title>
					<v-card-text>
						Mateus Pelloso sempre ganha!
					</v-card-text>
					<v-divider></v-divider>
					<v-card-actions>
						<v-spacer></v-spacer>
						<v-btn color="primary" flat @click="dialog2 = false, show = false">
							Sair
						</v-btn>
						<v-btn color="primary" flat @click="dialog2 = false">
							Jogar novamente
						</v-btn>
					</v-card-actions>
				</v-card>
			</v-dialog>
		</div>
	
		<v-footer class="pa-3">
			Bernardo C. Franceschina
			<v-spacer></v-spacer>
			<div>&copy; {{ new Date().getFullYear() }}</div>
		</v-footer>
	
	</v-app>
</template>

<script>
	export default {
		data() {
			return {
				pelloso: false,
				dialog: false,
				dialog2: false,
				show: false,
				title: '',
				content: '',
			}
		},
		methods: {
			pellosoFunc: function() {
				this.dialog2 = true;
			},
			papel: function() {
				let bot1 = Math.floor((Math.random() * 3) + 1);
	
				if (bot1 == 1) {
					this.title = 'Ganhou!';
					this.content = 'O computador escolheu pedra e foi amassado, você ganhou!';
					this.dialog = true;
				}
				if (bot1 == 2) {
					this.title = 'Empate!';
					this.content = 'O computador escolheu papel também, empatou!';
					this.dialog = true;
				}
				if (bot1 == 3) {
					this.title = 'Perdeu!';
					this.content = 'O computador escolheu tesoura e lhe cortou, você perdeu!';
					this.dialog = true;
				}
			},
			pedra: function() {
				let bot1 = Math.floor((Math.random() * 3) + 1);
	
				if (bot1 == 1) {
					this.title = 'Empate!';
					this.content = 'O computador escolheu pedra também, empatou!';
					this.dialog = true;
				}
				if (bot1 == 2) {
					this.title = 'Perdeu!';
					this.content = 'O computador escolheu papel e lhe embrulhou, você perdeu!';
					this.dialog = true;
				}
				if (bot1 == 3) {
					this.title = 'Ganhou!';
					this.content = 'O computador escolheu tesoura e foi destruído, você ganhou!';
					this.dialog = true;
				}
			},
			tesoura: function() {
				let bot1 = Math.floor((Math.random() * 3) + 1);
	
				if (bot1 == 1) {
					this.title = 'Perdeu!';
					this.content = 'O computador escolheu pedra e lhe destruiu, você perdeu!';
					this.dialog = true;
				}
				if (bot1 == 2) {
					this.title = 'Ganhou!';
					this.content = 'O computador escolheu papel e foi cortado, você ganhou!';
					this.dialog = true;
				}
				if (bot1 == 3) {
					this.title = 'Empate!';
					this.content = 'O computador escolheu tesoura também, empatou!';
					this.dialog = true;
				}
			}
	
		}
	}
</script>
