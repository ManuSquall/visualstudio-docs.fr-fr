---
title: 'CA1714 : Les noms des enums Flags doivent être au pluriel'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 512e66c65cb3abd0b5e56f268b9a89e4d51758bf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953904"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714 : Les noms des enums Flags doivent être au pluriel

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une énumération publique comporte le <xref:System.FlagsAttribute?displayProperty=fullName> et son nom ne se termine pas in'.

## <a name="rule-description"></a>Description de la règle
 Les types marqués avec <xref:System.FlagsAttribute> ont des noms au pluriel, car l’attribut indique que plusieurs valeurs peuvent être spécifiées. Par exemple, une énumération qui définit les jours de la semaine peut être conçue pour une utilisation dans une application dans laquelle vous pouvez spécifier plusieurs jours. Cette énumération doit avoir le <xref:System.FlagsAttribute> et peut être appelée 'Jours'. Une énumération semblable qui permet uniquement à un jour d’être spécifié n’a pas l’attribut et peut être appelée « Day ».

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Vérifiez le nom de l’énumération un mot au pluriel, ou supprimez la <xref:System.FlagsAttribute> attribut si plusieurs valeurs d’énumération ne doivent pas être spécifiées simultanément.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer une violation si le nom est un mot au pluriel mais ne pas se termine sans de ». Par exemple, si l’énumération de plusieurs jours qui a été décrite ont été précédemment nommée « DaysOfTheWeek », cela risque de violer la logique de la règle, mais pas son intention. Ces violations doivent être supprimées.

## <a name="related-rules"></a>Règles associées
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Conception d’énumérations](/dotnet/standard/design-guidelines/enum)