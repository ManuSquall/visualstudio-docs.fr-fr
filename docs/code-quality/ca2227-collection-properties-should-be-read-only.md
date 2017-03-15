---
title: "CA2227&#160;: Les propri&#233;t&#233;s de collection doivent &#234;tre en lecture seule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2227&#160;: Les propri&#233;t&#233;s de collection doivent &#234;tre en lecture seule
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une propriété accessible en écriture extérieurement visible est un type qui implémente <xref:System.Collections.ICollection?displayProperty=fullName>.  Les tableaux, les indexeurs \(propriétés portant le nom 'Item'\) et les jeux d'autorisations sont ignorés par la règle.  
  
## Description de la règle  
 Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente.  Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d'être définis.  Si le remplacement de la collection est un objectif, le schéma de conception recommandé consiste à inclure une méthode pour supprimer tous les éléments de la collection et une méthode pour remplir de nouveau la collection.  Consultez les méthodes <xref:System.Collections.ArrayList.Clear%2A> et <xref:System.Collections.ArrayList.AddRange%2A> de la classe <xref:System.Collections.ArrayList?displayProperty=fullName> pour obtenir un exemple de ce schéma.  
  
 Les sérialisations binaire et XML prennent en charge les propriétés en lecture seule qui sont des collections.  La classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> a des conditions requises spécifiques pour les types pour qui implémentent <xref:System.Collections.ICollection> et <xref:System.Collections.IEnumerable?displayProperty=fullName> afin d'être sérialisables.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la propriété accessible en lecture seule et, si la conception le requiert, ajoutez des méthodes pour vider et remplir de nouveau la collection.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant montre un type avec une propriété de collection accessible en écriture et comment la collection peut être directement remplacée.  En outre, il montre la meilleure manière de remplacer une propriété de collection en lecture seule à l'aide des méthodes `Clear` et `AddRange`.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Règles connexes  
 [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)