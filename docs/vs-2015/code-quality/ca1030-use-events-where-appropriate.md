---
title: 'CA1030 : utiliser des événements lorsque cela est approprié | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661922"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030 : Utiliser des événements lorsque cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le nom d’une méthode publique, protégée ou privée commence par l’un des éléments suivants :

- Additionnelle

- RemoveOn

- Flammes

- Génère

## <a name="rule-description"></a>Description de la règle
 Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Les événements suivent le modèle de conception observateur ou publication-abonnement. ils sont utilisés lorsqu’un changement d’État dans un objet doit être communiqué à d’autres objets. Si une méthode est appelée en réponse à une modification d’état clairement définie, la méthode doit être appelée par un gestionnaire d’événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode.

 Des exemples courants d’événements se trouvent dans les applications de l’interface utilisateur, où une action de l’utilisateur, telle qu’un clic sur un bouton, entraîne l’exécution d’un segment de code. Le modèle d’événement [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] n’est pas limité aux interfaces utilisateur ; elle doit être utilisée partout où vous devez communiquer des modifications d’État à un ou plusieurs objets.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si la méthode est appelée lorsque l’état d’un objet change, vous devez envisager de modifier la conception pour utiliser le modèle d’événement [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si la méthode ne fonctionne pas avec le modèle d’événement [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
