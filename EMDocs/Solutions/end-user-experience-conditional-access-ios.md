---
title: "Führen Sie Experiência Usuário letzten Absatz Acesso Condicional langen Dispositivos iOS"
description: "Ein Experiência Usuário endgültigen de Registrierung tun um Dispositivo iOS."
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c641ea8-2c0e-490e-b1de-831336f46d19
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 183e8d9169df969a4667e64fe41f70b389ea4e20
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="ios"></a>iOS

O Prozessor de Registro e als Telas Que o Usuário Vê Serão um Pouco Diferentes Dependendo da Versão Möglichkeiten Sistema Operacional langen Execução keine Dispositivo Usuário endgültigen. Este Tópico Descreve eine Experiência Aktionen Usuário letzte Absatz Registrierung Dispositivos iOS aus.

## <a name="registro"></a>Registro

1.  SE um Usuário Já Estiver Registrado keine Intune e für Compatível Ele Não Verá Nenhuma Diferença langen Dispositivos führen iOS: o Acesso Aos Continuará Normalmente-e-Mails. SE o Usuário Ainda Não Estiver Registrado, Ele Verá Uma Mensagem de Quarentena Semelhante eine Este Quando Iniciar Seu Aplicativo de e-Mail:

    ![Captura de Tela Mostrando o langen Quarentena Que o Usuário Recebe langen e-Mail um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-Get-Started.PNG)

    Ein Usuário Clica langen **Comece Agora Mesmo** Absatz Começar eine Registrierung Seus Dispositivos.

2.  Führen Sie Ä Solicitado Que o Usuário instale o Aplicativo Portal da Empresa Intune Na Respectiva Loja de Aplicativos.

    ![Captura de Tela Mostrando o Portal da Empresa führen Intune langen um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-intune-Company-Portal.png)

    O Usuário Abre o Aplicativo e Entra Usando Suas Credenciais da Empresa Depois de Instalado.

3.  Na Tela de Configuração de Acesso da Empresa, o Usuário Clica langen **Iniciar** Absatz Começar ein Configurar Seu Dispositivo e Verificar Se Ele ä Compatível.

    ![Captura de Tela Mostrando einer Tela Configuração de Acesso da Empresa langen um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-company-AccessSetup.png)

4.  Na Tela de Registro Aktionen Dispositivo o Usuário Clica langen **Registro** Absatz Registrierung Seu Dispositivo aus.

    ![Captura de Tela Mostrando eine Tela Registro Dispositivo langen führen um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-device-Enrollment.png)

    Durante o Registro, o Perfil de Gerenciamento de Dispositivo Móvel ä Instalado Absatz Permitir Que Você, o Administrador de TI Gerencie Remotamente o Dispositivo. O Usuário insere Sua Senha Se Solicitada.

5.  Na Tela de Configuração de Acesso da Empresa o Usuário Clica langen **Continuar** Absatz Iniciar eine Verificação de Conformidade Dispositivo.

    ![Captura de Tela Mostrando Que o Registro de Dispositivo Foi Bem Sucedido langen um Dispositivo iOS e o Usuário Precisa Verificar eine Conformidade](./media/ProtectEmail/EUX-iOS-device-Compliance-Check.png)

    SE Houver um Problema de Conformidade, Será Solicitado Que o Usuário Resolva o Problema (Como Criar Uma Senha Válida) e, langen Seguida, Clique langen **Verificar Conformidade** Absatz Continuar.

    ![Captura de Tela Mostrando Que o Usuário Deve Auflösung Problemas de Conformidade langen um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-check-Compliance.png)

6.  Depois Que o Dispositivo Estiver Totalmente Compatível, o Usuário Clica langen **Continuar** Absatz Continuar.

    ![Captura de Tela Mostrando Que o-Dispositivo iOS ä-Compatível E ein Instalação Foi concluída](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    Depois Que o Usuário Estiver Registrado e ein Conformidade für Verificada, o Acesso Ao e-Mail Deverá Ficar Disponível Dentro de Alguns Minutos.

SE o Usuário Seguir Essas Etapas Absatz Registrierungsstelle e Ficar Compatível e Ainda Não Puder Acessar Seus-e-Mails keine Dispositivo Móvel, Ele Poderá Seguir Estas Etapas Adicionais Absatz Tentar Corrigir o Problema:

-   Primeiro, Verifique Se Seu Dispositivo Está Registrado. Caso Contrário, o Usuário Deve Seguir als Etapas Acima.

-   Verifique Se o Dispositivo ä Compatível Clicando langen **Verificar Conformidade**. SE um Aufgabenschema de Conformidade für Identificado, o Usuário Poderá Seguir als Instruções Específicas Absatz Seu Dispositivo Móvel Sobre Como Resolvê-la, Tal Como Redefinir Sua Senha.

-   Ligue Absatz o Suporte Técnico.

## <a name="problemas-e-solues"></a>Problemas e soluções
Por Padrão, eine Cada 8 Horas os Dispositivos São Verificados Absatz Verificar Se Eles Ainda São Compatíveis. SE um Dispositivo Que Zeitraum Anteriormente Compatível Considerado Incompatível (Por Exemplo Devido eine Uma Política de Conformidade ter Sido Adicionada Ou Alterada), o Usuário Pode Seguir Estas Etapas Absatz Restaurar eine Conformidade Dispositivo bieten:

1.  O Usuário Recebe eine Notificação Por e-Mail-Ou langen Seu Dispositivo Que Este ä Incompatível. Neste Momento, o Dispositivo Está langen Quarentena keine Exchange.

2.  SE o Usuário Tentar Acessar o e-Mail, Ele Será Redirecionado Absatz a Tela de Configuração de Acesso da Empresa Portal da Empresa Intune langen Que Se ä Mostrado Se Eles Estão für eine de Conformidade führen.

    ![Captura de Tela Mostrando Que o Dispositivo iOS Se Tornou Não compatível](./media/ProtectEmail/EUX-iOS-fallOut-Compliance.png)

3.  Ein Usuário Clica langen **Continuar** e o Problema de Conformidade Que Está Impedindo Que Ele Acesse o e-Mail ä Mostrado.

    ![Captura de Tela Mostrando Que o Usuário Deve Auflösung Problemas de Conformidade langen um Dispositivo iOS](./media/ProtectEmail/EUX-iOS-check-Compliance.png)

4.  Depois Que o Problema Foi Corrigido, Eles Devem Clicar langen **Verificar Conformidade** Absatz Verificar Se o Problema Foi Resolvido.

5.  SE o Problema Estiver Corrigido, o Usuário Clica langen **Continuar** Absatz Concluir o Prozessor.

    ![Captura de Tela Mostrando Que o-Dispositivo iOS ä-Compatível E ein Instalação Foi concluída](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    O Acesso Ao e-Mail Deverá Ficar Disponível Novamente Dentro de Alguns Minutos.

### <a name="onde-ir-daqui"></a>Onde Infrarot-daqui
Ein Experiência Aktionen endgültigen ä Usuário um Pouco Diferente langen Outros Dispositivos Móveis aus. Saiba Mais Sobre eine Experiência Aktionen Usuário letzte Absatz [Android](end-user-experience-conditional-access-android.md) e [Windows Phone](end-user-experience-conditional-access-winphone.md)aus.
