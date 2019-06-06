---
title: 'CA1030 : Utiliser des événements lorsque cela est approprié'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a3d2ef30018c7fe57f1e7d728ba1dd152f56f5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714296"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030 : Utiliser des événements lorsque cela est approprié

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un nom de la méthode commence par l’une des opérations suivantes :

- AddOn
- RemoveOn
- Incendie
- Raise

Par défaut, cette règle examine uniquement les méthodes visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Événements suivent le modèle de design observateur ou publier / abonner ; ils sont utilisés lorsqu’un changement d’état dans un objet doit être communiqué à d’autres objets. Si une méthode est appelée en réponse à un changement d’état clairement définie, la méthode doit être appelée par un gestionnaire d’événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode.

Voici quelques exemples courants d’événements sont trouvent dans des applications d’interface utilisateur où une action de l’utilisateur comme un clic sur un bouton provoque un segment de code à exécuter. Le modèle d’événement .NET n’est pas limité aux interfaces utilisateur. Il doit être utilisé partout où que vous devez communiquer l’état passe à un ou plusieurs objets.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Si la méthode est appelée lorsque l’état d’un objet change, envisagez de modifier la conception pour utiliser le modèle d’événement .NET.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle si la méthode ne fonctionne pas avec le modèle d’événement .NET.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).
