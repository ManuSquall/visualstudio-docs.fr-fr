---
title: "CA1043&#160;: Utiliser un argument de cha&#238;ne ou int&#233;gral pour les indexeurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1043&#160;: Utiliser un argument de cha&#238;ne ou int&#233;gral pour les indexeurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé contient un indexeur public ou protégé qui utilise un type d'index autre que <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> ou <xref:System.String?displayProperty=fullName>.  
  
## Description de la règle  
 Les indexeurs, c'est\-à\-dire les propriétés indexées, doivent utiliser des types entier ou de chaîne pour l'index.  Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d'utilisation de la bibliothèque.  L'utilisation du type <xref:System.Object> doit se restreindre aux cas où le type entier ou de chaîne spécifique ne peut pas être spécifié au moment du design.  Si le design nécessite d'autres types pour l'index, reconsidérez le fait que le type représente ou non un magasin de données logique.  S'il ne représente pas un magasin de données logique, utilisez une méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez l'index en un type entier ou un type de chaîne, ou utilisez une méthode au lieu de l'indexeur.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l'indexeur non standard.  
  
## Exemple  
 L'exemple suivant présente un indexeur qui utilise un index <xref:System.Int32>.  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## Règles connexes  
 [CA1023 : Les indexeurs ne doivent pas être multidimensionnels](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)