# Horário de Pico — visual arcade 16-bit (v3)

## Objetivo e limites
Esta versão aproxima **o gameplay** da referência de ônibus noturno em pixel art, mantendo a identidade do estagiário, seus acessórios, os inimigos característicos, as mecânicas e as cenas originais. É uma versão funcional de desenhos procedurais em pixels, **não** uma reprodução literal do conceito ilustrado nem um pacote profissional de spritesheets.

## Arquivos realmente modificados ou criados
- `src/game/arcadeActors.ts` (novo): sprites pixelados próprios para protagonista e todos os tipos de inimigos, poses para ataque, caminhada, dano, guard, mochila, etc.
- `src/game/arcadeDepth.ts` (novo): cidade ao fundo, janelas iluminadas, passageiros não interativos, textura de piso e encostos em primeiro plano.
- `src/game/visualSettings.ts` (novo): `USE_NEW_ARCADE_ACTORS = true` por padrão. Altere para `false` para retornar aos personagens anteriores sem mexer em combate. **O cenário continuará com o acabamento v3.**
- `src/game/engine.ts`: alterna o renderizador de personagens. Nada alterado nas regras de combate, danos, colisões ou pontuação.
- `src/game/vectorArt.ts`: complementa o ônibus original com camadas de detalhe 16-bit, sem remover catraca, validador, bancos ou saída.
- `src/game/levels.ts`: ajusta o céu da Linha 101 para fim de tarde e o da Linha 202 para pôr do sol. A Linha 303 continua noturna. Todas as posições, fases, inimigos e ondas permanecem intactas.

## Artes de introdução preservadas
Todos os **18 JPG** em `src/assets/images/` e os **10 arquivos em `public/assets/`** foram comparados por SHA-256 com a versão anterior: nenhum foi modificado. `IntroStoryboard.tsx`, `introFrames.ts`, `TitleScreen.tsx` e `GameModals.tsx` continuam intactos.

## Importar no Google AI Studio
1. Duplique seu projeto para evitar perda do trabalho atual.
2. Extraia o ZIP `horario_de_pico_referencia_16bit_v3_alteracoes.zip`.
3. Copie os seis arquivos para os caminhos correspondentes dentro do projeto. Os três arquivos novos são **obrigatórios**.
4. Execute e teste as linhas 101, 202 e 303, com socos, chutes, bag guard, especiais, itens, catraca, validador, bancos, chefes, ranking e cenas iniciais.
5. Não apague variáveis de ambiente ou configurações Firebase já existentes.

## Importar no Bolt
1. Extraia o projeto completo e publique os arquivos em um repositório GitHub privado.
2. No Bolt, importe o projeto a partir do repositório GitHub.
3. Configure as variáveis de ambiente exigidas pelo seu projeto, sem colocar segredos no código público.
4. Execute os comandos de instalação e build da aplicação (`npm install` e `npm run build`, conforme suporte do ambiente).

## Verificações realizadas
- `tsc --noEmit` passou para os módulos visuais (`arcadeActors.ts`, `arcadeDepth.ts`, `vectorArt.ts`, `heritageSprites.ts`, `levels.ts`, `types.ts`, `seats.ts`, `visualSettings.ts`).
- Teste de desenho isolado no Canvas: 108 amostras de herói, 81 estados/combinações de inimigo e 6 cenas de ônibus sem erros de execução.
- Comparação SHA-256 de 28 recursos estáticos: todos preservados.

## Limitações
O teste completo em navegador, o build Vite completo e a validação de FPS ainda precisam ser feitos no Google AI Studio/Bolt, pois as dependências do projeto não estão instaladas nesta sessão. A prévia PNG é renderizada isoladamente pelo código do Canvas, com um cabeçalho de HUD ilustrativo; não é captura de gameplay rodando no navegador.
