---
title: "CA1804&#160;: Supprimez les variables locales inutilis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1804&#160;: Supprimez les variables locales inutilis&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode déclare une variable locale, mais n'utilise pas la variable sauf éventuellement en tant que destinataire d'une instruction d'assignation.  Pour l'analyse par cette règle, l'assembly testé doit être construit avec des informations de débogage et le fichier de base de données de programme \(.pdb\) associé doit être disponible.  
  
## Description de la règle  
 Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez ou utilisez la variable locale.  Remarquez que le compilateur C\# intégré à [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] supprime ces variables locales inutiles lorsque l'option `optimize` est activée.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si la variable était émise par un compilateur.  Par mesure de sécurité, il est également recommandé de supprimer un avertissement de cette règle, voire de désactiver la règle, si les performances et la maintenance du code ne constituent pas des problèmes de premier plan.  
  
## Exemple  
 L'exemple suivant présente plusieurs variables locales inutilisées.  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## Règles connexes  
 [CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812 : Évitez les classes internes non instanciées](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801 : Passez en revue les paramètres inutilisés](../Topic/CA1801:%20Review%20unused%20parameters.md)