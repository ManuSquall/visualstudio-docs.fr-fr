---
title: 'DA0006 : Remplacer Equals() pour les types valeur | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e30894ec98dd1db4de0b724082467a681a0fa696
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970689"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006 : Remplacer Equals() pour les types valeur

|||
|-|-|
|ID de règle|DA0006|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|Échantillonnage|
|Message|Remplacer Equals et l’opérateur d’égalité pour les types valeur.|
|Type de messages|Warning|

## <a name="cause"></a>Cause
 Les appels à la méthode Equals ou aux opérateurs d’égalité d’un type valeur public représentent une part importante des données de profilage. Implémentez une méthode plus efficace.

## <a name="rule-description"></a>Description de la règle
 Pour les types valeur, l’implémentation héritée de Equals utilise la bibliothèque <xref:System.Reflection> et compare le contenu de tous les champs du type. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.

 Pour plus d’informations sur la façon de remplacer Equals et les opérateurs d’égalité, consultez [Conseils pour l’implémentation de Equals et de l’opérateur d’égalité (==)](http://go.microsoft.com/fwlink/?LinkId=177818).

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Pour obtenir un exemple d’implémentation d’Equals et des opérateurs d’égalité, consultez la règle d’analyse du code [CA1815 : Remplacer Equals et l’opérateur d’égalité dans les types valeur](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)