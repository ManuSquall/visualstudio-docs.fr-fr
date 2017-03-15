---
title: "CA1028&#160;: Enum Storage doit &#234;tre Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1028&#160;: Enum Storage doit &#234;tre Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le type sous\-jacent d'une énumération publique n'est pas <xref:System.Int32?displayProperty=fullName>.  
  
## Description de la règle  
 Une énumération est un type valeur qui définit un jeu de constantes nommées associées.  Par défaut, le type de données <xref:System.Int32?displayProperty=fullName> est utilisé pour stocker la valeur de constante.  Bien que vous puissiez modifier ce type sous\-jacent, ce n'est ni nécessaire, ni recommandé dans la plupart des scénarios.  Remarquez que l'utilisation d'un type de données plus petit que <xref:System.Int32> n'entraîne aucun gain de performance significatif.  Si vous ne pouvez pas utiliser le type de données par défaut, vous devez utiliser l'un des types intégraux conformes CLS \(Common Language System\), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> ou <xref:System.Int64>, afin de garantir que toutes les valeurs de l'énumération peuvent être représentées dans des langages de programmation conformes CLS.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, à moins qu'il y ait des problèmes de compatibilité ou de taille, utilisez <xref:System.Int32>.  Dans les situations où <xref:System.Int32> n'est pas assez grand pour contenir les valeurs, utilisez <xref:System.Int64>.  Si la compatibilité descendante requiert un type de données plus petit, utilisez <xref:System.Byte> ou <xref:System.Int16>.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement si des problèmes de compatibilité descendante le requièrent.  Dans les applications, la non\-conformité à cette règle ne provoque généralement aucun problème.  Dans les bibliothèques où l'interopérabilité des langages est requise, la non\-conformité à cette règle peut avoir une incidence négative sur vos utilisateurs.  
  
## Exemple de violation  
  
### Description  
 L'exemple suivant présente deux énumérations qui n'utilisent pas le type de données sous\-jacent recommandé.  
  
### Code  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Exemple de résolution  
  
### Description  
 L'exemple suivant corrige la violation précédente en modifiant le type de données sous\-jacent en <xref:System.Int32>.  
  
### Code  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Règles connexes  
 [CA1008 : Les enums doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## Voir aussi  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>