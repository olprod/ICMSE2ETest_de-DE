---
title: "Proteção de e-Mail e Documentos da empresa"
description: "Permitir Que Apenas Dispositivos Compatíveis Acessem e-Mail da Sua Empresa e Protejam o Conteúdo e Anexos de e-Mail."
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 78d8368e-1bfe-4ac4-991d-467321a76ed7
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: d2d2b5254267af54b9c3f3243104f9bbb3066976
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="proteo-de-emails-e-documentos-corporativos"></a>De Proteção e Documentos Corporativos-e-Mails
Proteção de e-Mail Corporativo Envolve Dois Objetivos Principais:

-   Permitir Somente einer Dispositivos Compatíveis Acessar o e-Mail da empresa

-   Führen Sie Proteção Conteúdo de e-Mail e anexos

## <a name="permitir-somente-a-dispositivos-compatveis-acessar-o-email-da-empresa"></a>Permitir Somente einer Dispositivos Compatíveis Acessar o e-Mail-da empresa
UMA Etapa Importante Absatz Proteger Dados Corporativos ä Restringir o Acesso eine Dispositivos Que Não Usem Uma Senha Forte-Não Estejam Desbloqueado Ou Não Estejam Criptografados. O Microsoft Intune Oferece eine Capacidade de Definir als Condições Que os Usuários Devem Cumprir Absatz Obter Acesso Aos Recursos da Empresa. Isso ä Conhecido Como Acesso Condicional.

Acesso Condicional ä Determinado Por Dois Tipos de Políticas Que Podem Server Definidas keine Intune:


            **Políticas de conformidade** determinam a conformidade de um dispositivo. Elas avaliam as configurações e as condições, como:

-   
            **PINs e Senhas**: Sua TI Pode Criar Regras Absatz Exigir Senhas de Desbloquear antes um Dispositivo, Como Complexidade da Senha Expiração de Senha e Outras Configurações de Senha.

-   
            **Criptografia**: Sua TI Pode Restringir o Acesso ein Dispositivos Criptografados.

-   
            **O Dispositivo Não Está Desbloqueado Ou Enraizado**: o Intune Pode Detectar Se um Dispositivo Registrado Está Desbloqueado e Sua TI Pode Definir eine Política Absatz Bloquear o Acesso ein Esses Dispositivos.


            **Políticas de acesso condicional** são configuradas para um serviço específico como o Exchange Online ou no SharePoint Online. Para cada serviço, você pode definir a quais grupos de usuários essas políticas devem ser aplicadas. Por exemplo, você pode garantir que todos no departamento financeiro possam acessar apenas email de dispositivos registrados e compatíveis.

## <a name="experincia-de-alto-nvel-do-usurio-final"></a>Experiência de Alto Nível Usuário final
Após einer Solução-Server-Implementada os Usuários Finais Só Poderão Acessar o e-Mail da Empresa langen Dispositivos Gerenciados e Compatíveis. Quando Eles Tiverem eine Capacidade de Acessar o e-Mail Nummern Dispositivos, os Dados da Empresa Ficarão Protegidos e Contidos keine Ecossistema Aplicativo e Ficarão Disponíveis Apenas Absatz os Usuários Pretendidos. O Acesso Pode Server Revogado ein Qualquer Momento Se o Dispositivo für Incompatível.

Especificamente, als Políticas de Acesso Condicional Definidas keine Intune Garantem Que os Dispositivos Possam Acessar o e-Mail Somente Se Forem Compatíveis com als Políticas de Conformidade Que Você Definir. Ações Como Copiar e colar Ou Salvar langen Serviços Pessoais de Armazenamento NV Nuvem Podem Server Restringidas Usando Políticas de Gerenciamento de Aplicativos Móveis. O Serviço de Gerenciamento de Direitos Aktionen Azure Pode Server Usado Absatz Garantir Que os Dados Confidenciais de-e-Mails, Bem Como os Anexos Encaminhados, Somente Possam Server Lidos Pelos Destinatários Pretendidos aus. Eine Experiência führen Usuário endgültigen ä Descrita com Mais Detalhes langen [Experiência Usuário endgültigen de Acesso Condicional führen](end-user-experience-conditional-access.md).


