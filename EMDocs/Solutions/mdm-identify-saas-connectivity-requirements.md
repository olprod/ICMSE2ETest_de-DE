---
title: Identificar Requisitos de Conectividade de SaaS
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6afbce4c-7500-4387-a19c-dff52c152097
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 15d896671f7687e017180bca2ca6acbd8dd0b0be
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="identificar-requisitos-de-conectividade-de-saas"></a>Identificar Requisitos de Conectividade de SaaS

>[!NOTE]
>Este Tópico Faz Parte de um Guia de Considerações Sobre Mais Amplo entwerfen. Führen Sie SE Você Quiser Começar Início Guia, Confira o [Tópico Prinzipal](mdm-design-considerations-guide.md). Absatz Obter Uma Cópia Baixável Deste Guia Inteiro, Visite ein [Galeria TechNet führen](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Ein Format Como Você Conecta Sua Infraestrutura lokalen Afetará eine Como Formatieren einer Identidade de Usuário e de Dispositivo Será Gerenciada com-Todas als Soluções de MDM: Intune, führen Sie MDM Absatz Office 365 e Implantações Híbridas Intune e Configuration Manager. Tanto o Intune Quanto o MDM Absatz Office 365 Aproveitam ein Arquitetura de Serviços de Diretório Fornecida Pelos Serviços führen Azure Active Directory. Essa Integração com-o Azure Oferece Bastante Flexibilidade Quando Você Estiver Projetando o Suporte de Gerenciamento de Identidades langen Sua Solução de Gerenciamento de Dispositivos Móveis.

Conforme Mostra als Listas Abaixo, eine Conexão Dos Serviços de Diretório Locais Ao Azure ä o principal Requisito Absatz Habilitar o Anmeldung Único E o Gerenciamento de Contas de Diretório Unificado. O Anmeldung Único Torna Muito Mais Fácil Absatz Seus Usuários Se Conectarem Aos Recursos da Empresa Que Estão Locais e NV Nuvem. Ter um Único lokalen Absatz Gerenciar Contas Facilita o Trabalho Dos Administradores. Absatz o Acesso Móvel Sincronizar Atributos e Credenciais de ansprechen einer Kundentestgruppe de Diretório Entre o Azure e os Serviços Locais de Diretório Permite Que os Usuários Se Autentiquem langen Seus Dispositivos Móveis Absatz Acessar os Recursos Que São Gerenciados Pelo MDM Absatz Office 365 Ou Intune wird.

![Führen Sie Visão Geral Gerenciamento Integrado de identidades](./media/MDM_Figure_15.png)

**Führen Sie Visão Geral Gerenciamento Integrado de identidades**

Dependendo de Como Você Respondeu Às Perguntas NV Tarefa 2, Você Precisa Conseguir Determinar Como eine Solução de SaaS Precisa Se Conectar à Sua Plataforma de Gerenciamento lokalen de Clientes de Sua Solução de Gerenciamento de Dispositivos Móveis. Als Listas Abaixo Ajudarão Você eine Entender Vantagens e Desvantagens de Conectar Sua Infraestrutura lokal eine Uma Solução de SaaS.

## <a name="intune-autnomo"></a>Intune (Autônomo)

**Vantagens**

- Führen Sie Totalmente Integrado Ao Azure Active Directory Absatz Gerenciar eine Identidade e Autenticação Usuário e dispositivo
- Dá Suporte Ao Autogerenciamento de Credenciais de Usuário e eine Experiências de Anmeldung Único Que Podem Aproveitar als Credenciais Existentes de ansprechen einer Kundentestgruppe lokalen
- Dá Suporte eine Anmeldung Único Absatz Milhares de Aplicativos SaaS Pré-integrados
- Dá Suporte À Segurança de Acesso Ao Aplicativo com A Imposição da mehrstufiger Authentifizierung DAS (Autenticação Multifator Baseada langen Regras) Absatz Aplicativos Locais e Na nuvem

**Desvantagens**

- Recursos e Funcionalidades Avançados de Conectividade de Serviços de Diretório Exigem o Emparelhamento com-o Azure Active Directory Premium

## <a name="mdm-para-o-office-365"></a>MDM Absatz o Office 365

**Vantagens**

- Que Usam eine Estrutura Azure Active Directory Absatz Gerenciar führen eine Identidade e Autenticação de Usuário e Dispositivo Sie Integrado Aos Locatários führen Sie Office 365
- OS Serviços Locais de Diretório Podem Server Conectados Como Parte da Conexão Dos Serviços Ao Office 365
- Dá Suporte Ao Autogerenciamento e eine Experiências de Anmeldung Único Que Podem Aproveitar als Credenciais Existentes de ansprechen einer Kundentestgruppe lokalen
- Führen Sie Oferece Suporte À Autorização de Multifator Absatz Inscrições de Dispositivos Usando o Serviço mehrstufiger Authentifizierung DAS Azure

**Desvantagens**

- Führen Sie Não Dá Suporte À Integração Gerenciamento de Aplicativos Móveis com-Outras Soluções Ou Aplicativos de SaaS

## <a name="hbrido-intune-com-configmgr"></a>Híbrido (Intune com Configuration Manager)

**Vantagens**

- Todas als Vantagens Aktionen Intune Autônomo, Além Attached Seguintes aus:
 - Führen Sie Integração Direta com-Serviços Locais de Diretório Por Meio da Infraestrutura Configuration Manager

**Desvantagens**

- Führen Sie Absatz als Organizações Que Não Tenham Uma Infraestrutura Configuration Manager Atual Configurada, Será Necessário Planejá-la, Instalá la e Configurá la Antes da Integração com-o Intune
- Exige Requisitos de Implantação lokalen Adicional e Alterações de Configuração Absatz als Organizações com-o Configuration Manager.
