---
title: 'CA1726 : utiliser les termes préférés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 639a42e26442e31f7bbbbb2245af0289c6a04fd8
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918222"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726 : Utilisez les termes par défaut
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1726 : utiliser les termes préférés](/visualstudio/code-quality/ca1726-use-preferred-terms).

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Catégorie|Microsoft.Naming|
|Modification avec rupture|Avec rupture : en cas de déclenchement sur les assemblys<br /><br /> Sans rupture-en cas de déclenchement sur les paramètres de type|

## <a name="cause"></a>Cause
 Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Le nom comprend également l’indicateur de terme ou les indicateurs.

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
