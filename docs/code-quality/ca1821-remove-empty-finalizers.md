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
ms.openlocfilehash: a93ebea78c9258667d7c6ca10e35d22fc4113f48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233439"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimez les finaliseurs vides

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type implémente un finaliseur vide, appelle uniquement le finaliseur de type de base ou appelle uniquement des méthodes émises de manière conditionnelle.

## <a name="rule-description"></a>Description de la règle

À chaque fois que vous le pouvez, évitez les finaliseurs en raison de la surcharge de performances supplémentaire qui est impliquée dans le suivi de la durée de vie des objets. Le garbage collector exécute le finaliseur avant de collecter l’objet. Cela signifie qu’au moins deux collections sont requises pour collecter l’objet. Un finaliseur vide entraîne cette surcharge ajoutée sans aucun avantage.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Supprimez le finaliseur vide. Si un finaliseur est requis pour le débogage, mettez l’ensemble du finaliseur `#if DEBUG / #endif` dans des directives.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un message de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre un finaliseur vide qui doit être supprimé, un finaliseur qui doit être placé dans `#if DEBUG / #endif` les directives et un finaliseur qui utilise correctement `#if DEBUG / #endif` les directives.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
