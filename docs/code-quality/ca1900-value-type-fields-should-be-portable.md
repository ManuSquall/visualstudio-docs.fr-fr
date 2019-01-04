---
title: 'CA1900 : Champs de type valeur doivent être portables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ffac1cca87f3b1cbed23e2bbc8a9b463cd4adc6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987847"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900 : Champs de type valeur doivent être portables

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Category|Microsoft.Portability|
|Modification avec rupture|Avec rupture - Si le champ peut être visible en dehors de l’assembly.<br /><br /> Sans rupture - Si le champ n’est pas visible en dehors de l’assembly.|

## <a name="cause"></a>Cause
 Cette règle vérifie que les structures déclarées avec une disposition explicite seront aligneront correctement lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 64 bits. IA-64 n’autorise pas les accès mémoire non alignés et le processus se bloquera si cette violation n’est pas résolue.

## <a name="rule-description"></a>Description de la règle
 Structures qui ont une disposition explicite qui contient des champs non alignés provoquent des pannes sur les systèmes d’exploitation 64 bits.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Tous les champs qui sont inférieures à 8 octets doivent avoir les décalages qui sont un multiple de leur taille et les champs qui sont de 8 octets ou plus doivent avoir des offsets qui sont un multiple de 8. Une autre solution consiste à utiliser `LayoutKind.Sequential` au lieu de `LayoutKind.Explicit`, s’il est raisonnable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cet avertissement doit être supprimé uniquement s’il se produit dans l’erreur.