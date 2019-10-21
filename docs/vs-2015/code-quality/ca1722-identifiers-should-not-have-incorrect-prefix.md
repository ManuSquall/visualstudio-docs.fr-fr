---
title: 'Ca1722 : les identificateurs ne doivent pas avoir un préfixe incorrect | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f50c5aca934886f03a54692d98a6be3f8bb5562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671578"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un identificateur a un préfixe incorrect.

## <a name="rule-description"></a>Description de la règle
 Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique.

 Les noms de types n’ont pas de préfixe spécifique et ne doivent pas être précédés de’C'. Cette règle signale des violations pour les noms de types tels que « CMyClass » et ne signale pas de violations pour les noms de types tels que « cache ».

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le préfixe de l’identificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1715 : Les identificateurs doivent avoir un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
