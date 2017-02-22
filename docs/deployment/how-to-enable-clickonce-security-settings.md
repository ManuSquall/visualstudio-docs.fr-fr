---
title: "How to: Enable ClickOnce Security Settings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "security [Visual Studio], ClickOnce applications"
  - "ClickOnce deployment, security settings"
  - "security settings, ClickOnce deployment"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La sécurité d'accès du code pour les applications ClickOnce doit être activée pour publier l'application.  Cela s'effectue automatiquement si vous publiez une application à l'aide de l'Assistant Publication.  
  
 Dans certains cas, l'activation de la sécurité d'accès du code peut avoir un impact sur les performances lors de la génération ou du débogage de votre application ; si tel est le cas, il peut être utile de désactiver temporairement les paramètres de sécurité.  
  
 Les paramètres de sécurité ClickOnce peuvent être activés ou désactivés dans la page **Sécurité** du **Concepteur de projets**.  
  
### Pour activer les paramètres de sécurité ClickOnce  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité**.  
  
3.  Activez la case à cocher **Activer les paramètres de sécurité ClickOnce**.  
  
     Vous pouvez désormais personnaliser les paramètres de sécurité de votre application dans la page Sécurité.  
  
    > [!NOTE]
    >  Cette case à cocher est automatiquement activée à chaque publication de l'application avec l'Assistant **Publication**.  
  
### Pour désactiver les paramètres de sécurité ClickOnce  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité**.  
  
3.  Désactivez la case à cocher **Activer les paramètres de sécurité ClickOnce**.  
  
     Votre application s'exécutera avec les paramètres de sécurité Confiance totale ; tout paramètre de la page **Sécurité** sera ignoré.  
  
    > [!NOTE]
    >  Cette case à cocher sera activée à chaque publication de l'application avec l'Assistant Publication ; vous devez la désactiver à nouveau à chaque publication réussie.  
  
## Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)