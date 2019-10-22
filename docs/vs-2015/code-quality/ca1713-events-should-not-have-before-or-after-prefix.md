---
title: 'CA1713 : les événements ne doivent pas avoir le préfixe Before ou after | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7286272e121cf5054013576c4278f787c8423d79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669148"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un événement commence par’before’ou’after'.

## <a name="rule-description"></a>Description de la règle
 Les noms d’événements doivent décrire l’action qui déclenche l’événement. Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions. Par exemple, quand vous nommez une paire d’événements qui est déclenchée lors de la fermeture d’une ressource, vous pouvez la nommer’Closing’et’Closed’au lieu de’BeforeClose’et’AfterClose'.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le préfixe du nom de l’événement et envisagez de modifier le nom pour utiliser le présent ou le passé d’un verbe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.
