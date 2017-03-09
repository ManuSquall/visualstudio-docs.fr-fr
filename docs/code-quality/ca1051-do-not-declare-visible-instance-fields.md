---
title: "CA1051&#160;: Ne pas d&#233;clarer de champs d&#39;instances visibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051&#160;: Ne pas d&#233;clarer de champs d&#39;instances visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type visible de l'extérieur dispose d'un champ d'instance extérieurement visible.  
  
## Description de la règle  
 Un champ s'utilise principalement en tant que détail d'implémentation.  Les champs doivent être `private` ou `internal` et doivent être exposés au moyen de propriétés.  Il est aussi facile d'accéder à une propriété qu'à un champ, et le code dans les accesseurs d'une propriété peut changer lorsque les fonctionnalités du type évoluent sans introduire de modifications avec rupture.  Les propriétés qui retournent simplement la valeur d'un champ privé ou interne sont optimisées pour s'exécuter de pair avec l'accès à un champ ; le gain de performance associé à l'utilisation de champs visibles de l'extérieur au lieu de propriétés est minime.  
  
 L'expression "visible de l'extérieur" fait référence aux niveaux d'accessibilité `public`, `protected` et `protected internal` \(`Public`, `Protected` et `Protected Friend` en Visual Basic\).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez le champ `private` ou `internal`, puis exposez\-le à l'aide d'une propriété visible de l'extérieur.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Les champs visibles de l'extérieur ne fournissent pas tous les avantages inaccessibles aux propriétés.  En outre, les champs publics ne peuvent pas être protégés par [Demandes de liaison](../Topic/Link%20Demands.md).  Consultez [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Exemple  
 L'exemple suivant présente un type, \(`BadPublicInstanceFields`\), qui ne respecte pas cette règle.  `GoodPublicInstanceFields` affiche le code corrigé.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Règles connexes  
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## Voir aussi  
 [Demandes de liaison](../Topic/Link%20Demands.md)