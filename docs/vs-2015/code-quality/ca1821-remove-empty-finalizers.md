---
title: 'CA1821 : Supprimez les finaliseurs vides | Microsoft Docs'
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
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8abb9f00e61c8c24e91921519c706356b6ded16c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589762"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimer les finaliseurs vides
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1821 : supprimez les finaliseurs vides](https://docs.microsoft.com/visualstudio/code-quality/ca1821-remove-empty-finalizers).

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

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



