---
title: 'CA1821 : supprimer les finaliseurs vides | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545351"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimez les finaliseurs vides
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un type implémente un finaliseur vide, appelle uniquement le finaliseur de type de base ou appelle uniquement des méthodes émises de manière conditionnelle.

## <a name="rule-description"></a>Description de la règle
 Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Le garbage collector exécutera le finaliseur avant de collecter l’objet. Cela signifie que deux collections seront nécessaires pour collecter l’objet. Un finaliseur vide entraîne cette surcharge ajoutée sans aucun avantage.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le finaliseur vide. Si un finaliseur est requis pour le débogage, mettez l’ensemble du finaliseur dans des `#if DEBUG / #endif` directives.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un message de cette règle. L’impossibilité de supprimer la finalisation diminue les performances et n’offre aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre un finaliseur vide qui doit être supprimé, un finaliseur qui doit être placé dans `#if DEBUG / #endif` les directives et un finaliseur qui utilise `#if DEBUG / #endif` correctement les directives.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
