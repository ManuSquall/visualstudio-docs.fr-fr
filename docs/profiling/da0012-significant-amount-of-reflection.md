---
title: 'DA0012 : Quantité importante de réflexion | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1c1b96e9a73b488ba9c9920e8ea43e27f78f67ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777671"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012 : Quantité importante de réflexion

|||
|-|-|
|ID de règle|DA0012|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|échantillonnage|
|Message|Vous utilisez trop de réflexion. C’est une opération coûteuse.|
|Type de règle|Avertissement|

## <a name="cause"></a>Cause :
 Les appels aux méthodes System.Reflection, telles que InvokeMember et GetMember, ou aux méthodes de type telles que MemberInvoke, représentent une part importante des données de profilage. Si possible, remplacez ces méthodes par une liaison anticipée aux méthodes des assemblys dépendants.

## <a name="rule-description"></a>Description de la règle
 La réflexion est une fonctionnalité souple du .NET Framework qui peut être utilisée pour créer une liaison tardive entre votre application et un assembly de runtime dépendant, ou pour créer et exécuter dynamiquement de nouveaux types pendant l’exécution. Toutefois, ces techniques peuvent dégrader les performances si elles sont fréquemment utilisées ou appelées dans des boucles serrées.

 Pour plus d’informations, consultez la section [Reflection and Late Binding](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) de la rubrique Chapter 5 — Improving Managed Code Performance qui fait partie de la documentation Improving .NET Application Performance and Scalability, disponible sur le site MSDN, dans la bibliothèque Microsoft Patterns and Practices.

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage. Examinez les fonctions appelantes de la méthode System.Type ou System.Reflection pour rechercher les sections du programme qui utilisent le plus fréquemment les API de réflexion .NET. Évitez d’utiliser des méthodes qui retournent des métadonnées. Si les performances de votre application sont critiques, évitez d’utiliser des liaisons tardives et de créer dynamiquement des types au moment de l’exécution.
