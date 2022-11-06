async function enviarScript(scriptText){
	const lines = scriptText.split(/[\n\t]+/).map(line => line.trim()).filter(line => line);
	main = document.querySelector("#main"),
	textarea = main.querySelector(`div[contenteditable="true"]`)
	
	if(!textarea) throw new Error("Não há uma conversa aberta")
	
	for(const line of lines){
		console.log(line)
	
		textarea.focus();
		document.execCommand('insertText', false, line);
		textarea.dispatchEvent(new Event('change', {bubbles: true}));
	
		setTimeout(() => {
			(main.querySelector(`[data-testid="send"]`) || main.querySelector(`[data-icon="send"]`)).click();
		}, 100);
		
		if(lines.indexOf(line) !== lines.length - 1) await new Promise(resolve => setTimeout(resolve, 250));
	}
	
	return lines.length;
}

enviarScript(`

É a união Flasco, mano, é sem caô
Batendo punheta com pau no ventilador
E se essa mina fala merda, vai ficar sem cabelo
Vou raspar a cabeça dela sem usar barbeador
É a união Flasco, Câmera Privê
Tu responde o chat enquanto eu meto ni você
Magé é do lado da minha casa, nessa porra caiu ET
Se eles brotar chei' de cutcharra, eu como eles e você
É a união Flasco, vai tomar no cu
Se tu é Fluminense, mano, chupa meu piru
Só tem maluco abafa-crack nessa porra dessa equipe
É o trem bala da colina carregando AR-15
É a união Flasco, nova ordem mundial
Os botafoguense tudo mamando o meu pau
E pra tu namorar comigo, vai ter que fazer anal
E se tiver dor de barriga, tu vai cagar no meu pau
É a união Flasco, bota o Gabigol
Ribamar cheirado nesse jogo, acelerou
Se tem traveco nessa festa, por que ninguém me avisou?
O meu flow tá tipo Ronaldo: se tem bunda, meto gol
É a união Flasco, puta que pariu
Tua boca é um colete e o meu pau é um fuzil
Não vem falar inglês pra mim, meu mano, eu moro no Brasil
Eu tô embrasado de Skol com funk do Buffalo Bill
É a união Flasco, tô passando o aço
Se tá respirando, eu taco-lhe o vapo-vapo
E se não tiver respirando, eu vejo se o corpo tá quente
Rima de necrofilia, um salve pro presidente
É a união Flasco, é a novidade
Eu ressuscitei e trouxe essa merda-postagem
A minha piroca é o porta-mala, tua bunda é bagagem
Tu não come travesti, mano, isso é muita viadagem
É a união Flasco, uh, uh, uh
Quem tá respirando gosta de lamber piru
Eu tô falando muita merda nesse beat do Haku
Se a tua raba é uma floresta, meu pau é o Zoboomafoo
É a união Flasco, passei Rexona
Eu não sou boiola pra ficar pickando Sona
Se a tua boca é um forró, a minha piroca é a sanfona
A xota dessa mina é verde, eu acho que eu comi a Fiona
É a união Flasco, é a seleção
Batendo punheta, mas eu nem tô com tesão
A quarentena tá chatona e meu pau tá na minha mão
Eu tô no meio da aula online e que se foda, meu irmão
É a união Flasco, mano, eu sou real
Uma track inteira só falando do meu pau
Eu sou o melhor do shitrap e nunca vai ter discussão
Esses mano pensa em dinheiro, eu penso na minha diversão
É a união Flasco, esse é o meu momento
Piscando meu cu, a pica faz o movimento
Cê pode ter várias view 'memo teu som sendo sem graça
Eu sou rei do underground e bato punheta na praça
É a união Flasco

`).then(e => console.log(`Código finalizado, ${e} mensagens enviadas`)).catch(console.error)
