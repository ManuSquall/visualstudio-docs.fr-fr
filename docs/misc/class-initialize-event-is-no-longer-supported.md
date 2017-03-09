---
title: "L’&#233;v&#233;nement &#39;Class_Initialize&#39; n’est plus pris en charge | Microsoft Docs"
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
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;Class_Initialize&#39; n’est plus pris en charge
L’événement 'Class\_Initialize' n’est plus pris en charge. Utilisez 'Sub New' pour initialiser une classe.  
  
 L’événement `Class_Initialize` des versions précédentes de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] est remplacé par des constructeurs de classe.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42001  
  
### Pour corriger cette erreur  
  
-   Déclarez une ou plusieurs procédures `Sub` nommées `New` pour initialiser une classe.`Sub New` est appelé quand une instance de classe est créée.  
  
## Voir aussi  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/fr-fr/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)