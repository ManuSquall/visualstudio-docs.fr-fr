---
title: "D&#233;pannage des exceptions&#160;: System.CannotUnloadAppDomainException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CannotUnloadAppDomainException (classe)"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.CannotUnloadAppDomainException
Une exception <xref:System.CannotUnloadAppDomainException> est levée en cas de tentative de déchargement d'un des éléments suivants :  
  
-   Le domaine d'application par défaut, qui doit rester chargé pendant la durée de vie de l'application  
  
-   Un domaine d'application avec un thread en cours d'exécution qui ne peut pas arrêter l'exécution immédiatement  
  
-   Un domaine d'application qui a déjà été déchargé  
  
## Conseils associés  
 **Assurez\-vous que vous ne tentez pas de décharger le domaine d'application qui est le domaine par défaut, qui a un thread en cours d'exécution ou qui est déjà déchargé.**  
 Chacune de ces conditions provoque la levée de cette exception. Pour plus d'informations, consultez <xref:System.AppDomain.Unload%2A>.  
  
## Voir aussi  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)