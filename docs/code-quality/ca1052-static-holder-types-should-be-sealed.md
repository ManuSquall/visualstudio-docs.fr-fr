---
title: "CA1052&#160;: Les types de conteneurs statiques doivent &#234;tre sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1052&#160;: Les types de conteneurs statiques doivent &#234;tre sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé contient uniquement des membres statiques et n'est pas déclaré avec le modificateur [sealed](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\).  
  
## Description de la règle  
 Cette règle suppose qu'un type qui contient uniquement des membres statiques n'est pas conçu pour être hérité, car il ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé.  Un type qui n'est pas destiné à être hérité doit être marqué avec le modificateur `sealed` pour empêcher son utilisation en tant que type de base.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez le type en tant que `sealed`.  Si vous ciblez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 ou une version antérieure, une meilleure approche consiste à marquer le type comme `static`.  Vous évitez ainsi de devoir déclarer un constructeur privé pour empêcher la création de la classe.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité.  L'absence du modificateur `sealed` laisse entendre que le type est utile en tant que type de base.  
  
## Exemple de violation  
  
### Description  
 L'exemple suivant présente un type qui enfreint la règle.  
  
### Code  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Résoudre avec le modificateur statique  
  
### Description  
 L'exemple suivant indique comment résoudre une violation de cette règle en marquant le type avec le modificateur `static`.  
  
### Code  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Règles connexes  
 [CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)