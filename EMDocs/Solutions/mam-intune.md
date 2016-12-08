---
title: "Usando Políticas de Gerenciamento de Aplicativos Móveis keine Intune"
description: "Crie e Implante um Aplicativo keine Intune com Uma Política de Gerenciamento de Aplicativos Móveis."
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d7c4104-b85f-407e-8832-0e6bbac934f5
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 24e3953f0625da90dc42c68703ee2433429efbf8
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="usar-polticas-de-gerenciamento-de-aplicativos-mveis-no-intune"></a>Usar Políticas de Gerenciamento de Aplicativos Móveis keine Intune
Um Dos Motivos Principais Pelos Quais Muitas Empresas Usam o Microsoft Intune ä implantar Aplicativos Que os Usuários Precisam Absatz Realizar Seu Trabalho. Antes de implantar Aplicativos, Você Precisará [Tornar Seus Dispositivos Gerenciados](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)an.

Por Exemplo, Se Sua Empresa Usa o Microsoft Word Há Versões Disponíveis Absatz Windows, iOS und Android e Outros. O Desafio Que Você Como um Administrador de TI Enfrenta ä Gerenciar eine Variedade de Aplicativos Disponíveis, langen Muitas Plataformas Diferentes de Computador E de Dispositivo com-o Objetivo de Permitir Que os Usuários Façam Seu Trabalho E, Simultaneamente, Garantir eine Segurança Dos Seus Dados Corporativos.

SE Estiver Usando o Intune com-o Consulte [wie Steuerelement Apps mithilfe von Mobile Anwendung Informationsverwaltungsrichtlinien im Konfigurations-Manager](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396) -Konfigurations-Manager (Como controlar Aplicativos Usando Políticas de Gerenciamento de Aplicativos Móveis keine Konfigurations-Manager).

Als Políticas de MAM (Gerenciamento de Aplicativos Móveis) Dão Suporte a:
- Dispositivos Que Executam o Android 4 e hinteren.
- Dispositivos Que Executam o iOS 7 e hinteren.

> [!NOTE]
> Als Políticas de MAM Dão Suporte eine Dispositivos Registrados com-o Intune. Absatz Saber Mais Sobre Como Criar Políticas de Gerenciamento de Aplicativos Absatz Dispositivos Que Não São Gerenciados Pelo Intune, Veja [Proteger os Dados Aplicativo Usando Políticas de Gerenciamento de Aplicativos Móveis com-o Microsoft Intune führen](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).

Diferente de Outras Políticas Aktionen Intune Você Não Implanta Uma Política de MAM Diretamente aus. Dieser Abschnitt Vez Disso Você Associa eine Política Ao Aplicativo Que Deseja Restringir. Quando o Aplicativo ä Implantado E Instalado langen Dispositivos, als Configurações Especificadas Entrarão langen Blue Yonder.

Absatz Aplicar Restrições einer um Aplicativo, o Aplicativo Deve Incorporar o SDK (Software Development Kit) Aplicativo Microsoft Intune führen. Há Dois Métodos de Obter Esse Tipo de Aplicativo:

- 
            **Usar um Aplicativo Gerenciado Por Política** – Tem o SDK Interno Aplicativo führen. Absatz Adicionar Este Tipo de Aplicativo Especifique link um Absatz o Aplicativo de Uma Loja de Aplicativos, Como eine iTunes Store Ou, o Google wiedergeben. Nenhum Processamento Adicional ä Necessário Absatz Este Tipo de Aplicativo. Absatz-Ver ein Lista Completa de Aplicativos da Microsoft com Suporte, Vá Absatz ein Galeria de Aplicativos Móveis machen Microsoft Intune Na Página de [Parceiros de Aplicativos Microsoft Intune führen](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners). Clique keine Aplicativo Absatz Ver os Cenários e Plataformas com-Suporte e Se o Aplicativo Dá Suporte eine Várias Identidades Ou Não an.
