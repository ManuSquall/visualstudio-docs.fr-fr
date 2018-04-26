---
title: 'CA1822 : Marquez les membres comme static'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822 : Marquez les membres comme static
|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture - Si le membre n’est pas visible à l’extérieur de l’assembly, quelle que soit la modification vous apporter. Sans rupture - Si vous remplacez simplement le membre à un membre d’instance avec le `this` (mot clé).<br /><br /> Avec rupture - Si vous modifiez le membre à partir d’un membre d’instance à un membre statique, et il est visible en dehors de l’assembly.|

## <a name="cause"></a>Cause
 Un membre qui n’accèdent pas aux données d’instance n’est pas marqué comme static (Shared dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Description de la règle
 Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. L’émission de sites d’appel non virtuels empêche une vérification à l’exécution pour chaque appel qui permet de s’assurer que le pointeur d’objet actuel est non null. Cela permet de garantir un gain de performances mesurable pour le code dépendant des performances. Dans certains cas, l’échec d’accès de l’instance d’objet actuelle représente un problème d’exactitude.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Marquez le membre comme static (ou Shared dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou utilisez 'this' / 'Me' dans la méthode corps, si nécessaire.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle d’un code précédemment livré pour lequel le correctif constituerait une modification avec rupture.

## <a name="related-rules"></a>Règles associées
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)