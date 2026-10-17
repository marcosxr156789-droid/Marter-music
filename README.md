# Master Music — projeto Android

Aplicativo local/offline em Java com tema preto e roxo. Recursos desta primeira versão:
- Lista arquivos de áudio que o Android disponibiliza pela biblioteca de mídia.
- Reproduzir, pausar, faixa anterior/próxima e barra de progresso.
- Tenta mostrar a capa do álbum fornecida pela biblioteca de mídia.
- Equalizador nativo Android com controles de graves, médios e agudos (o suporte depende do aparelho/saída de áudio).
- Campo para colar e salvar letras manualmente por faixa, localmente no aparelho.

## Requisitos
- Android Studio recente.
- Android SDK Platform 35 instalado pelo SDK Manager.
- JDK 17 (normalmente incluído no Android Studio).
- Internet apenas para baixar dependências e ferramentas de compilação; o app em si não precisa de internet para tocar música.

## Abrir e compilar
1. Extraia o ZIP.
2. Abra o Android Studio → **Open** → selecione a pasta `MasterMusic` extraída.
3. Aguarde o Gradle Sync. Se pedir para instalar Android SDK Platform 35 ou Build Tools, aceite.
4. Para testar, ative Opções do desenvolvedor e Depuração USB no Galaxy A07, conecte ao computador e selecione o telefone no Android Studio.
5. Pressione **Run ▶**.
6. Para gerar APK: **Build → Build Bundle(s) / APK(s) → Build APK(s)**. O Android Studio mostrará o caminho do APK ao terminar.
7. Copie o APK para o celular e abra-o. Se solicitado, permita “Instalar apps desconhecidos” para o aplicativo usado para abrir o arquivo.

## Observações e limitações
- Esta é uma primeira versão de código-fonte; não foi compilada/testada neste ambiente.
- A lista inclui apenas áudio que o Android indexou na biblioteca de mídia. Copie arquivos MP3, M4A, OGG ou outros formatos suportados para o telefone e aguarde a indexação.
- Letras não são buscadas automaticamente na internet: cole letras que você tenha direito de usar e toque em “Salvar letra desta música”.
- A capa depende de metadados/capa de álbum que o Android consiga fornecer.
- O equalizador usa o efeito de áudio nativo. Alguns dispositivos, Bluetooth, players ou versões do Android podem ignorar ou limitar o efeito.
- Esta versão mantém reprodução enquanto a tela do app está aberta; não implementa serviço de reprodução em segundo plano/notificação nem persistência de playlists personalizadas. A lista de músicas é a biblioteca local.
- Se o Android Studio indicar incompatibilidade de Gradle/SDK, use JDK 17 e instale o SDK Platform 35. Não altere `compileSdk` para uma versão que não esteja instalada.

## Gerar APK pela nuvem usando apenas o celular (GitHub)
Este projeto inclui `.github/workflows/build-apk.yml` para compilar um APK de depuração no GitHub Actions.
1. No navegador do celular, entre no GitHub e crie um repositório novo.
2. Envie os arquivos e pastas deste projeto para o repositório (incluindo a pasta oculta `.github/workflows`).
3. Abra a aba **Actions**, selecione **Build Master Music APK** e toque em **Run workflow** se a execução não iniciar automaticamente.
4. Quando a execução terminar com sucesso, abra a execução e baixe o artefato **Master-Music-debug-apk**. Ele é um ZIP que contém `app-debug.apk`.
5. Extraia esse ZIP e instale `app-debug.apk` no Android. Pode ser necessário permitir instalação de apps desconhecidos para o navegador/gerenciador de arquivos.
O APK gerado é de depuração, não assinado para distribuição na Play Store. A compilação depende de a configuração do projeto continuar compatível com as ferramentas do GitHub Actions.
