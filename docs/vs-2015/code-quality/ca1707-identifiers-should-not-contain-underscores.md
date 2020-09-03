---
title: 'CA1707 : les identificateurs ne doivent pas contenir de traits de soulignement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544025"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1707 : les identificateurs ne doivent pas contenir de traits de soulignement](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|Élément|Valeur|
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft. Naming|
|Modification avec rupture|Avec rupture-en cas de déclenchement sur les assemblys<br /><br /> Sans rupture-en cas de déclenchement sur les paramètres de type|

## <a name="cause"></a>Cause
 Le nom d’un identificateur contient le caractère de soulignement (_).

## <a name="rule-description"></a>Description de la règle
 Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). La règle vérifie les espaces de noms, les types, les membres et les paramètres.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez tous les traits de soulignement du nom.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
