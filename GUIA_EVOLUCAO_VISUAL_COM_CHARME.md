# Horário de Pico: Briga no Busão — Retrô sem perder o charme

## Direção visual escolhida
A referência de fliperama 16-bit serve como acabamento, **não como substituição da personalidade do jogo original**. A arte das cenas iniciais e de transição permanece 100% intacta.

Este ajuste corrige a primeira experiência com personagens demasiadamente simples e quadriculados: a gameplay agora usa **as funções de desenho dos personagens originais** como base para sprites rasterizados em grade pixelada e ampliados com nearest-neighbor. Isso preserva rosto, roupa, gravata, mochila, bengala, características dos inimigos e chefes.

## O que mudou
- `src/game/heritageSprites.ts` (novo): converte as ilustrações originais dos personagens em quadros pixelados com atualização visual em 12 FPS e cache limitado. Personagens ligeiramente maiores, mantendo o ponto de apoio no chão e a altura do pulo. Poses de ataque ganham um pequeno avanço/recuo gráfico e linhas de movimento sem mudar dano ou colisões.
- `src/game/engine.ts`: usa o novo renderizador para jogador/inimigos; barras de vida e falas acompanham a altura visual atualizada. Mantém a renderização pixelated, os efeitos, a pontuação, as fases e a lógica de combate da implementação anterior.
- `src/game/vectorArt.ts`: restaura a pintura original do piso do ônibus, com degradê azul. Todo o interior original continua em uso.
- `src/components/GameHUD.tsx` e `src/index.css`: mantém a interface retrô e os controles multitouch da versão anterior; as pequenas animações de combo no HUD voltam a aparecer.
- `src/App.tsx`: mantém a separação entre Canvas de gameplay e cenas iniciais.

## O que NÃO mudou
- Todas as 18 imagens originais em `src/assets/images/`: verificadas por hash, idênticas à última versão fornecida.
- `src/components/IntroStoryboard.tsx`, `src/game/introFrames.ts`, `src/components/GameModals.tsx` e `src/components/TitleScreen.tsx`: inalterados.
- Nenhum sistema de combate, energia, itens, fases, ranking, Firebase ou pontuação foi alterado nesta revisão.

## Usar no Google AI Studio
1. Salve uma cópia do projeto que funciona atualmente.
2. Importe os arquivos do ZIP completo como **nova cópia** do projeto (mais seguro). Para aplicar apenas arquivos alterados sobre a última versão enviada originalmente, extraia o ZIP de alterações respeitando a estrutura de pastas. O arquivo `heritageSprites.ts` é obrigatório.
3. Mantenha as configurações e variáveis de ambiente do seu projeto; não compartilhe chaves de API em arquivos ZIP.
4. Confira as linhas 101, 202, 303, o soco de três hits, chute, defesa da mochila, bengala, validador, descanso nos bancos, chefes, pausas, HUD e controles de toque.

## Verificações
- Verificação TypeScript isolada dos módulos do motor e renderização: passou.
- Desenho de 18 estados do protagonista, 81 combinações de inimigo/estado, três interiores de ônibus: passou na renderização isolada.
- Cena inicial: imagens e componentes originais preservados por comparação byte a byte.
- **Ainda é necessário executar o jogo completo no navegador.** O ambiente de verificação não contém as dependências instaladas para `vite build` e o teste isolado não comprova FPS, controles reais ou ausência de bugs de integração.

## Limitação artística
Isto aproxima o gameplay do acabamento 16-bit sem substituir a identidade original. Não cria spritesheets ilustrados manualmente e não alcança automaticamente o nível de detalhe da arte conceitual anterior. A vantagem é manter os desenhos existentes, as animações e a mecânica original, com risco bem menor de mudanças indesejadas.
