---
title: 'CA1048 : ne pas déclarer les membres virtuels dans les types sealed | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546794"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048 : Ne pas déclarer les membres virtuels dans les types sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public est sealed et déclare une méthode qui est à la fois `virtual` ( `Overridable` en Visual Basic) et non final. Cette règle ne signale pas de violations pour les types délégués, qui doivent suivre ce modèle.

## <a name="rule-description"></a>Description de la règle
 Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, vous ne pouvez pas hériter d’un type sealed, ce qui rend inutile une méthode virtuelle sur un type sealed.

 Les compilateurs .NET et C# Visual Basic ne permettent pas aux types de violer cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou rendez le type héritable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Le fait de laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
