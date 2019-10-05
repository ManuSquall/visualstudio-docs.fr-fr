---
title: 'CA2207 : Initialisez les champs statiques des types valeur en ligne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46f579b6776ffab6d0ed3b2e216e29d36d2065ee
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231694"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207 : Initialisez les champs statiques des types valeur en ligne

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type valeur déclare un constructeur statique explicite.

## <a name="rule-description"></a>Description de la règle
Lorsqu’un type valeur est déclaré, il subit une initialisation par défaut où tous les champs de type valeur ont la valeur zéro et tous les champs de type référence ont la valeur `null` (`Nothing` en Visual Basic). L’exécution d’un constructeur statique explicite est garantie uniquement avant l’appel d’un constructeur d’instance ou d’un membre statique du type. Par conséquent, si le type est créé sans appeler un constructeur d’instance, l’exécution du constructeur statique n’est pas garantie.

Si toutes les données statiques sont initialisées inline et qu’aucun constructeur statique explicite n' C# est déclaré, les compilateurs et `beforefieldinit` Visual Basic ajoutent l’indicateur à la définition de la classe MSIL. Les compilateurs ajoutent également un constructeur statique privé qui contient le code d’initialisation statique. Ce constructeur statique privé est garanti s’exécuter avant l’accès à tous les champs statiques du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
[CA1810 Initialiser les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)