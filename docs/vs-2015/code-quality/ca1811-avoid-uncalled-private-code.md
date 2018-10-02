---
title: 'CA1811 : Évitez le recours à du code privé | Microsoft Docs'
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
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2f08d3fe31d6a314de9bc64441add64246f8e256
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590060"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811 : Évitez le recours à du code privé non appelé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1811 : Évitez le recours à du code privé](https://docs.microsoft.com/visualstudio/code-quality/ca1811-avoid-uncalled-private-code).

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Membre privé ou interne (de niveau assembly) n’a pas d’appelants dans l’assembly n’est pas appelé par le common language runtime et n’est pas appelé par un délégué. Les membres suivants ne sont pas vérifiés par cette règle :

-   Membres d’interface explicite.

-   Constructeurs statiques.

-   Constructeurs de sérialisation.

-   Les méthodes marquées avec <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Membres qui sont des remplacements.

## <a name="rule-description"></a>Description de la règle
 Cette règle peut rapporter des faux positifs si les points d’entrée produisent, qui ne sont pas identifiées par la logique de règle. En outre, un compilateur peut émettre du code ne pouvant être appelé dans un assembly.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le code ne pouvant être appelé ou ajouter du code qui l’appelle.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)



