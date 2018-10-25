---
title: 'CA2207 : Initialisez les champs statiques de type valeur en ligne | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2833e14c941ae4d2ac6c16f8f5abf625f430de9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890594"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207 : Initialisez les champs static des types valeur en ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



