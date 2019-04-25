---
title: 'CA1002 : N’exposez pas de listes génériques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 77b50f5511f76cceda1827d2a36db7514daa6bea
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076014"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002 : Ne pas exposer de listes génériques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type contient un membre extérieurement visible est un <xref:System.Collections.Generic.List%601?displayProperty=fullName> type, retourne un <xref:System.Collections.Generic.List%601?displayProperty=fullName> type, ou dont la signature inclut un <xref:System.Collections.Generic.List%601?displayProperty=fullName> paramètre.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> est une collection générique qui est conçue pour les performances et non l’héritage. <xref:System.Collections.Generic.List%601?displayProperty=fullName> ne contient pas de membres virtuels qui le rendent plus facile de modifier le comportement d’une classe héritée. Les collections génériques suivantes sont conçues pour l’héritage et doivent être exposées au lieu de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le <xref:System.Collections.Generic.List%601?displayProperty=fullName> type à une des collections génériques qui est conçu pour l’héritage.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement de cette règle, sauf si l’assembly qui déclenche cet avertissement n’est pas destiné à être une bibliothèque réutilisable. Par exemple, il serait possible de supprimer cet avertissement dans une application de paramétrer des performances sans où un gain de performances a été acquise à partir de l’utilisation de listes génériques.

## <a name="related-rules"></a>Règles associées
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Collections doivent implémenter l’interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser des instances du Gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des classes génériques le cas échéant](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
