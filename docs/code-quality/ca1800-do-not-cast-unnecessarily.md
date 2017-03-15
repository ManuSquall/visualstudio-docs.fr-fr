---
title: "CA1800&#160;: N&#39;effectuez pas de cast inutilement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800&#160;: N&#39;effectuez pas de cast inutilement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode exécute des casts en doublon sur l'un de ses arguments ou l'une de ses variables locales.  Pour l'analyse complète par cette règle, l'assembly testé doit être construit à l'aide des informations de débogage et le fichier de base de données de programme \(.pdb\) associé doit être disponible.  
  
## Description de la règle  
 Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes.  Pour les opérations de casts en doublon explicites, stockez le résultat du cast dans une variable locale et utilisez cette dernière en lieu et place des opérations de casts en doublon.  
  
 Si l'opérateur C\# `is` est utilisé pour déterminer par test si le cast réussira avant son exécution proprement dite, vous pouvez plutôt envisager de tester le résultat de l'opérateur `as`.  Ce procédé offre les mêmes fonctionnalités sans que l'opérateur `is` exécute le cast implicite.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l'implémentation de la méthode pour réduire le nombre d'opérations de cast.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle, voire d'ignorer la règle, si les performances ne sont pas un problème.  
  
## Exemple  
 L'exemple suivant présente une méthode qui viole la règle à l'aide de l'opérateur C\# `is`.  Une seconde méthode satisfait la règle en remplaçant l'opérateur `is` par un test appliqué au résultat de l'opérateur `as`, procédé qui réduit le nombre d'opérations de cast par itération de deux à un.  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## Exemple  
 L'exemple suivant présente une méthode, `start_Click` avec plusieurs casts explicites en doublon qui enfreignent la règle, et une méthode, `reset_Click` qui satisfait la règle en stockant le cast dans une variable locale.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## Voir aussi  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)