---
title: 'CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545650"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre de l’énumération contient le mot « reserved ».

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture. Vous ne devez pas vous attendre à ce que les utilisateurs ignorent un membre uniquement parce que son nom contient « réservé », et que vous ne pouvez pas compter sur les utilisateurs pour lire ou respecter la documentation. En outre, étant donné que les membres réservés apparaissent dans les explorateurs d’objets et les environnements de développement intégré de manière intelligente, ils peuvent provoquer une confusion quant aux membres qui sont réellement utilisés.

 Au lieu d’utiliser un membre réservé, ajoutez un nouveau membre à l’énumération dans la version future. Dans la plupart des cas, l’ajout du nouveau membre n’est pas une modification avec rupture, à condition que l’ajout n’entraîne pas la modification des valeurs des membres d’origine.

 Dans un nombre limité de cas, l’ajout d’un membre est une modification avec rupture même lorsque les membres d’origine conservent leurs valeurs d’origine. En premier lieu, le nouveau membre ne peut pas être retourné à partir de chemins de code existants sans arrêter les appelants qui utilisent une `switch` `Select` instruction (dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) sur la valeur de retour qui englobe l’ensemble de la liste de membres et qui lèvent une exception dans le cas par défaut. Une préoccupation secondaire est que le code client ne peut pas gérer la modification du comportement à partir de méthodes de réflexion telles que <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . En conséquence, si le nouveau membre doit être retourné à partir de méthodes existantes ou si une incompatibilité d’application connue se produit en raison d’une mauvaise utilisation de la réflexion, la seule solution sans rupture consiste à :

1. Ajoutez une nouvelle énumération qui contient les membres originaux et nouveaux.

2. Marquez l’énumération d’origine avec l' <xref:System.ObsoleteAttribute?displayProperty=fullName> attribut.

   Suivez la même procédure pour tous les types ou membres visibles de l’extérieur qui exposent l’énumération d’origine.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez ou renommez le membre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle pour un membre actuellement utilisé ou pour les bibliothèques qui ont déjà été expédiées.

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028 : Enum Storage doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008 : Les enums doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
