---
title: "Security of Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, security"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Security of Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les modèles de texte posent les problèmes de sécurité suivants :  
  
-   Les modèles de texte sont vulnérables aux insertions de code arbitraire.  
  
-   Si le mécanisme que l'hôte utilise pour rechercher un processeur de directive n'est pas sécurisé, un processeur de directive malveillant peut être exécuté.  
  
## Code arbitraire  
 Lorsque vous écrivez un modèle, vous pouvez placer n'importe quel code dans les balises \<\# \#\>.  Cela permet l'exécution de code arbitraire à partir d'un modèle de texte.  
  
 Veillez à obtenir les modèles auprès de sources approuvées.  Faites savoir aux utilisateurs finaux de votre application qu'ils ne doivent pas exécuter de modèles ne provenant pas de sources approuvées.  
  
## Processeur de directive malveillant  
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle en fichier de sortie.  Pour plus d'informations, consultez [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Si le mécanisme que l'hôte utilise pour rechercher un processeur de directive n'est pas sécurisé, un processeur de directive malveillant risque d'être exécuté.  Le processeur de directive malveillant peut fournir du code qui est exécuté en mode `FullTrust` en même temps que le modèle.  Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, tel que le Registre, pour permettre au moteur de rechercher les processeurs de directive.