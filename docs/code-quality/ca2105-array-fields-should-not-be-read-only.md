---
title: "CA2105&#160;: Les champs de tableau ne doivent pas &#234;tre en lecture seule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2105&#160;: Les champs de tableau ne doivent pas &#234;tre en lecture seule
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un champ public ou protégé qui contient un tableau est déclaré en lecture seule.  
  
## Description de la règle  
 Lorsque vous appliquez le modificateur `readonly` \(`ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) à un champ qui contient un tableau, le champ ne peut pas être modifié pour faire référence à un tableau différent.  Toutefois, les éléments du tableau stockés dans un champ en lecture seule peuvent être modifiés.  Un code qui prend des décisions ou exécute des opérations en fonction des éléments d'un tableau en lecture seule accessible publiquement peut présenter une faille de sécurité exploitable.  
  
 Notez que la présence d'un champ public viole également la règle de conception [CA1051 : Ne pas déclarer de champs d'instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
## Comment corriger les violations  
 Pour corriger la faille de sécurité identifiée par cette règle, ne vous fondez pas sur le contenu d'un tableau en lecture seule accessible publiquement.  Il est fortement recommandé d'utiliser l'une des procédures suivantes :  
  
-   Remplacez le tableau par une collection fortement typée qui ne peut pas être modifiée.  Pour plus d’informations, consultez <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.  
  
-   Remplacez le champ public par une méthode qui retourne un clone d'un tableau privé.  Votre code ne repose pas sur le clone ; aussi, n'y a\-t\-il aucun danger si les éléments sont modifiés.  
  
 Si vous avez opté pour la deuxième approche, ne remplacez pas le champ par une propriété ; les propriétés qui retournent des tableaux influencent défavorablement les performances.  Pour plus d’informations, consultez [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md).  
  
## Quand supprimer les avertissements  
 L'exclusion d'un avertissement issu de cette règle est fortement déconseillée.  Il n'existe pratiquement aucun scénario dans lequel le contenu d'un champ en lecture seule est d'importance négligeable.  Si c'est le cas dans votre scénario, supprimez le modificateur `readonly` au lieu d'exclure le message.  
  
## Exemple  
 Cet exemple montre les dangers inhérents à la violation de cette règle.  La première partie présente un exemple de bibliothèque dotée d'un type, `MyClassWithReadOnlyArrayField`, contenant deux champs \(`grades` et `privateGrades`\) non sécurisés.  Le champ `grades` est public, et par conséquent vulnérable pour tout appelant.  Le champ `privateGrades` est privé, mais reste vulnérable parce qu'il est retourné aux appelants par la méthode `GetPrivateGrades`.  Le champ `securePrivateGrades` est exposé de manière sûre par la méthode `GetSecurePrivateGrades`.  Il est déclaré comme privé pour respecter des pratiques conceptuelles optimales.  La deuxième partie affiche un code qui modifie des valeurs stockées dans les membres `grades` et `privateGrades`.  
  
 L'exemple de bibliothèque de classes apparaît dans l'exemple suivant.  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## Exemple  
 Le code suivant utilise la bibliothèque de classes exemple pour illustrer les problèmes de sécurité liés aux tableaux en lecture seule.  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 Le résultat généré par cet exemple est le suivant :  
  
  **Avant de manipuler : Notes : 90, 90, 90 Notes Privées : 90, 90, 90 Notes Sécurisées, 90, 90, 90 Après manipulation : Notes : 90, 555, 90 Notes Privées : 90, 555, 90 Notes Sécurisées, 90, 90, 90**   
## Voir aussi  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>