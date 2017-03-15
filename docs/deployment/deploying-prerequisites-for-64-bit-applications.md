---
title: "Composants requis pour le d&#233;ploiement d&#39;applications 64&#160;bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 bits (Visual Studio)"
  - "applications 64 bits (Visual Studio)"
  - "programmation 64 bits (Visual Studio)"
  - "déployer des applications (Visual Studio), 64 bits"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Composants requis pour le d&#233;ploiement d&#39;applications 64&#160;bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le déploiement ClickOnce prend en charge l'installation des applications sur les plateformes 64 bits.  Les plateformes cibles sont de type **x86** pour les plateformes 32 bits, **x64** pour les machines prenant en charge les jeux d'instructions AMD64 et EM64T, et **Itanium** pour le processeur Itanium 64 bits.  
  
## Composants requis  
 Le tableau suivant répertorie les composants redistribuables que vous pouvez utiliser comme composants requis pour l'installation de votre application 64 bits.  
  
 Si vous sélectionnez un composant requis qui n'a pas de composants 64 bits, vous risquez de voir s'afficher un avertissement indiquant que les packages sélectionnés ne sont pas disponibles pour la plateforme 64 bits.  
  
|Composant redistribuable|Prise en charge x64|Prise en charge IA64|  
|------------------------------|-------------------------|--------------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Oui|Non|  
|Bibliothèques Runtime Visual C\+\+ 2010 \(IA64\)|Non|Oui|  
|Bibliothèques Runtime Visual C\+\+ 2010 \(x64\)|Oui|Non|  
|Microsoft .NET Framework 4 \(x86 et x64\)|Oui||  
|Microsoft .NET Framework 4 Client Profile \(x86 et x64\)|Oui||  
  
## Voir aussi  
 [Déploiement d'applications, de services et de composants](../deployment/deploying-applications-services-and-components.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Applications 64 bits](../Topic/64-bit%20Applications.md)