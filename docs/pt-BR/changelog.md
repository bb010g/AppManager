---
sidebar: auto
---

# Histórico de Atualizações

![Versão de Depuração](https://github.com/MuntashirAkon/AppManager/workflows/Debug%20Build/badge.svg) [![Lançamento no GitHub](https://img.shields.io/github/v/release/MuntashirAkon/AppManager)](https://github.com/MuntashirAkon/AppManager/releases/latest) [![F-Droid](https://img.shields.io/f-droid/v/io.github.muntashirakon.AppManager)](https://f-droid.org/packages/io.github.muntashirakon.AppManager) ![Tamanho do Repo no GitHub](https://img.shields.io/github/repo-size/MuntashirAkon/AppManager) ![Commit por Semana no GitHub](https://img.shields.io/github/commit-activity/w/MuntashirAkon/AppManager)

Currently supported versions are [v2.5.20](#v2-5-20-375), [v2.5.19](https://github.com/MuntashirAkon/AppManager/releases/tag/pre-v2.5.19), [v2.5.18](https://github.com/MuntashirAkon/AppManager/releases/tag/pre-v2.5.18) and [v2.5.17](#v2-5-17-368). Por favor, atualize o App Manager se você estiver usando uma versão mais antiga do que estas.

::: details Tabela de Conteúdos
[[toc]]
:::

## v2.5.20 (375)
### Introducing Profiles
[Profiles][profile_page] finally closes the [related issue](https://github.com/MuntashirAkon/AppManager/issues/72). Profiles can be used to execute certain tasks repeatedly without doing everything manually. A profile can be applied (or invoked) either from the [Profiles page][profiles_page] or from the home screen by creating shortcuts. There are also some presets which consist of debloating profiles taken from [Universal Android Debloater](https://gitlab.com/W1nst0n/universal-android-debloater).

**Known limitations:**
- Exporting rules and applying permissions are not currently working.
- Profiles are applied for all users.

### The Interceptor
[Intent Intercept](https://github.com/MuntashirAkon/intent-intercept) works as a man-in-the-middle between source and destination, that is, when you open a file or URL with another app, you can see what is being shared by opening it with Interceptor first. You can also add or modify the intents before sending them to the destination. Additionally, you can double click on any exportable activities in the Activities tab in the App Details page to open them in the Interceptor to add more configurations.

**Known limitation:** Editing extras is not currently possible.

### UnAPKM: DeDRM the APKM files
When I released a small tool called [UnAPKM](https://f-droid.org/en/packages/io.github.muntashirakon.unapkm), I promised that similar feature will be available in App Manager. I am proud to announce that you can open APKM files directly in the App Info page or convert them to APKS or install them directly.

### Multiple user
App manager now supports multiple users! For now, this requires root or ADB. But no-root support is also being considered. If you have multiple users enabled and click on an app installed in multiple profiles, an alert prompt will be displayed where you can select the user.

### Vive la France!
Thanks to the contributors, we have one more addition to the language club: French. You can add more languages or improve existing translations at [Weblate](https://hosted.weblate.org/engage/app-manager).

### Report crashes
If App Manager crashes, you can now easily report the crash from the notifications which opens the share options. Crashes are not reported by App Manager, it only redirects you to your favourite Email client.

### Android 11
Added support for Android 11. Not everything may work as expected though.

### App Installer Improvements
#### Set installation locations
In settings page, you can set install locations such as auto (default), internal only and prefer external.
#### Set APK installer
In settings page, you can also set default APK installer (root/ADB only) instead of App Manager.
#### Multiple users
In settings page, you can allow App Manager to display multiple users during APK installation.
#### Signing APK files
In settings page, you can choose to sign APK files before installing them. You can also select which signature scheme to use in the _APK signing_ option in settings.

**Known limitation:** Currently, only a generic key is used to sign APK files

## v2.5.17 (368)
### App Installer
As promised, it is now possible to select splits. AM also provides recommendations based on device configurations. If the app is already installed, recommendations are provided based on the installed app. It is also possible to downgrade to a lower version without data loss if the device has root or ADB. But it should be noted that not all app can be downgraded. Installer is also improved to speed up the install process, especially, for root users. If the app has already been installed and the new (x)apk(s) is newer or older or the same version with a different signature, AM will display a list of changes similar to [what's new][whats_new] before prompting the user to install the app. This is useful if the app has introduced tracker components, new permissions, etc.

**Known Limitations:**
- Large app can take a long time to fetch app info and therefore it may take a long time display the install prompt.
- If the apk is not located in the internal storage, the app has to be cached first which might also take a long time depending on the size of the apk.

### Scanner: Replacement for Exodus Page
exodus page is now replaced with scanner page. [Scanner page][scanner] contains not only a list of trackers but also a list of used libraries. This is just a start. In future, this page will contain more in depth analysis of the app.

### Introducing System Config
System Config lists various system configurations and whitelists/blacklists included in Android by either OEM/vendor, AOSP or even some Magisk modules. Root users can access this option from the overflow menu in the main page. There isn't any official documentation for these options therefore it's difficult to write a complete documentation for this page. But I will gradually add documentations using my own knowledge. But some of the functions should be understandable by their name.

### More Languages
Thanks to the contributors, AM now has more than 12 languages. New languages include Bengali, Hindi, Norwegian, Polish, Russian, Simplified Chinese, Turkish and Ukrainian. You can add more languages or improve existing translations at [Weblate](https://hosted.weblate.org/engage/app-manager).

### App Info Tab
More tags are added in the [app info tab][app_info] such as **KeyStore** (apps with KeyStore items), **Systemless app** (apps installed via Magisk), **Running** (apps that are running). For external apk, two more options are added namely **Reinstall** and **Downgrade**. Now it is possible to share an apk via Bluetooth. For system apps, it is possible to uninstall updates for root/ADB users. But like the similar option in the system settings, this operation will clear all app data. As stated above, exodus has been replaced with scanner.

### Navigation Improvements
It's now relatively easy to navigate to various UI components just by using keyboard. You can use up/down button to navigate between list items and tab button to navigate to UI components inside an item.

### Running Apps Page
It is now possible to sort and filter processes in this tab. Also the three big buttons are replaced with an easy to use three dot menu. Previously the memory usage was wrong which is fixed in this version.

### Built-in Toybox
Toybox (an alternative to busybox) is bundled with AM. Although Android has this utility built-in from API 23, toybox is bundled in order to prevent buggy implementations and to support API < 23.

### Component Blocker Improvements
Component blocker seemed to be problematic in the previous version, especially when global component blocking is enabled. The issues are mostly fixed now.

::: warning Caution
The component blocking mechanism is no longer compatible with v2.5.6 due to various security issues. If you have this version, upgrade to v2.5.13 or earlier versions first. After that enable [global component blocking][5] and disable it again.
:::

### Improvements in the App Details Page
Value of various app ops depend on their parent app ops. Therefore, when you allow/deny an app op, the parent of the app op gets modified. This fixes the issues some users have been complaining regarding some app ops that couldn't be changed.

If an app has the target API 23 or less, its permissions cannot be modified using the `pm grant ...` command. Therefore, for such apps, option to toggle permission has been disabled.

The signature tab is improved to support localization. It also displays multiple checksums for a signature.

### App Manifest
Manifest no longer crashes if the size of the manifest is too long. Generated manifest are now more accurate than before.


## v2.5.13 (348)
### Aplicativo Empacotado (APK Dividido)
Formatos de aplicativos empacotados como **apks** e **xapk** agora são suportados. Você pode instalar esses aplicativos usando os botões de instalação regulares. Para usuários com root e adb, os aplicativos são instalados usando shell e, para usuários sem root, o método padrão da plataforma é usado.

**Limitações Conhecidas:**
- Atualmente _todos_ os apks divididos são instalados. Mas esse comportamento vai mudar no próximo lançamento. Se você precisar apenas de algumas divisões em vez de todas, extraia o arquivo **apks** ou **xapk** e então crie um novo arquivo zip com seus apks divididos desejados e substitua a extensão **zip** por **apks**. Agora, abra com o AM.
- Não há um diálogo de progresso para exibir o progresso da instalação.

### Suporte para Instalação Direta
Agora você pode instalar **apk**, **apks** ou **xapk** diretamente do seu navegador ou gerenciador de arquivos favorito. Para aplicativos que precisam de atualizações, um diálogo de **O Que Há de Novo** é exibido mostrando as mudanças na nova versão.

**Limitações Conhecidas:**
- Downgrade ainda não é possível.
- Não há um diálogo de progresso para exibir o progresso da instalação. Se você não puder interagir com a página atual, aguarde até que a instalação esteja concluída.

### Remover Todas as Regras de Bloqueio
Na página de Configurações, uma nova opção que pode ser usada para remover todas as regras de bloqueio configuradas no App Manager foi adicionada.

### Operações de Aplicativos
- Operações de Aplicativos agora são geradas usando uma técnica semelhante ao AppOpsX. Isso deve diminuir significativamente o tempo de carregamento na aba de Operações de Aplicativo.
- Na aba de Operações de Aplicativo, um item no menu que pode ser usado para listar apenas operações de aplicativo ativas sem incluir as operações de aplicativo padrão foi adicionado. Essas preferências são salvas nas preferências compartilhadas.

**Limitações Conhecidas:** Muitas vezes, a aba de Operações de Aplicativo pode não ser responsiva. Se esse for o caso, reinicie o AM.

### Suporte ao ADB Melhorado
Os comandos de ADB shell agora são executados usando uma técnica semelhante ao AppOpsX (Esta é uma alternativa _grátis_ ao Shizuku.). Isso deve melhorar drasticamente o tempo de execução.

**Limitações Conhecidas:** Muitas vezes, a aba de Operações de Aplicativo pode não ser responsiva. Se esse for o caso, reinicie o AM.

### Filtragem na Página Principal
Adicionada uma opção para filtrar aplicativos que tem pelo menos uma atividade.

### Backup/Compartilhamento de APK
Os arquivos apk agora são salvos como `nome do aplicativo_versão.extensão` em vez de `pacote.nome.extensão`.

### Operações em Lote
- Adicionado um serviço em primeiro plano para executar operações em lote. O resultado da operação é exibido em uma notificação. Se uma operação falhar para alguns pacotes, clicar na notificação abrirá uma caixa de diálogo listando os pacotes que falharam. Há também um botão de **Tentar Novamente** na parte inferior que pode ser usada para executar a operação novamente para os pacotes que falharam.
- Substituído o Linux _Encerrar_ por **forçar parada**.

### Traduções
Adicionado traduções para Alemão e Português (Brasileiro).

**Limitações Conhecidas:** Nem todas as traduções foram verificadas ainda.

### Backup de Dados de Aplicativos
Instalar o aplicativo apenas para o usuário atual no momento da restauração de backups. O suporte para apks divididos também foi adicionado.

A função de backup de dados agora é considerada instável. _Se encontrar algum problema, por favor me informe sem hesitação._

## v2.5.12 (341)
- <span><TagFeature/></span> Adicionado o suporte para a divisão de backups de dados em arquivos de 1GB para contornar a limitação do sistema de arquivos FAT32
- <span><TagFeature/></span> Adicionado a capacidade de desbloquear rastreadores
- <span><TagFeature/></span> Adicionada uma opção para pular verificações de assinatura enquanto restaura backups
- <span><TagFeature/></span> Suporte ao [Termux][termux]: Executar como aplicativo depurável ou executar nova sessão como aplicativo na [Aba de Informações do Aplicativo][app_info]
- <span><TagFeature/></span> Exibir informações de backup do aplicativo na [Página principal][main_page]
- <span><TagFeature/></span> Restaurar arquivos de origem (exceto arquivos apk) desativados em arquitetura não suportada
- <span><TagFeature/></span> Exibir o diálogo de confirmação antes de limpar os dados do aplicativo
- <span><TagFeature/></span> Capacidade de importar componentes desativados usando IFW no MAT
- <span><TagFeature/></span> Inclua mídia externa e diretório obb para backups
- <span><TagFeature/></span> Permitir a importação de regras existentes por outros aplicativos ou ferramentas
- <span><TagFeature/></span> Adicionada uma opção para extrair ícone de aplicativo na [Aba de Informações do Aplicativo][app_info]
- <span><TagFix/></span> Exibir restauração e excluir backups apenas para aplicativos com backup
- <span><TagFix/></span> Exibir indicador de progresso ao fazer backups
- <span><TagFix/></span> Exibir indicador de progresso ao carregar operações de aplicativo
- <span><TagFix/></span> Corrigido aplicativo não abrir no mais recente e único suportado Aurora Droid (v1.0.6)
- <span><TagFix/></span> Corrigido crash ao mudar para o modo noturno enquanto navega pela [Página de Detalhes do Aplicativo][1]
- <span><TagFix/></span> Corrigido um crash ao tentar abrir um arquivo apk externo
- <span><TagFix/></span> Corrigido o NullPointerException quando um diretório de dados externo é nulo
- <span><TagFix/></span> Corrigida a barra de ferramentas no diálogo em tela cheia
- <span><TagFix/></span> Corrigido a busca insensível de caso
- <span><TagFix/></span> Tema do aplicativo otimizado
- <span><TagFix/></span> Substituído AndroidShell pelo LibSuperuser
- <span><TagFix/></span> Solicite permissão de armazenamento externo ao salvar arquivos apk
- <span><TagFix/></span> Solução alternativa para o bug appBarLayout em Material Design
- <span><TagFix/></span> Atualize informações externas do Apk sobre eventos de instalação/desinstalação

Para usar as funções do Termux, certifique-se de que você está usando o Termux v0.96 ou posterior e `allow-external-apps=true` foi adicionado em <tt>~/.termux/termux.properties</tt>.

A função de backup de dados ainda é considerada experimental e, por favor, não confie nela para gerenciar seus backups ainda.

## v2.5.11 (333)
- <span><TagFeature/></span> Adicionado suporte experimental para backup de dados de aplicativos. Por favor, teste apenas em aplicativos que você não precisa. (apenas root)
- <span><TagFeature/></span> Adicionado compartilhamento de arquivos apk divididos como apks (pode ser instalado via [SAI][8]).
- <span><TagFeature/></span> Implementado o salvamento de arquivos apk no modo de seleção em lote.
- <span><TagFeature/></span> Adicionado novidades para o arquivo apk que precisa de uma atualização (ao abrir arquivos apk externos).
- <span><TagFeature/></span> Adicionada uma opção para aplicar operações em 1 clique em aplicativos do sistema (desativado por padrão).
- <span><TagFeature/></span> Adicionadas informações da versão do aplicativo instalada na aba de Informações do Aplicativo. Clicar no ícone _i_ abre a aba [Informações do Aplicativo][app_info] do instalado.
- <span><TagFeature/></span> Novas permissões solicitadas <tt>READ_EXTERNAL_STORAGE</tt> e <tt>WRITE_EXTERNAL_STORAGE</tt> para suporte ao backup de aplicativos
- <span><TagFeature/></span> Exibir aplicativos que são desinstalados, mas têm backups na página principal
- <span><TagFeature/></span> Adicionado um disclaimer
- <span><TagFix/></span> Corrigida as seleções não sendo limpas após a tarefa ser concluída na página principal
- <span><TagFix/></span> Convertida várias informações nas configurações e a aba de funções para o texto para melhorar a legibilidade
- <span><TagFix/></span> Corrigido um crash na [Página principal][main_page] enquanto filtra aplicativos por consulta de busca
- <span><TagFix/></span> Corrigido um crash na aba de [Informações do Aplicativo][app_info] quando a existência do diretório de dados externos tem resultado falso-positivo

**Obs:** Os dados de backup são armazenados em <tt>/sdcard/AppManager</tt> e backups de apk são armazenados em <tt>/sdcard/AppManager/apks</tt>. Backups de dados não estão funcionando no Android Lollipop.

## v2.5.10 (324)
- <span><TagFeature/></span> Adicionadas operações em 1 clique (como [Operações em 1 Clique](./guide/one-click-ops-page.md) na seção de menu na [Página principal][main_page]): bloquear (anúncios e) rastreadores, bloqueio de componentes por assinaturas, bloqueio de operações de aplicativo
- <span><TagFeature/></span> Adicionado o suporte para apk externo: Agora você pode abrir arquivos apk do seu gerenciador de arquivos. Você pode visualizar detalhes do aplicativo, manifest ou scanear rastreadores diretamente de lá
- <span><TagFeature/></span> Adicionada opção de filtragem de aplicativos persistentes na [Página principal][main_page]
- <span><TagFeature/></span> Visualizador de manifest alternativo para apks instalados
- <span><TagFeature/></span> Exibir número de rastreadores como uma tag na aba [Informações do Aplicativo][app_info]
- <span><TagFeature/></span> Adicionada uma opção selecionar tudo na barra inferior na [Página principal][main_page] no modo de seleção
- <span><TagFeature/></span> Adicionado links ao código fonte e à comunidade
- <span><TagFeature/></span> Adicionado suporte para instalação/atualização de arquivos apk na aba [Informações do Aplicativo][app_info] (incompleto)
- <span><TagFeature/></span> Adicionada uma opção para importar componentes desativados existentes nas configurações de importação/exportação (incompleto)
- <span><TagFeature/></span> Informações de apk divididos adicionadas na aba [Informações do Aplicativo][app_info]
- <span><TagFeature/></span> Adicionada uma opção para abrir o [Termux](./guide/main-page.md#termux) na [Página principal][main_page] (incompleto)
- <span><TagFeature/></span> Suporte inicial para banner de aplicativo
- <span><TagFix/></span> Corrigida uma inconsistência de ativar e desativar na aba de Informações do Aplicativo
- <span><TagFix/></span> Corrigido um problema com cache de aplicativo persistente
- <span><TagFix/></span> Corrigido o problema de rolagem na página de configurações
- <span><TagFix/></span> Corrigido os crashes ao mudar para as abas de componentes para usuários sem root
- <span><TagFix/></span> Corrigido o crash ao tentar visualizar o resumo enquanto o scaneamento ainda está em andamento na página do exodus
- <span><TagFix/></span> Corrigido os crashes em dispositivos que não suportam o uso de dados
- <span><TagFix/></span> Corrigido o crash ao tentar ver o manifest de um apk dividido
- <span><TagFix/></span> Corrigido o nome de instalador de pacote errado na aba de [Informações do Aplicativo][app_info]
- <span><TagFix/></span> Corrigido a formatação do histórico de atualizações para dispositivos antigos

## v2.5.9 (315)
- <span><TagFeature/></span> Mescladas as [Informações do Aplicativo][app_info] como uma única aba em [Detalhes do Aplicativo][1]
- <span><TagFeature/></span> Opção adicionada para redefinir todas as operações de aplicativo
- <span><TagFeature/></span> Opção adicionada para revogar todas as operações/permissões de aplicativo perigosas
- <span><TagFeature/></span> Destaque os rastreadores nas abas de componentes
- <span><TagFeature/></span> Opção adicionada para salvar o manifest e o despejo de classe
- <span><TagFeature/></span> Adicionado a capacidade de conceder/revogar permissões de desenvolvimento
- <span><TagFeature/></span> Adicionadas opções de ordenação para as abas de componentes, operações de aplicativo e permissões utilizadas
- <span><TagFeature/></span> Adicionada a ordenação pelo uso de wi-fi na página de [Uso de Aplicativos][6]
- <span><TagFeature/></span> Botão de início adicionado na aba de [Informações do Aplicativo][app_info]
- <span><TagFeature/></span> Adicionada a opção nunca peça para usar o status prompt
- <span><TagFeature/></span> Adicionado clique longo para selecionar aplicativos na [Página principal][main_page]
- <span><TagFeature/></span> Histórico de atualizações adicionado dentro do aplicativo
- <span><TagFix/></span> Clique para selecionar aplicativos durante o modo de seleção
- <span><TagFix/></span> Bloqueador de componentes melhorado
- <span><TagFix/></span> Carregamento de manifest melhorado para aplicativos grandes
- <span><TagFix/></span> Desempenho do carregamento de abas melhorado
- <span><TagFix/></span> Corrigida a verificação das operações de aplicativo e operações de aplicativos personalizadas para alguns dispositivos
- <span><TagFix/></span> Desativada a abertura de atividades para atividades desativadas
- <span><TagFix/></span> Obtenha nome de atividade real para atividades que usam alias de atividade
- <span><TagFix/></span> Cores de fundo corrigidas
- <span><TagFix/></span> Corrigido o crash ao carregar a aba de serviços para usuários sem root
- <span><TagFix/></span> Corrigido o botão de voltar para o visualizador de classe que não estava funcionando
- <span><TagFix/></span> Mudada a cor do ícone de bloqueio para a cor de destaque
- <span><TagFix/></span> Tradução removida até que o aplicativo esteja completo
- <span><TagFix/></span> Links na seção de crédito agora são clicáveis
- <span><TagFix/></span> Corrigidos vários vazamentos de memória

## v2.5.8 (289)
- <span><TagFeature/></span> Adicionado [recursos de importação/exportação para regras de bloqueio](./guide/settings-page.md#importar-exportar-regras-de-bloqueio)
- <span><TagFeature/></span> Adicionada a opção para [selecionar temas](./guide/settings-page.html#tema-do-aplicativo) (noite/dia)
- <span><TagFeature/></span> Adicionados modo, duração, tempo de aceitação, tempo de rejeição para operações de aplicativo
- <span><TagFeature/></span> Destacar serviços em execução
- <span><TagFeature/></span> Destacar componentes desativados não desativados no App Manager
- <span><TagFeature/></span> Adicionado puxar para atualizar na aba de [Uso de Aplicativos][6]
- <span><TagFeature/></span> Porcentagem de tempo de tela adicionada com indicador
- <span><TagFeature/></span> Separadas as páginas de instruções e sobre com diálogo em tela cheia para ambos
- <span><TagFeature/></span> Menu flutuante arredondado (ainda incompleto)
- <span><TagFix/></span> Corrigidos vários problemas de operações de aplicativo específicas de dispositivos/SDK
- <span><TagFix/></span> Melhorias de estabilidade de todos os aplicativos
- <span><TagFix/></span> Adicionada a permissão <tt>ACCESS_NETWORK_STATE</tt> para suportar sistemas operacionais mais antigos
- <span><TagFix/></span> Corrigido a exclusão de todas as regras IFW ao selecionar o [Bloqueio Global de Componentes][5]
- <span><TagFix/></span> Corrigido vários problemas de busca

## v2.5.7 (265)
- <span><TagFeature/></span> Suporte inicial para [ADB sobre TCP](./guide/adb-over-tcp.md) (port 5555) para usuários sem root
- <span><TagFix/></span> Corrigida a importação de regras do [Watt][2] e [Blocker][3]
- <span><TagFix/></span> Mostrar Aurora Droid na página de [Informações do Aplicativo][app_info] como prioridade sobre F-Droid
- <span><TagFix/></span> Desempenho melhorado para bloqueio de componentes
- <span><TagFix/></span> Corrigido o problema de detecção do modo de operação de aplicativo

**Para usuários com root:** Se você pulou a [v2.5.6](#v2-5-6-233), você pode precisar aplicar todas as regras globalmente, aplicando o [Bloqueio Global de Componentes][5] nas Configurações para que elas funcionem.

## v2.5.6 (233)
- <span><TagFeature/></span> [Operações em lote](./guide/main-page.md#operacoes-em-lote) na página principal: limpar dados do aplicativo, desativar a execução em segundo plano, desativar/encerrar/desinstalar aplicativos (clique no ícone do aplicativo para selecionar)
- <span><TagFeature/></span> Suporte total aos arquivos exportados do [Blocker][3] que foi quebrado devido a um bug no Blocker
- <span><TagFeature/></span> Reimplementação do bloqueio de atividades, receptores, serviços e provedores
- <span><TagFix/></span> Removida a dependência ConstraintLayout portanto, uma potencial diminuição no tamanho do aplicativo
- <span><TagFix/></span> Corrigido o aviso de uso do aplicativo duplicado na página de [Informações do Aplicativo][app_info]
- <span><TagFix/></span> Corrigido o crash quando um ícone de aplicativo não é encontrado na página de [Detalhes do Aplicativo][1]

**Nota para usuários com root:** A fim de garantir que as regras de bloqueio anteriores sejam preservadas com a nova implementação de bloqueio, esta atualização lê-se das regras anteriores, consequentemente, aumentando o tempo de carregamento na [Página principal][main_page]. Esta função será removida na próxima versão, mas ainda pode ser simulada pela aplicação do [bloqueio global de componentes][5] nas Configurações.

## v2.5.5 (215)
- <span><TagFeature/></span> Adicionado [Visualizador de Aplicativos/Processos em Execução](./guide/main-page.md#aplicativos-em-execucao) (requer root)
- <span><TagFeature/></span> Adicionado [Visualizador de Detalhes de Uso][6]
- <span><TagFeature/></span> Adicionado [Atualizador de Apk](./guide/main-page.md#apk-updater) e suporte à [Aurora Store](./guide/app-details-page.md#painel-de-acao-horizontal)
- <span><TagFeature/></span> Salvar valores modificados de operações de aplicativo e permissões no disco (em progresso)
- <span><TagFix/></span> Suporte para desinstalação para usuários sem root
- <span><TagFix/></span> Reestruturação do uso do aplicativo
- <span><TagFix/></span> Adicionado mais clareza, bem como melhor desempenho na página de [Detalhes do Aplicativo][1]


[profile_page]: ./guide/profile-page.md
[1]: ./guide/app-details-page.md
[profiles_page]: ./guide/profiles-page.md
[2]: https://github.com/tuyafeng/Watt
[scanner]: ./guide/scanner-page.md
[3]: https://github.com/lihenggui/blocker
[whats_new]: ./guide/app-details-page.md#horizontal-action-panel
[app_info]: ./guide/app-details-page.md#aba-de-informacoes-do-aplicativo
[5]: ./guide/settings-page.md#bloqueio-global-de-componentes
[6]: ./guide/main-page.md#uso-de-aplicativos
[main_page]: ./guide/main-page.md
[8]: https://github.com/Aefyr/SAI
[termux]: https://github.com/termux/termux-app
