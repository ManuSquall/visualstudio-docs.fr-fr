---
title: 'CA1823 : Évitez les champs privés inutilisés | Microsoft Docs'
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
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfe51ab6c163c82d413c5c7cc74edc0b980abd85
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47516897"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823 : Évitez les champs privés inutilisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1823 : Évitez les champs privés inutilisés](https://docs.microsoft.com/visualstudio/code-quality/ca1823-avoid-unused-private-fields).

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Cette règle est signalée lorsqu’un champ privé dans votre code existe mais n’est pas utilisé par n’importe quel chemin d’accès du code.

## <a name="rule-description"></a>Description de la règle
 Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le champ ou ajouter du code qui l’utilise.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)



