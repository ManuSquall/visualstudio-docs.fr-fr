---
title: "CA1720&#160;: Les identificateurs ne doivent pas contenir de noms de types | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1720&#160;: Les identificateurs ne doivent pas contenir de noms de types
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un paramètre dans un membre visible de l'extérieur contient un nom de type de données.  
  
 ou  
  
 Le nom d'un membre visible de l'extérieur contient un nom de type de données propre à un langage.  
  
## Description de la règle  
 Les noms de paramètres et de membres sont plus efficaces pour véhiculer leur signification que pour décrire leur type, qui devrait être fourni par les outils de développement.  Pour les noms de membres, si un nom de type de données doit être utilisé, utilisez un nom indépendant des langages au lieu d'un nom propre à un langage.  Par exemple, au lieu du nom de type C\# 'int', utilisez le nom de type de données indépendant du langage, Int32.  
  
 Chaque jeton discret dans le nom du paramètre ou du membre est vérifié par rapport aux noms de types de données suivants propres au langage, sans respecter la casse :  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Entier  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Non signé  
  
-   Signé  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 En outre, les noms d'un paramètre sont également vérifiés par rapport aux noms de types de données suivants indépendants du langage, sans respecter la casse :  
  
-   Objet  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   Chaîne  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   Pointeur  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## Comment corriger les violations  
 **En cas de déclenchement sur un paramètre :**  
  
 Remplacez l'identificateur de type de données dans le nom du paramètre par un terme qui décrit mieux sa signification ou par un terme plus générique, tel que « valeur ».  
  
 **En cas de déclenchement sur un membre :**  
  
 Remplacez l'identificateur de type de données propre au langage dans le nom du membre par un terme qui décrit mieux sa signification, par un équivalent indépendant du langage ou par un terme plus générique, tel que « valeur ».  
  
## Quand supprimer les avertissements  
 L'utilisation occasionnelle de noms de paramètres et membres fondés sur un type peut être appropriée.  Cependant, dans le cas d'un nouveau développement, aucun scénario connu n'oblige à supprimer un avertissement de cette règle.  Pour des bibliothèques déjà livrées, vous pouvez être amené à supprimer un avertissement de cette règle.  
  
## Règles connexes  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)