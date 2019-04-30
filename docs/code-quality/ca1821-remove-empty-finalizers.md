---
title: 'CA1821 : Supprimez les finaliseurs vides'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16bb2786c4c7b0ca94fe60a9577e4b462d663bfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545711"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimez les finaliseurs vides

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type implémente un finaliseur qui est vide, appelle uniquement le finaliseur du type de base ou appelle uniquement émises sous certaines conditions de méthodes.

## <a name="rule-description"></a>Description de la règle
 Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Le garbage collector exécutera le finaliseur avant de collecter l’objet. Cela signifie que deux collections sera nécessaire pour collecter l’objet. Un finaliseur vide entraîne cette charge supplémentaire sans aucun avantage.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le finaliseur vide. Si un finaliseur est requis pour le débogage, insérez-le entièrement dans `#if DEBUG / #endif` directives.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un message à partir de cette règle. Échec de supprimer la finalisation diminue les performances et ne présente aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre un finaliseur vide qui doit être supprimé, un finaliseur qui doit être placé dans `#if DEBUG / #endif` directives et un finaliseur qui utilise le `#if DEBUG / #endif` directives correctement.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]