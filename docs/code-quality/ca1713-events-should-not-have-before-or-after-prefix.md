---
title: "CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8dba144740a2a39494323a456cddf90131e35c6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920325"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un événement commence par 'Before' ou 'After'.

## <a name="rule-description"></a>Description de la règle
 Noms d’événements doivent décrire l’action qui déclenche l’événement. Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions. Par exemple, lorsque vous nommez une paire d’événements qui est déclenché lors de la fermeture d’une ressource, vous pouvez le nommer « Fermer » et « Fermé », au lieu de 'BeforeClose' et 'AfterClose'.

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le préfixe de nom de l’événement et envisagez de modifier le nom à utiliser le présent ou passé d’un verbe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.