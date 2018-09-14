---
title: 'CA2207 : Initialisez les champs static des types valeur en ligne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5730acf02cf12dce6d98e7cbd1b6f38f7ece05e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550568"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207 : Initialisez les champs static des types valeur en ligne
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type valeur déclare un constructeur statique explicite.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un type valeur est déclaré, il subit une initialisation par défaut où tous les champs de type de valeur sont définies à zéro et tous les champs de type référence sont définies `null` (`Nothing` en Visual Basic). Un constructeur statique explicite est garanti uniquement à exécuter avant le constructeur d’instance ou un membre statique du type est appelé. Par conséquent, si le type est créé sans appeler un constructeur d’instance, le constructeur statique n’est pas garanti pour exécuter.

 Si toutes les données statiques sont initialisées inline et aucun constructeur statique explicite n’est déclaré, les compilateurs c# et Visual Basic ajoutent le `beforefieldinit` indicateur pour la définition de classe MSIL. Les compilateurs ajoutent également un constructeur statique privé qui contient le code d’initialisation statique. Ce constructeur statique privé est garanti à exécuter avant que tous les champs statiques du type sont accessibles.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle initialiser toutes les données statiques lorsqu’il est déclaré et supprimez le constructeur statique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)