---
title: 'CA1726 : Utilisez les termes par défaut'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f359f7aa24ada0edf2c98a7d527ed715df85086
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233922"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726 : Utilisez les termes par défaut

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Category|Microsoft.Naming|
|Modification avec rupture|Avec rupture : en cas de déclenchement sur les assemblys<br /><br /> Sans rupture-en cas de déclenchement sur les paramètres de type|

## <a name="cause"></a>Cause

Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Ou, le nom comprend l’indicateur de terme ou les indicateurs.

## <a name="rule-description"></a>Description de la règle

Cette règle analyse un identificateur dans des jetons. Chaque jeton unique et chaque combinaison de jetons doubles contigus sont comparés aux termes intégrés à la règle et à la section dépréciée de tous les dictionnaires personnalisés. Le tableau suivant présente les termes intégrés à la règle et leurs alternatives préférées.

|Terme obsolète|Terme préféré|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` ou `Flags`|Il n’y a aucun terme de remplacement. Ne pas utiliser.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez le terme par le terme de remplacement par défaut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un avertissement de cette règle uniquement si le nom de l’identificateur est intentionnel et s’applique spécifiquement au terme d’origine au lieu du terme préféré.

## <a name="related-rules"></a>Règles associées
[Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)