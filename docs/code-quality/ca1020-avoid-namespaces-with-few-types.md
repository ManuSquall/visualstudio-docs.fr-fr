---
title: 'CA1020 : Éviter les espaces de noms comportant peu de types'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c7aae7f5db19a8f72a0d4670727dbf787cf228e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31896489"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020 : Éviter les espaces de noms comportant peu de types
|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un espace de noms autre que l’espace de noms global contient moins de cinq types.

## <a name="rule-description"></a>Description de la règle
 Assurez-vous que chacun de vos espaces de noms bénéficie d’une organisation logique, et qu’une raison valide justifie pour placer des types dans un espace de noms peu rempli. Espaces de noms doit contenir des types qui sont utilisées ensemble dans la plupart des scénarios. Lorsque leurs applications sont mutuellement exclusives, les types doivent se trouver dans les espaces de noms distincts. Par exemple, le <xref:System.Web.UI> espace de noms contient des types qui sont utilisés dans les applications Web, et le <xref:System.Windows.Forms> espace de noms contient des types qui sont utilisés dans [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-en fonction des applications. Même si les deux espaces de noms possèdent des types qui contrôlent les aspects de l’interface utilisateur, ces types ne sont pas conçus pour une utilisation dans la même application. Par conséquent, ils se trouvent dans les espaces de noms distincts. Organisation de l’espace de noms peut également être utile, car elle augmente la détectabilité d’une fonctionnalité prudent. En examinant la hiérarchie de l’espace de noms, les consommateurs de la bibliothèque doivent être en mesure de localiser les types qui implémentent une fonctionnalité.

> [!NOTE]
>  Autorisations et les types au moment du design ne doivent pas être fusionnées dans d’autres espaces de noms pour se conformer à cette règle. Ces types appartiennent à leurs propres espaces de noms sous votre espace de noms principal et les espaces de noms doit se terminer dans `.Design` et `.Permissions`, respectivement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, essayez d’associer les espaces de noms qui contiennent des quelques types dans un espace de noms.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque l’espace de noms ne contient pas de types qui sont utilisés avec les types dans vos autres espaces de noms.