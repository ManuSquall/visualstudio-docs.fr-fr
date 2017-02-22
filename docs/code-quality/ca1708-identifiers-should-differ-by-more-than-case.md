---
title: "CA1708 : Les identificateurs ne doivent pas diff&#233;rer que par leur casse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1708 : Les identificateurs ne doivent pas diff&#233;rer que par leur casse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Les noms de deux types, membres, paramètres ou espaces de noms qualifiés complets deviennent identiques lorsqu'ils sont convertis en minuscules.  
  
## Description de la règle  
 Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle\-ci.  Par exemple, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] est un langage ne respectant pas la casse qui est beaucoup utilisé.  
  
 Cette règle déclenche uniquement sur des membres visibles publiquement.  
  
## Comment corriger les violations  
 Sélectionnez un nom qui se révélera unique lors d'une comparaison à d'autres identificateurs qui ne respectent pas la casse.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  La bibliothèque peut ne pas être utilisable dans tous les langages disponibles dans [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Exemple de violation  
 L'exemple suivant indique une violation de cette règle.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Règles connexes  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)