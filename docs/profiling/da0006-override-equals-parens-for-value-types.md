---
title: "DA0006&#160;: Remplacer Equals() pour les types valeur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006&#160;: Remplacer Equals() pour les types valeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0006|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage|  
|Message|Remplacer Equals et l'opérateur d'égalité pour les types valeur.|  
|Type Messge|Avertissement|  
  
## Cause  
 Les appels à la méthode Equals ou les opérateurs d'égalité d'un type valeur public représentent une proportion significative des données de profilage.  Envisagez d'implémenter une méthode plus efficace.  
  
## Description de la règle  
 Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque <xref:System.Reflection> et compare le contenu de tous les champs dans le type.  Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile.  Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals.  Si votre langage de programmation prend en charge la surcharge d'opérateur, vous devez également fournir une implémentation des opérateurs d'égalité et d'inégalité.  
  
 Pour plus d'informations sur la substitution de Equals et des opérateurs d'égalité, consultez [Guidelines for Implementing Equals and the Equality Operator \(\=\=\)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## Comment examiner un avertissement  
 Pour obtenir un exemple de l'implémentation des opérateurs Equals et d'égalité, consultez la règle d'analyse du code [CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)