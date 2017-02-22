---
title: "Comment&#160;: d&#233;finir une zone de s&#233;curit&#233; pour une application ClickOnce | Microsoft Docs"
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
  - "déploiement de ClickOnce, paramètres de sécurité"
  - "sécurité d’accès du code, applications ClickOnce"
  - "zones de sécurité, applications ClickOnce"
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: d&#233;finir une zone de s&#233;curit&#233; pour une application ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quand vous définissez des autorisations de sécurité d’accès du code pour une application ClickOnce, vous devez d’abord définir un ensemble d’autorisations de base dans la page **Sécurité** du **Concepteur de projet**.  
  
 Dans la plupart des cas, vous pouvez aussi sélectionner la zone **Internet** qui contient un ensemble limité d’autorisations, ou la zone **Intranet local** qui fournit un ensemble plus complet d’autorisations. Si votre application nécessite des autorisations personnalisées, sélectionnez la zone de sécurité **Personnalisée** pour les définir. Pour plus d’informations sur la définition d’autorisations personnalisées, consultez [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### Pour définir une zone de sécurité  
  
1.  Après avoir sélectionné un projet dans l’**Explorateur de solutions**, dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité**.  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce**.  
  
4.  Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle**.  
  
     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.  
  
5.  Dans la liste déroulante **Zone à partir de laquelle votre application sera installée**, sélectionnez une zone de sécurité.  
  
## Voir aussi  
 [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)