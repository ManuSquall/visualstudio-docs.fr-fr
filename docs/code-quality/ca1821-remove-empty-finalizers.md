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
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921372"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimez les finaliseurs vides

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Catégorie|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type implémente un finaliseur vide, appelle uniquement le finaliseur de type de base ou appelle uniquement des méthodes émises de manière conditionnelle.

## <a name="rule-description"></a>Description de la règle
Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Le garbage collector exécutera le finaliseur avant de collecter l’objet. Cela signifie que deux collections seront nécessaires pour collecter l’objet. Un finaliseur vide entraîne cette surcharge ajoutée sans aucun avantage.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Supprimez le finaliseur vide. Si un finaliseur est requis pour le débogage, mettez l’ensemble du finaliseur `#if DEBUG / #endif` dans des directives.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un message de cette règle. L’impossibilité de supprimer la finalisation diminue les performances et n’offre aucun avantage.

## <a name="example"></a>Exemple
L’exemple suivant montre un finaliseur vide qui doit être supprimé, un finaliseur qui doit être placé dans `#if DEBUG / #endif` les directives et un finaliseur qui utilise correctement `#if DEBUG / #endif` les directives.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]