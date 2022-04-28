class Jogos{
    constructor(nome, preco){
        this.nome = nome
        this.preco = preco
    }}
    const zelda = new Jogos('Zelda', 100) 
    const thesims = new Jogos('The Sims',120) 
    const castlevania = new Jogos('Castlevania',170) 
    const gta = new Jogos('GTA', 172) 
    const cod = new Jogos('Cod',179) 
    const goldmax = new Jogos('Gold Max',125) 
    const candycrush = new Jogos('Candy Crush',112) 
    const wow = new Jogos('Wow',130) 
    const fifa99 = new Jogos('Fifa 99',165) 
    const supermario = new Jogos('Super Mario',171) 
    const assassinscreed = new Jogos('Assasins Creed',180) 
 
//colocar nº menor antes do pivo
function encontraMenores (pivo,array){
    let menores = 0
       for(let atual = 0; atual < array.length; atual++){
        let produtoAtual = array[atual]
        if(produtoAtual.preco < pivo.preco){
        menores ++
        }
    }
    trocaLugar(array,array.indexOf(pivo),menores)
    return array
     }
function trocaLugar(array,de,para){
    const elem1 = array[de]
    const elem2 = array[para]

    array[para] = elem1
    array[de] = elem2 
    }  
function divideNoPivo(array,){
    let pivo = array[Math.floor(array.length / 2)]
    encontraMenores(pivo,array)
    let valoresMenores = 0

    for(let analisando = 0;analisando < array.length; analisando ++){
        let atual = array[analisando]
        if(atual.preco < pivo.preco){
    trocaLugar(array,analisando,valoresMenores)
    valoresMenores ++
    }
}
        
    return array
}
//ordenar do lado direito e depois do esquerdo
// - 1 para ficar antes do pivo
function quickSort(array, esquerda, direita) {
    if(array.length > 1) {
        let indiceAtual = particiona(array, esquerda, direita);
    if(esquerda < indiceAtual - 1) {
        quickSort(array, esquerda, indiceAtual - 1);
    }
    if(indiceAtual <direita) {
        quickSort(array, indiceAtual, direita)
    }
    }
    return array;
}

//comparação de direita e esquerda e troca de lugar
 function particiona(array, esquerda, direita) {
     let pivo = array[Math.floor((esquerda+direita) / 2)]
     let atualEsquerda = esquerda;
     let atualDireita = direita;

while(atualEsquerda <= atualDireita){
    while(array[atualEsquerda].preco < pivo.preco){
        atualEsquerda++
        }
    while(array[atualDireita].preco > pivo.preco){
        atualDireita--
    }
    if(atualEsquerda <= atualDireita){
        trocaLugar(array, atualEsquerda, atualDireita);
        atualEsquerda++
        atualDireita--
    }
    }
    return atualEsquerda
 }  

    const jogos = []
    jogos.push(zelda,thesims,castlevania,gta,cod,goldmax,candycrush,wow,fifa99,supermario,assassinscreed)
    module.exports = jogos

console.log(jogos)
console.log(divideNoPivo(jogos))
console.log(quickSort(jogos,0, jogos.length - 1))
const listasJogos = quickSort(jogos, 0, jogos.length - 1)
module.exports = listasJogos
