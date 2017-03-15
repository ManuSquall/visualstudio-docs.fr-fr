---
title: "Probl&#232;me possible d&#233;tect&#233; pendant la g&#233;n&#233;ration de l’assembly&#160;: &lt;erreur&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40009"
  - "bc40009"
helpviewer_keywords: 
  - "BC40009"
ms.assetid: 4bc5108a-a96e-43be-8bba-a47441a25f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Probl&#232;me possible d&#233;tect&#233; pendant la g&#233;n&#233;ration de l’assembly&#160;: &lt;erreur&gt;
L’outil ALink, appelé par le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], signale une erreur lors de la génération de l’assembly. Il est possible qu’un assembly signé fasse référence à un assembly non signé.  
  
 Ce message est un avertissement. Le compilateur continue de générer l’assembly. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40009  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d’erreur et prenez les mesures nécessaires.  
  
2.  Recompilez le programme pour voir si l'erreur se produit à nouveau.  
  
3.  Si l'erreur se produit à nouveau, réinstallez le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
4.  Si l’erreur persiste après la réinstallation, rassemblez des informations sur le contexte dans lequel est survenue l’erreur, puis avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [PAVEOVER Support technique et accessibilité](http://msdn.microsoft.com/fr-fr/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)