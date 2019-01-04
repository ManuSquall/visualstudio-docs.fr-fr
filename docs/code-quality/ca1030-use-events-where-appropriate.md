---
title: 'CA1030 : Utiliser des événements appropriés'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 445330d654e870fe12aa2ca19626377972235eac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860804"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030 : Utiliser des événements appropriés

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un nom de la méthode publique, protégée ou privée commence par l’une des opérations suivantes :

- Composant additionnel

- RemoveOn

- Incendie

- Raise

## <a name="rule-description"></a>Description de la règle
 Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Événements suivent le modèle de design observateur ou publier / abonner ; ils sont utilisés lorsqu’un changement d’état dans un objet doit être communiqué à d’autres objets. Si une méthode est appelée en réponse à un changement d’état clairement définie, la méthode doit être appelée par un gestionnaire d’événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode.

 Voici quelques exemples courants d’événements sont trouvent dans des applications d’interface utilisateur où une action de l’utilisateur comme un clic sur un bouton provoque un segment de code à exécuter. Le modèle d’événement .NET Framework n’est pas limité aux interfaces utilisateur ; Il doit être utilisé partout où que vous devez communiquer l’état passe à un ou plusieurs objets.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si la méthode est appelée lorsque l’état d’un objet change, vous devez envisager de modifier la conception pour utiliser le modèle d’événement .NET Framework.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si la méthode ne fonctionne pas avec le modèle d’événement .NET Framework.