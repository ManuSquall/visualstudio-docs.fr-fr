---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; est sp&#233;cifi&#233; pour la classe &#39;&lt;nom_classe&gt;&#39;, mais n’a pas de membres publics pouvant &#234;tre expos&#233;s &#224; COM&#160;; par cons&#233;quent, aucune interface COM n’est g&#233;n&#233;r&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; est sp&#233;cifi&#233; pour la classe &#39;&lt;nom_classe&gt;&#39;, mais n’a pas de membres publics pouvant &#234;tre expos&#233;s &#224; COM&#160;; par cons&#233;quent, aucune interface COM n’est g&#233;n&#233;r&#233;e
Une classe qui utilise un bloc d’attributs `COMClassAttribute` ne définit pas de propriétés ou de méthodes `Public`. Si une classe doit être exposée comme un objet COM, ses propriétés et ses méthodes doivent être déclarées avec un accès `Public`.  
  
 Ce message est un avertissement par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40011  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Public` à une ou plusieurs propriétés ou méthodes de la classe, ou supprimez le bloc d’attributs `COMClassAttribute`.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)