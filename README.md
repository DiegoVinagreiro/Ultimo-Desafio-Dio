// Molde de objeto para representar personagens de jogos
function Personagem(nome, classe, nivel, pontosDeVida, pontosDeAtaque) {
  this.nome = nome;
  this.classe = classe;
  this.nivel = nivel;
  this.pontosDeVida = pontosDeVida;
  this.pontosDeAtaque = pontosDeAtaque;

  // Método para exibir informações do personagem
  this.exibirInfo = function() {
    console.log(`Nome: ${this.nome}`);
    console.log(`Classe: ${this.classe}`);
    console.log(`Nível: ${this.nivel}`);
    console.log(`Pontos de Vida: ${this.pontosDeVida}`);
    console.log(`Pontos de Ataque: ${this.pontosDeAtaque}`);
  };

  // Método para aumentar o nível do personagem
  this.aumentarNivel = function() {
    this.nivel++;
    console.log(`${this.nome} subiu para o nível ${this.nivel}!`);
  };

  // Método para atacar outro personagem
  this.atacar = function(outroPersonagem) {
    console.log(`${this.nome} atacou ${outroPersonagem.nome} causando ${this.pontosDeAtaque} de dano!`);
    outroPersonagem.receberDano(this.pontosDeAtaque);
  };

  // Método para receber dano
  this.receberDano = function(dano) {
    this.pontosDeVida -= dano;
    if (this.pontosDeVida <= 0) {
      console.log(`${this.nome} foi derrotado!`);
    } else {
      console.log(`${this.nome} sofreu ${dano} de dano e agora tem ${this.pontosDeVida} pontos de vida.`);
    }
  };
}

// Exemplo de uso do molde de objeto
const guerreiro = new Personagem("Aragorn", "Guerreiro", 10, 100, 20);
const mago = new Personagem("Gandalf", "Mago", 8, 80, 25);

// Exibir informações iniciais
console.log("Status inicial dos personagens:");
guerreiro.exibirInfo();
mago.exibirInfo();

// Guerreiro ataca o mago
console.log("\nBatalha:");
guerreiro.atacar(mago);

// Aumentar o nível do guerreiro
console.log("\nApós a batalha:");
guerreiro.aumentarNivel();
guerreiro.exibirInfo();
mago.exibirInfo();
