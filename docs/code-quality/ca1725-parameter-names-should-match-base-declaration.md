---
title: 'CA1725 : Les noms des paramètres doivent correspondre à la déclaration de base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 457051fa9701aac81c92389d6d33e125f5064f1e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873410"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725 : Les noms des paramètres doivent correspondre à la déclaration de base

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’un paramètre dans une substitution de méthode ne correspond pas le nom du paramètre dans la déclaration de base de la méthode ou le nom du paramètre dans la déclaration d’interface de la méthode.

Par défaut, cette règle examine uniquement les méthodes visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, renommez le paramètre pour correspondre à la déclaration de base. Le correctif est une modification avec rupture pour les méthodes visibles par COM.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle à l’exception des méthodes visibles par COM dans les bibliothèques fournies antérieurement.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1725.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (d’affectation de noms). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).