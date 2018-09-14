---
title: 'CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bcb0bfe07c9e9fb843ea6c7a0960b96cc09339b9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549454"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un identificateur a un préfixe incorrect.

## <a name="rule-description"></a>Description de la règle
 Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique.

 Noms de types n’ont pas d’un préfixe spécifique et ne doivent pas être préfixés par un « C ». Cette règle signale les violations pour les noms de types tels que 'CMyClass' et ne signale pas de violations pour les noms de types tels que « Cache ».

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cette cohérence réduit la courbe d’apprentissage qui a requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le préfixe de l’identificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1715 : Les identificateurs doivent avoir un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)