- 
            **Usar um Aplicativo "Encapsulado"** – Aplicativos Que São Empacotados Novamente Absatz Incluir o SDK Aplicativo Usando führen Sie eine Ferramenta de Encapsulamento de Aplicativos Microsoft Intune. Normalmente, Essa Ferramenta ä Usada Absatz Processar Aplicativos da Empresa Criados Internamente. Ele Não Pode Server Usado Absatz Processar Aplicativos Que Foram Baixados da Loja de Aplicativos. Consulte:
  - [Preparar Aplicativos iOS Absatz o Gerenciamento de Aplicativos Móveis com einen Ferramenta de Disposição de Aplicativos führen Sie Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
  - [Preparar Aplicativos Android Absatz o Gerenciamento de Aplicativos Móveis com einen Ferramenta de Encapsulamento de Aplicativos Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

Alguns Aplicativos Gerenciados, Como o Aplicativo führen Outlook Absatz iOS e Android, Dão Suporte eine **Multi-Identidade**. Isso Significa Que Intune Aplica als Configurações de Gerenciamento Somente eine Dados Ou Contas Corporativas keine Aplicativo.

Por Exemplo, Usando o Aplicativo führen Sie Outlook aus:
- SE o Usuário Configurar Uma ansprechen einer Kundentestgruppe de e-Mail Pessoal e Uma Corporativa, o Intune Aplicará als Configurações de Gerenciamento Apenas À ansprechen einer Kundentestgruppe Corporativa e Não Gerencia A ansprechen einer Kundentestgruppe Pessoal.
- SE o Dispositivo für Desativado Ou Seu Registrado Cancelado, führen Sie Somente os Dados Corporativos Outlook Serão Removidos Dispositivo.
- Eine ansprechen einer Kundentestgruppe Corporativa Usada Deve Server eine Mesma ansprechen einer Kundentestgruppe Que Foi Usada Absatz Registrierung o Dispositivo keine Intune.

Word, Excel e PowerPoint Também Dão Suporte eine Identidades Várias Exceto als Restrições de Política Que Se Aplicam Somente Ao Gerenciar e Editar Dados de Identificação Empresarial de Serviço Como um OneDrive Ou SharePoint.

## <a name="criar-e-implantar-um-aplicativo-no-intune-com-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Criar e implantar um Aplicativo keine Intune com Uma Política de Gerenciamento de Aplicativos Móveis

- Etapa 1: Obter o verknüpfen Absatz um Aplicativo Gerenciado Por Política Ou Criar um Aplicativo Encapsulado.
- Etapa 2: Publicar o Aplicativo langen Seu Espaço de Armazenamento de Nuvem.
- Etapa 3: Criar Uma Política de Gerenciamento de Aplicativos Móveis.
- Etapa 4: implantar o Aplicativo Selecionando einer Opção Absatz Associar o Aplicativo ein Uma Política de Gerenciamento de Aplicativos Móveis.
- Etapa 5: Monitorar einer Implantação führen Aplicativo.

### <a name="etapa-1-obter-o-link-para-um-aplicativo-gerenciado-por-poltica-ou-criar-um-aplicativo-encapsulado"></a>Etapa 1: Obter o verknüpfen Absatz um Aplicativo Gerenciado Por Política Ou Criar um Aplicativo Encapsulado
- 
            Führen Sie Aplicativo Gerenciado Por Política Que Você Deseja implantar **Obter Absatz um verknüpfen Absatz um Aplicativo Gerenciado Por Política** - Na Windows Store, Encontre e Anote eine URL.
Por Exemplo, führen Sie eine URL Aplicativo Microsoft Word Absatz iPad ä [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- 
            **Absatz Criar um Aplicativo Encapsulado**: Verwenden Sie als Informações Nummern Tópicos [Preparar Aplicativos iOS Absatz o Gerenciamento de Aplicativos Móveis com einen Ferramenta de Disposição führen Aplicativo führen Sie Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) e [Preparar Aplicativos Android Absatz o Gerenciamento de Aplicativos Móveis com einen Ferramenta de Disposição führen Aplicativo führen Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) Absatz Criar um Aplicativo Encapsulado. Ein Ferramenta Cria um Aplicativo Processado Que Será Usado Quando Você Publica o Aplicativo keine Espaço de Armazenamento de Nuvem.

### <a name="etapa-2-carregar-o-aplicativo-em-seu-espao-de-armazenamento-de-nuvem"></a>Etapa 2: Carregar o Aplicativo langen Seu Espaço de Armazenamento de nuvem
Quando Você Publica um Aplicativo Gerenciado, os Procedimentos Diferem Se Você Estiver Publicando um Aplicativo Gerenciado Por Política Ou um Aplicativo Que Foi Processado Usando eine Ferramenta de Disposição de Aplicativos führen Microsoft Intune Absatz iOS.

Veja [Adicionar Aplicativos Absatz Dispositivos Móveis keine Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune#add-the-app) Absatz Obter als Etapas Completas Necessárias Absatz Carregar um Aplicativo langen Seu Espaço de Armazenamento de Nuvem.

### <a name="etapa-3-criar-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Etapa 3: Criar Uma Política de Gerenciamento de Aplicativos móveis
O Portal Azure ä o Konsole de Administração Recomendado Absatz Criar Políticas MAM de. O Portal Aktionen Azure Dá Suporte Aos Seguintes Cenários MAM aus:
- Dispositivos Registrados keine Intune
- Dispositivos Gerenciados Por Uma Solução MDM terceirizada
- Dispositivos Que Não São Gerenciados Por Uma Solução MDM (BYOD).

Veja [Criar e implantar Políticas de Gerenciamento de Aplicativo Móvel com-o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) Absatz Saber Mais Sobre o uso Portal Azure Absatz Criar Uma Política de MAM.

SE keine Momento Você Estiver Usando o Konsole de Administração Intune Absatz Gerenciar Seus Dispositivos Poderá Criar Uma Política MAM Que dê Suporte einer Aplicativos Absatz Dispositivos Registrados keine Intune Usando o [Konsole de Administração Intune führen](https://docs.microsoft.com/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console#-step-3-create-a-mobile-application-management-policy).


### <a name="etapa-4-implantar-o-aplicativo-selecionando-a-opo-para-associar-o-aplicativo-a-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Etapa 4: implantar o Aplicativo, eine Opção Absatz Associar o Aplicativo eine Uma Política de Gerenciamento de Aplicativos Móveis selecionando
SE Você Estiver Usando o Portal, Azure, [Implante ein Política de MAM Absatz Usuários](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune#deploy-a-policy-to-users)folgendermaßen vor.

SE Você Estiver Usando o Portal Intune, [Implante o Aplicativo](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune#deploy-an-app), Garantindo Que Você Selecione werden eine Política de Gerenciamento de Aplicativo Móvel NV Página de Gerenciamento de Aplicativo Móvel Absatz Associar eine Política Ao Aplicativo.

SE o Dispositivo Tiver o Registro keine Intune Desfeito, als Políticas Não Serão Removidas Dos Aplicativos. Quaisquer Aplicativos Que Tiverem Políticas Aplicadas Manterão als Configurações de Política, Mesmo Depois de Server Desinstalado e Reinstalado.

#### <a name="o-que-fazer-quando-um-aplicativo-j-est-implantado-em-dispositivos"></a>O Que Fazer Quando um Aplicativo Já Está Implantado langen Dispositivos

Pode haver Situações langen Que Você implantar um Aplicativo e um Dos Usuários Ou Dispositivos de Destino Já Tem Uma Versão Não Gerenciada führen Aplicativo Instalada, Por Exemplo, o Usuário Instalou o Microsoft Word da Loja de Aplicativos.

Nesse Caso, Você Deve Pedir Ao Usuário Absatz Desinstalar Manualmente einer Versão Não Gerenciada Absatz Que Possa Server Instalada ein Versão Gerenciada Que Você Configurou.

Keine Entanto, Absatz Dispositivos Que Executam o iOS 9 e Versões Posteriores, o Intune Automaticamente Solicitará Ao Usuário Permissão Absatz Assumir o Gerenciamento Aplicativo Existente. SE Eles Concordarem o Aplicativo Será Gerenciado Pelo Intune e Qualquer Política de MAM Associada Ao Aplicativo Também Será Aplicada.


### <a name="etapa-5-monitorar-a-implantao-do-aplicativo-com-a-poltica-de-mam"></a>Etapa 5: Führen Sie eine Implantação Monitorar Aplicativo com einen Política de MAM
Betriebssystems Procedimentos eine Seguir Absatz Monitorar eine Implantação Aplicativo Por Meio Konsole Aktionen Intune e Auflösung Conflitos de Política aus.

1. Keine [Konsole de Administração führen Sie Microsoft Intune](https://manage.microsoft.com/)Clique langen **Grupos**.
2. Uma Attached Seguintes Etapas ausführen:
  -  Clique langen **Todos os Usuários** e Clique Duas Vezes keine Usuário Cujos Dispositivos Você Deseja Examinar. Na Página Propriedades Usuário Clique langen **Dispositivos** e Clique Duas Vezes führen keine Dispositivo Que Você Deseja Examinar.
  -  Dieser Abschnitt Clique **Todos os Dispositivos > Todos os Dispositivos Móveis**. Na Página Propriedades Aktionen Grupo de Dispositivos, Clique langen **Dispositivos** e Clique Duas Vezes keine Dispositivo Que Você Deseja Examinar aus.
3. Na Página Propriedades Dispositivo Móvel, Clique langen **Política** Absatz Ver Uma Lista Attached Políticas de MAM Que Foram Implantados führen keine Dispositivo.
4. Ein Política de MAM Cujo Status Você Deseja Exibir Selecione. Você Pode Ver Detalhes da Política keine Painel schlechter e Expandir o Nó Absatz Exibir als Configurações.
5.  Na Coluna Status de Cada Uma Attached Políticas de MAM, Compatível, Compatível (Pendente) Ou Aufgabenschema Será Exibido. SE eine Política Selecionada Tiver Uma Ou Mais Configurações Conflitantes, Aufgabenschema Será Exibido Nesse campo
6.  Após ter Identificado um Conflito Você Pode Revisar als Configurações de Política Conflitantes Absatz usar eine Mesma Configuração Ou implantar Apenas Uma Política Absatz o Aplicativo e o Usuário.

> [!NOTE]
> Você Pode Saber Mais Informações Gerais Sobre Monitoramento de Aplicativos Por Meio machen [Portal werden Azure](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) Ou Usando o [Konsole Intune führen](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune).

## <a name="onde-ir-daqui"></a>Onde Infrarot-daqui

Depois de Criar e implantar um Aplicativo Associado eine Uma Política de MAM, Você Pode Saber Mais Sobre o [Experiência führen Usuário endgültigen de MAM](end-user-experience-mam.md). Isso Ajudará einer Se Preparar Absatz Problemas Que Possam Surgir.
