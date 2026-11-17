# Horário de Pico — Arcade com Charme (v2)

## O que foi entregue
Uma evolução **incremental** da versão retrô que mantinha as artes originais. A versão mantém a identidade de estagiário, gravata, mochila, acessórios, inimigos e ônibus, com apresentação visual um pouco mais próxima dos beat’em ups 16-bit. **Não é uma conversão completa para spritesheets ilustrados.**

### Código alterado
- `src/game/vectorArt.ts`: progressão de poses dos socos/chutes, reação ao dano, pequenas sombras/dobras, leve profundidade no piso e postura visual dos inimigos.
- `src/game/heritageSprites.ts`: escala de apresentação dos personagens +13% (herói), +11% (inimigos); amostragem visual melhor de golpes e pequeno sombreamento duro.
- `src/game/engine.ts`: rastros discretos nas partículas existentes. Cálculos de dano, colisões, posições, IA, pontuação e progressão não mudaram.
- `src/components/GameHUD.tsx`: retrato pixelado do estagiário em SVG, incorporado diretamente ao código.
- `src/index.css`: retoques de contraste e acabamento arcade no HUD; redução de movimento respeitada.

### O que ficou intacto
- Todas as **18 imagens das cinemáticas em `src/assets/images/`** (mesmos hashes SHA-256).
- Os **10 recursos de `public/assets/`** (mesmos hashes).
- `IntroStoryboard.tsx`, `introFrames.ts`, `GameModals.tsx`, `TitleScreen.tsx`.
- Firebase, autenticação, regras, ranking e rotas do servidor (nenhuma alteração).
- Lógica de combate e progressão (nenhuma alteração, somente desenho na engine).

## Importar no Google AI Studio
1. **Duplique** o projeto que já funciona, antes de substituir qualquer arquivo.
2. Se o editor permitir importar ZIP/projeto, use `horario_de_pico_arcade_com_charme_v2_completo.zip`.
3. Se não houver importação de ZIP, extraia o ZIP completo e importe os arquivos mantendo a mesma estrutura de pastas — ou use a opção de importar um repositório Git, se disponível no seu ambiente.
4. **Se já tem o projeto aberto**, use `horario_de_pico_arcade_com_charme_v2_so_alteracoes.zip` e sobrescreva somente os cinco caminhos listados acima. Não carregue esse ZIP parcial como se fosse um projeto completo.
5. Preserve suas próprias variáveis de ambiente e credenciais: o ZIP contém apenas `.env.example`, não seu `.env`.
6. Abra a prévia e teste o gameplay. Não é necessário atualizar as artes de abertura.

## Importar no Bolt
1. A opção mais confiável é criar um repositório GitHub com os arquivos extraídos do ZIP **completo** (no diretório raiz do repositório) e então importar esse repositório no Bolt.
2. Se sua interface tiver importação de arquivos/ZIP, o arquivo completo também pode ser usado diretamente.
3. Caso já tenha importado a versão anterior no Bolt, substitua somente os arquivos do ZIP parcial, mantendo o restante da estrutura.
4. Configure suas variáveis de ambiente no ambiente do Bolt quando necessário; não publique chaves de API no repositório.

## Comandos e testes
No projeto completo, com Node.js/npm disponíveis:

```bash
npm install
npm run lint
npm run build
npm run dev
```

Se o seu projeto estiver servindo o app por `server.ts`, `npm run dev` executa esse servidor Express/Vite. As chamadas externas (Gemini, Firebase, música) dependem de configuração própria do ambiente.

### Validações realizadas neste pacote
- TypeScript dos módulos de jogo alterados (`engine.ts`, `heritageSprites.ts`, `vectorArt.ts`): passou.
- Transpilação sintática de `GameHUD.tsx` e `App.tsx`: passou.
- Teste isolado de renderização: 18 estados do protagonista (108 amostras), 81 combinações de inimigos/estados e 6 cenários: passou.
- **Ainda não foi feito build completo nem teste de gameplay no navegador** porque o projeto original não acompanhava as dependências `node_modules`.

### Como reverter
Restaurar os cinco arquivos correspondentes do ZIP anterior `horario_de_pico_retro_com_charme_completo.zip`. Os recursos das cenas iniciais já estão intocados.
