---
title: 'CA1714 : les énumérations d’indicateurs doivent avoir des noms au pluriel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669134"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714 : Les énumérations d'indicateurs doivent avoir des noms au pluriel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une énumération publique a le <xref:System.FlagsAttribute?displayProperty=fullName> et son nom ne se termine pas par’s'.

## <a name="rule-description"></a>Description de la règle
 Les types marqués avec <xref:System.FlagsAttribute> ont des noms au pluriel, car l’attribut indique qu’il est possible de spécifier plusieurs valeurs. Par exemple, une énumération qui définit les jours de la semaine peut être destinée à être utilisée dans une application où vous pouvez spécifier plusieurs jours. Cette énumération doit avoir le <xref:System.FlagsAttribute> et peut être appelée « Days ». Une énumération similaire qui autorise la spécification d’un seul jour n’a pas l’attribut et peut être appelée « Day ».

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Faites du nom de l’énumération un mot pluriel ou supprimez l’attribut <xref:System.FlagsAttribute> si plusieurs valeurs d’énumération ne doivent pas être spécifiées simultanément.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer en toute sécurité une violation si le nom est un mot pluriel, mais qu’il ne se termine pas par' '. Par exemple, si l’énumération de plusieurs jours qui a été décrite précédemment était nommée « DaysOfTheWeek », cela violerait la logique de la règle, mais pas son intention. Ces violations doivent être supprimées.

## <a name="related-rules"></a>Règles associées
 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 [conception d’énumération](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545) <xref:System.FlagsAttribute?displayProperty=fullName>
