---
title: 'CA1048 : Ne déclarez pas de membres virtuels dans les types sealed | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3ff0bb128c72f5483c9169a98c6fc41ec3057e54
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589746"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048 : Ne pas déclarer les membres virtuels dans les types sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1048 : ne déclarez pas de membres virtuels dans les types sealed](https://docs.microsoft.com/visualstudio/code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types).

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public est sealed et déclare une méthode qui est à la fois `virtual` (`Overridable` en Visual Basic) et non finale. Cette règle ne signale pas de violations pour les types délégués, qui doivent respecter ce modèle.

## <a name="rule-description"></a>Description de la règle
 Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, vous ne peut pas hériter d’un type sealed, effectuer une méthode virtuelle sur un type sealed sans signification.

 Les compilateurs c# et Visual Basic .NET n’autorisent pas les types de violer cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou rendez le type pouvant être héritées.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]



