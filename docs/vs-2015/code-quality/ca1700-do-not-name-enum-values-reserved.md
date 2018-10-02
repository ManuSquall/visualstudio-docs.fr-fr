---
title: 'CA1700 : Ne nommez pas les valeurs enum &#39;réservé&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7aaab7f774b274b9e70efac404d1ab4ba3315d93
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590293"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700 : Ne nommez pas les valeurs enum &#39;réservé&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39;](https://docs.microsoft.com/visualstudio/code-quality/ca1700-do-not-name-enum-values-reserved).

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre d’énumération contient le mot « réservés ».

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture. Vous ne devriez pas aux utilisateurs d’ignorer un membre, car son nom contient « réservés », ni compter sur les utilisateurs de lire ou de vous conformer à la documentation. En outre, étant donné que les membres réservés apparaissent dans les explorateurs d’objets et des environnements de développement intégré intelligents, ils peuvent provoquer confusion sur les membres sont réellement utilisés.

 Au lieu d’utiliser un membre réservé, ajoutez un nouveau membre à l’énumération dans la version futures. Dans la plupart des cas l’ajout du nouveau membre n’est pas une modification avec rupture, tant que l’ajout ne provoque pas les valeurs des membres d’origine à modifier.

 Un nombre limité de cas de l’ajout d’un membre est une modification avec rupture, même si les membres d’origine conservent leurs valeurs d’origine. Principalement, le nouveau membre ne peut pas être retourné à partir de chemins de code existant sans arrêter les appelants qui utilisent une `switch` (`Select` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) instruction sur la valeur de retour qui comprend la liste intégrale des membres et qui lève une exception dans le cas par défaut. Un problème secondaire est que le code client peut ne pas gérer le changement de comportement à partir de méthodes de réflexion comme <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. En conséquence, si le nouveau membre doit être retourné à partir de méthodes existantes ou si une incompatibilité d’application connue se produit en raison de l’utilisation médiocre de la réflexion, la seule solution sans rupture consiste à :

1.  Ajouter une nouvelle énumération qui contient les membres d’origine et nouvelles.

2.  Marquez l’énumération d’origine avec le <xref:System.ObsoleteAttribute?displayProperty=fullName> attribut.

 Suivez la même procédure pour les types visibles de l’extérieur ou les membres qui exposent l’énumération d’origine.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez ou renommez le membre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle pour un membre qui est actuellement utilisé ou pour les bibliothèques fournies antérieurement.

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028 : Le stockage de l’énumération doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008 : Les énumérations doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)



