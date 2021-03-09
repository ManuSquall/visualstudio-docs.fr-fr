---
title: 'DA0010 : GetHashCode coûteux | Microsoft Docs'
description: Les appels à la méthode GetHashCode du type représentent une part importante des données de profilage, ou la méthode alloue de la mémoire.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d44c998cabd3611e2ed393be0ad7df20e1ac49c
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469922"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010 : Fonction GetHashCode coûteuse

|Élément|Valeur|
|-|-|
|ID de règle|DA0010|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|échantillonnage<br /><br /> Mémoire .NET|
|Message|Les fonctions GetHashCode doivent être peu coûteuses et n’allouer aucune mémoire. Réduisez si possible la complexité de la fonction de code de hachage.|
|type de message|Avertissement|

## <a name="cause"></a>Cause
 Les appels à la méthode GetHashCode du type représentent une part importante des données de profilage, ou la méthode alloue de la mémoire.

## <a name="rule-description"></a>Description de la règle
 Le hachage est une technique pour localiser rapidement un élément particulier dans une collection de grande taille. Comme les tables de hachage peuvent être grandes et avoir à supporter des accès à des débits très élevés, elles doivent être efficaces. Une conséquence de cette nécessité est que les méthodes GetHashCode dans le .NET Framework ne doivent pas allouer de mémoire. L’allocation de mémoire augmente la charge sur le récupérateur de mémoire et expose la méthode à des délais potentiels s’il devient nécessaire d’exécuter la garbage collection suite à la demande d’allocation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Simplifiez la méthode.
