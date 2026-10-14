# Correção do rótulo de precisão

Em 14/10/2026, a revisão dos logs nativos confirmou que `gpu_accuracy=0` aparece como **Low** no APK do Eden usado nas capturas da 0.0.1. A documentação inicial chamou esse ajuste de Normal incorretamente.

A janela isolada de 23,4862 apresentações/s e o par 23,7588/23,4386 apresentações/s usaram Docked 1×/Low. Ambas as janelas do par tinham o mesmo APK, o mesmo valor numérico de precisão e as demais configurações verificadas. Os números medidos, as exclusões e a conclusão de ganho sustentado não comprovado permanecem os mesmos.

O APK identificado por SHA256 `f429745c16f851ff05cdb12635271a9abd6843c4959cda8d52441deeb89b4f4c` registra `Renderer.gpu_accuracy: Low` na inicialização de ambas as janelas. O rótulo foi corrigido no README, em `validation.json`, no gráfico e no texto da release. O coletor passa a registrar o nome observado nos logs em vez de presumir o nome pelo número.

Os três arquivos publicados originalmente na release conservam seus hashes. O ZIP de fontes contém o README e a validação do registro inicial, incluindo o rótulo incorreto; esta correção se aplica também àqueles documentos. A biblioteca do driver não foi recompilada ou alterada.