Assista eine [Este](https://www.youtube.com/watch?feature=player_embedded&v=lYx3YIezccg) Vídeo de Quatro Minutos Absatz Ver Como Acesso Condicional Afeta os Usuários Finais.

## <a name="por-que-a-arquitetura-importante"></a>Por Que eine Arquitetura ä importante
OS Diferentes Componentes Aktionen zur Abstimmung e o Office 365 São Criados e Projetados Absatz Execução NV Nuvem aus. Isso Traz Todos os Benefícios Que eine Nuvem Oferece: Escalabilidade, Flexibilidade e Facilidade de Gerenciamento.

UMA Vez Que Diferentes Empresas Têm Requisitos Diferentes, o zur Abstimmung Foi Projetado Absatz Integrar Se com einen lokalen Infraestrutura Existente, Como o Active Directory, o Exchange Server Ou o System Center Configuration Manager. Verwenden Sie Isso Permite Que Você als Credenciais Já Estabelecidas langen Sua Absatz Seus Recursos Locais e Na Nuvem.

Als Seções einer Seguir Descrevem eine Arquitetura Conforme Projetada Absatz Server Executada NV Nuvem e Falam Brevemente Sobre ein lokaler Opção.

### <a name="fluxo-de-acesso-de-email"></a>Fluxo de Acesso de e-Mail
Führen Sie Dependendo Tipo de Aplicativo de e-Mail Que Você Usa Absatz Acessar o Exchange online, o Caminho Absatz Estabelecer Acesso Seguro Ao e-Mail Pode Server Ligeiramente Diferente. Keine Entanto, os Componentes Principais: AD Azure (Active Directory Do Azure), Office 365/Exchange Online e Microsoft Intune São os Mesmos. Ein Experiência de TI e eine Experiência Usuário endgültigen Também São Semelhantes. O zur Abstimmung Atualmente Dá Suporte eine Aplicativos de e-Mail Nativos e Ao Aplicativo Microsoft Outlook Absatz iOS e Android.

### <a name="fluxo-de-controle-de-acesso-para-aplicativos-de-email-nativos"></a>Fluxo de Controle de Acesso Absatz Aplicativos de e-Mail nativos
OS Clientes führen Exchange ActiveSync (EAS) Que Estiverem Tentando Acessar e-Mail keine Exchange Online Serão Avaliados Absatz als Seguintes Propriedades:

-   O Dispositivo ä Gerenciado Pelo Intune?

-   O Dispositivo Está Registrado com-o Active Directory tun Azure?

-   O Dispositivo ä Compatível?

-   Eine ID EAS tun Cliente Está Mapeada Absatz um Dispositivo Registrado?

Absatz Obter um Estado Compatível, o Dispositivo langen Que o Cliente EAS Está langen Execução Precisa:

-   Registrierung com-o Intune

-   Registre-Se-com-o [Azure Active Directory](https://msdn.microsoft.com/6a14cb1f-a058-4453-8ede-d9f4a66a7073.aspx) Absatz

-   Estar langen Conformidade com als Políticas de Dispositivo Definidas Por Seu Administrador de TI.

Na Maioria Attached Plataformas o Registro de Dispositivo führen Sie Active Directory Azure Ocorre Automaticamente Durante o Registro. OS Estados de Dispositivo São Gravados Pelo Intune keine Active Directory Azure Então Lidos Pelo Exchange Online Na Próxima Vez Que o Cliente EAS Tenta Obter e-Mail führen. SE o Dispositivo Não Estiver Registrado, o Usuário Receberá Uma Mensagem NV Caixa de Entrada com Instruções Sobre Como Registrierung (Também Conhecido Como Registro). SE o Dispositivo Não für Compatível o Usuário Receberá um Diferente Que o Redireciona Absatz o Portal da Web Intune langen Que Ele Poderá Obter Mais Informações Sobre o Problema de Conformidade e Como Corrigi e-Mail-lo.

O**Azure AD**Autentica o Usuário e o Dispositivo Microsoft Intune Gerencia eine Conformidade e als Políticas de Acesso Condicional Enquanto o **Exchange Online** Gerencia o Acesso Ao e-Mail COM-Basis keine Estado Dispositivo.

![E-Mail-Gráfico Que Mostra o Fluxo de Controle de Acesso Absatz Aplicativos de Nativos langen Dispositivos com Android e iOS](./media/ProtectEmail/Access-Control-Flow-For-Native-Email-Apps.png)

### <a name="fluxo-de-controle-de-acesso-para-aplicativos-do-outlook"></a>Führen Sie Outlook Fluxo de Controle de Acesso Absatz aplicativos
Semelhante Ao Cliente EAS, o Aplicativo de e-Mail führen Outlook Que Estiver Tentando Acessar o e-Mail keine Exchange Online Será Avaliado Absatz als Seguintes Propriedades:

-   O Dispositivo ä Gerenciado Pelo Intune?

-   O Dispositivo Está Registrado com-o Active Directory tun Azure?

-   O Dispositivo ä Compatível?

Ein Conformidade tun Dispositivo ä Estabelecida Quase da Mesma formatieren Conforme Descrito keine Fluxo de Controle de Acesso de Cliente EAS an. Keine Entanto Absatz Aplicativos führen Sie Outlook, o Fluxo Entre os Componentes ä Levemente Diferente. Quando o Aplicativo Outlook Tenta Obter o e-Mail Ele ä Redirecionado Ao Azure AD. O Azure AD Emite um token de Segurança Se o Dispositivo für Avaliado com-Sucesso Como Estando Registrado e langen Conformidade. O token de Segurança Então ä Usado Absatz Obter e-Mail Corporativo führen Sie Exchange Online. Sincronização de e-Mail, NV Verdade, ä Orientada Por Meio Serviço de Nuvem Outlook und eine Que Obtém um token de Acesso Serviço EAS langen Nome Usuário Absatz Concluir eine Autenticação E Entrega o e-Mail.

![Führen Sie Outlook Gráfico Que Mostra o Fluxo de Controle de Acesso aplicativo](./media/ProtectEmail/Access-Control-Flow-For-Outlook-App.png)

## <a name="a-experincia-de-administrao-de-ti"></a>Ein Experiência de Administração de TI:
Não Há Necessidade de Uma Configuração de Infraestrutura Complexa Absatz o Azure AD Ou o Exchange Absatz Que Isso Aconteça. Seus Administradores de TI:

-   Konfigurieren von e Implante als Políticas de Conformidade Usadas Absatz Avaliar o Status de Conformidade Dispositivo.

-   Führen Sie eine Política de Acesso Condicional Exchange Online e Especificar Quais Grupos de Segurança AD Configurar führen Azure Serão Afetados Por Ela Ou Estão Isentos Dela.

-   Escolha Permitir Ou Bloquear Dispositivos Que Não São Capazes de Se Registrierungsstelle keine Intune. Eine Lista de Sistemas Operacionais com Suporte Absatz Dispositivos Móveis ä Apresentada Mais Adiante.

Pode Server Necessária Uma Etapa de Configuração Opcional. O Relatório Usado Absatz Gerenciar e Monitorar o Status e o Acesso Ao Dispositivo Requer eine Configuração Connector de Serviços führen Sie Microsoft Intune.

## <a name="a-experincia-do-usurio-final"></a>Ein Experiência-Usuário endgültigen:
E-Mail-Quando o Usuário Tenta Acessar keine Dispositivo Pela Primeira Vez Ou Sincronizar Posteriormente, o Status de Conformidade e de Registro Dispositivo ä Verificado führen. O Prozessor de Registrierungsstelle Ou Corrigir Problemas de Conformidade ä Uma Experiência Guiada. São Mostradas Ao Usuário als Etapas Necessárias Absatz Registrierung o Dispositivo e Torná final-lo Compatível sem Necessidade de Chamar o Suporte Técnico da TI:

-   
            **Se o Dispositivo Não Estiver Registrado**, eine Página de Anmeldung Mostrará o Acesso Negado e Solicitará o Registro. Keine Registro, o Dispositivo ä Registrado Automaticamente keine Active Directory Azure führen. O Intune Verifica o Dispositivo Absatz Rippen de Conformidade e Apresenta als Etapas de Solução Absatz Auflösung Quaisquer Problemas de Não Conformidade. Depois Que o Dispositivo Estiver langen Conformidade o Intune definieren o Status de Conformidade Dispositivo com-o Active Directory Azure.

-   
            **Se o Dispositivo Estiver Registrado, Mas Não Estiver langen Conformidade**, um com Etapas Absatz Corrigir os Problemas ä Enviado Ao Dispositivo verknüpfen. Quando o Usuário endgültigen Corrige o Problema (Por Exemplo, Definir Senha, Criptografia), o Intune Que Gerencia als Políticas de Conformidade Atualiza o Status de Conformidade führen Dispositivo keine Azure AD.

Quando o Dispositivo ä Avaliado Como Registro E langen Conformidade, eine Sincronização de e-Mail Deve Acontecer Dentro de Alguns Minutos.

## <a name="onde-ir-daqui"></a>Onde Infrarot-daqui
Agora Que Você Sabe Como Proteger-e-Mails e Documentos Corporativos, Pode verweist Sobre Como [Proteger Anexos de e-Mail](protect-email-attachments.md). Organisationseinheit Se Você Estiver pronto, Saiba Mais Sobre [Como Implementar Uma Solução Absatz Proteger Seu e-Mail Corporativo](implement-solution.md).
