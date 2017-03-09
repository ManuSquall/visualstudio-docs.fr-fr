---
title: "L’&#233;v&#233;nement &#39;Class_Terminate&#39; n’est plus pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;Class_Terminate&#39; n’est plus pris en charge
L’événement 'Class\_Terminate' n’est plus pris en charge. Utilisez 'Sub Finalize' pour libérer des ressources.  
  
 L’événement `Class_Terminate` des versions précédentes de Visual Basic est remplacé par des destructeurs de classe.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42002  
  
### Pour corriger cette erreur  
  
-   Déclarez une procédure `Sub` nommée `Finalize` pour terminer une classe.`Sub Finalize` est appelée lorsque le garbage collector détecte qu’il n’y a plus de références actives à l’instance.  
  
## Voir aussi  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/fr-fr/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [NOT IN BUILD : Procédure : implémentation du modèle DisposeFinalize \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/adf7a232-4ebb-485d-8626-8d64421eb0c4)