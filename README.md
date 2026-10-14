# RADV Xclipse 550 PGO

Versão experimental **0.0.1** do driver Vulkan RADV para Samsung Xclipse 550, baseada no port radv-xclipse de JimVulkan e no Mesa.

O pacote usa PGO de CPU coletado em gameplay e substitui algumas operações de blit 2D RGBA/BGRA UNORM em escala1:1 por cópias exatas. Casos com escala, inversão, conversão, sRGB ou extensões mantêm o caminho filtrado. Não altera a resolução nem as correções de sincronização da base.

## Instalação

Baixe `radv-xclipse550-pgo-0.0.1.zip` em Releases e importe o ZIP no seletor de driver gráfico do Eden. Reinicie o jogo depois de trocar o driver. O formato do pacote declara Android API34 mínimo; a validação local foi feita no SM-A576B/Xclipse550. Outros aparelhos e emuladores não foram validados nesta versão.

## Testes e desempenho

Oito testes de transferência passaram. Os quatro UNORM preservam os bytes de entrada; os casos sRGB continuam no caminho filtrado e suas diferenças são registradas. BOTW carregou no Eden oficial e uma captura de45s em Docked1x/Normal registrou aproximadamente23,49 apresentações/s e P95≈49,97ms.

`validation.json` contém os resultados agregados.

## Código e proveniência

`source-overlay/` contém as fontes congeladas usadas pelo driver, com as alterações desta candidata. `patches/` contém a alteração incremental de blit. `profiles/gameplay.profdata` é o feedback deCPU do driver. Isso não é PGO automático de shaders. `PROVENANCE.json` registra hashes, origem e limites de reprodução; o overlay requer a árvore base, headers gerados e dependências do radv-xclipse.

O nome público é0.0.1. A biblioteca mantém os mesmos bytes e o identificador interno da build testada, para preservar a rastreabilidade.

## Créditos e licenças

JimVulkan pelo port radv-xclipse; autores do Mesa, RADV, ACO, NIR e demais componentes pelos projetos originais. Os copyrights e licenças originais são preservados em `LICENSE`, nos headers e em `NOTICE.txt`, também incluído noZIP. Este projeto não é uma distribuição oficial da Samsung, do Mesa, do Eden ou de JimVulkan.
