---
title: 'CA1822 : marquer les membres comme static | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2416eb24c21ef0e61bdb6db3de66c892e1eb699f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545338"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822 : Marquez les membres comme static
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1822 : marquer les membres comme statiques](/visualstudio/code-quality/ca1822-mark-members-as-static).

|Élément|Valeur|
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture : si le membre n’est pas visible à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br /><br /> Sans rupture : Si vous changez simplement le membre en membre d’instance avec le `this` mot clé.<br /><br /> Avec rupture : Si vous remplacez le membre d’un membre d’instance par un membre statique et qu’il est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Un membre qui n’accède pas aux données d’instance n’est pas marqué comme static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Description de la règle
 Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. L’émission de sites d’appel non virtuels empêche une vérification au moment de l’exécution pour chaque appel qui garantit que le pointeur d’objet actuel n’est pas null. Cela permet d’obtenir un gain de performances mesurable pour le code dépendant des performances. Dans certains cas, l’échec de l’accès à l’instance d’objet actuelle représente un problème d’exactitude.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Marquez le membre comme static (ou Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) ou utilisez’This'/'me’dans le corps de la méthode, le cas échéant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle pour le code précédemment expédié pour lequel le correctif serait une modification avec rupture.

## <a name="related-rules"></a>Règles associées
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
