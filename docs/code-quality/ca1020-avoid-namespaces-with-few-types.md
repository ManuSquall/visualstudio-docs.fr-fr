---
title: 'CA1020 : Éviter les espaces de noms comportant peu de types'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236230"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020 : Éviter les espaces de noms comportant peu de types

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un espace de noms autre que l’espace de noms global contient moins de cinq types.

## <a name="rule-description"></a>Description de la règle

Assurez-vous que chacun de vos espaces de noms a une organisation logique, et qu’il existe une raison valable pour placer les types dans un espace de noms peu rempli. Les espaces de noms doivent contenir des types qui sont utilisés ensemble dans la plupart des scénarios. Lorsque leurs applications sont mutuellement exclusives, les types doivent se trouver dans des espaces de noms distincts. Par exemple, l' <xref:System.Web.UI> espace de noms contient des types utilisés dans les applications Web, <xref:System.Windows.Forms> et l’espace de noms contient des [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]types utilisés dans des applications basées sur. Même si les deux espaces de noms ont des types qui contrôlent les aspects de l’interface utilisateur, ces types ne sont pas conçus pour être utilisés dans la même application. Par conséquent, ils se trouvent dans des espaces de noms distincts. L’organisation de l’espace de noms avec prudence peut également être utile, car elle augmente la détectabilité d’une fonctionnalité. En examinant la hiérarchie des espaces de noms, les consommateurs de bibliothèques doivent être en mesure de localiser les types qui implémentent une fonctionnalité.

> [!NOTE]
> Les types et autorisations au moment du design ne doivent pas être fusionnés dans d’autres espaces de noms pour se conformer à cette instruction. Ces types appartiennent à leurs propres espaces de noms sous votre espace de noms principal, et les espaces de `.Design` noms `.Permissions`doivent se terminer par et, respectivement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, essayez de combiner des espaces de noms qui contiennent seulement quelques types dans un espace de noms unique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle lorsque l’espace de noms ne contient pas les types utilisés avec les types dans vos autres espaces de noms.