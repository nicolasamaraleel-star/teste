# Horário de Pico: Briga no Busão — Gameplay retrô 16-bit

## Entrega
Esta edição **preserva integralmente as artes de abertura e de transição** do ZIP fornecido. A mudança visual é **somente no gameplay e no HUD**. O sistema de combate, o movimento, o cálculo de dano, os itens, o Firebase, a pontuação, as fases e as cinemáticas continuam sob a mesma lógica existente.

## O que foi implementado
1. `src/game/retroSprites.ts` (novo) — lutadores **desenhados em pixels pelo próprio código**, incluindo o herói, todos os tipos de inimigos e chefes. Não usa artes externas, não depende de IA em tempo de execução e preserva as características distintivas de cada inimigo (mochila, uniforme, etc.). Possui estados para caminhar, atacar, defender, pular, girar, receber dano, descansar no banco e usar itens.
2. `src/game/engine.ts` — troca **somente as chamadas de desenho** do herói e dos inimigos. O jogo continua calculando movimento, golpes, colisões e pontuação com as funções originais. Renderiza em resolução lógica 480 × 270 e amplia para 960 × 540 pelo método nearest-neighbor, mantendo as coordenadas de jogo. Partículas e textos flutuantes agora desaparecem gradualmente.
3. `src/game/vectorArt.ts` — piso do ônibus com tons sólidos e textura discreta de pixels. Toda a arquitetura, janelas, bancos, catraca, validador e mecânicas continuam presentes.
4. `src/components/GameHUD.tsx` e `src/index.css` — UI arcade com barras retas, contornos fortes, cores menos saturadas e textura retrô. Em dispositivos móveis, os controles virtuais usam Pointer Events e permitem pressionar duas direções ao mesmo tempo.
5. `src/App.tsx` — aplica renderização pixelated apenas ao Canvas do **gameplay**. Não muda o componente da introdução.

## Como instalar no Google AI Studio
- Faça uma cópia do projeto atual antes de alterar os arquivos.
- Na edição completa: use os arquivos do ZIP `horario_de_pico_retro_16bit_completo.zip` para substituir os arquivos do projeto.
- Na edição parcial: use `horario_de_pico_retro_16bit_alteracoes.zip` e copie apenas os caminhos que aparecem dentro dele. **O arquivo `src/game/retroSprites.ts` é obrigatório**, pois é importado pelo motor.
- Execute o projeto normalmente, mantendo suas próprias variáveis de ambiente e configuração Firebase. **Não substitua seu `.env` por um arquivo de exemplo.**
- Teste uma partida da Linha 101, depois as linhas seguintes, e confirme especialmente: soco, combo, chute, bengala, mochila, desodorante, alça, validar passagem, descansar no banco, pausa, som, chefes, tela de vitória e ranking.

## Arquivos de cenas preservados
- Todos os 18 JPG em `src/assets/images/` foram comparados por hash com o ZIP original e permaneceram idênticos.
- `src/components/IntroStoryboard.tsx` e `src/game/introFrames.ts` não foram modificados.
- `src/components/GameModals.tsx` e `src/components/TitleScreen.tsx` também não foram modificados.
- Nenhum arquivo das cinemáticas foi gerado novamente, cortado, substituído ou sobrescrito.

## Verificações efetuadas
- TypeScript dos módulos `engine.ts` e `retroSprites.ts` com dependências de código do jogo: passou.
- Sintaxe TypeScript/TSX dos arquivos alterados: passou.
- Renderização isolada em Canvas da arte atualizada: passou (imagem `previa_gameplay_16bit.png` acompanha a entrega fora do ZIP).
- Não foi possível realizar o build Vite completo: o ZIP original não inclui `node_modules`, e esta sessão não dispõe de instalação das dependências npm.

## Notas de desenho
- O visual tem **referência genérica** à linguagem de jogos 16-bit, sem reproduzir sprites licenciados de outros jogos.
- Este é um primeiro conjunto funcional de sprites autorais de estilo pixel art. As fases são mantidas e os novos desenhos podem ser refinados isoladamente no arquivo `retroSprites.ts` sem mudar os hitboxes.
- O instante do acerto permanece no motor original, para não alterar o equilíbrio de combate. A animação é visual e não interfere nos cálculos de dano.
