---
title: Changer les vagues
description: Découvrez comment activer ou désactiver les fonctionnalités de MSBuild qui sont potentiellement perturbatrices.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 68aafd8ebb97b4bf649cc41eb7739e1700c9cb1a
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94532071"
---
# <a name="change-waves"></a>Changer les vagues

Une *vague de modification* est un ensemble de modifications de comportement dans MSBuild que vous pouvez refuser en spécifiant un indicateur particulier en tant que variable d’environnement. L’objectif est de vous avertir des modifications potentiellement perturbatrices, afin que vous ayez la flexibilité nécessaire pour adapter ces modifications avant qu’elles ne deviennent des fonctionnalités standard. Toutes les fonctionnalités d’une vague de modification spécifique peuvent être activées ou désactivées ensemble, et non individuellement.

Quand vous effectuez une mise à niveau vers une nouvelle version de MSBuild, les modifications potentiellement endommagées sont activées par défaut, mais si une fonctionnalité affecte votre build de manière négative, vous pouvez facilement désactiver cette vague de modifications. Chaque vague de modification est identifiée par un numéro de version MSBuild (par exemple, 16,8), mais la définition de l’onde de modification contrôle uniquement certaines fonctionnalités qui ont le potentiel d’affecter le processus de génération, mais pas toutes les modifications de cette version de MSBuild. Une liste des fonctionnalités de chaque vague de modification apparaît [plus loin dans cet article](#change-waves-and-associated-features). La désactivation d’une onde de modification désactive également les vagues modifiées des versions plus élevées.

## <a name="opt-out-of-change-wave-features"></a>Refuser les fonctionnalités de changement d’onde

Pour désactiver les fonctionnalités dans une vague de modification, définissez la variable `MSBuildDisableFeaturesFromVersion` d’environnement sur la modification Wave (ou la version MSBuild) qui contient la fonctionnalité que vous souhaitez **Désactiver**. Il s’agit de la version de MSBuild pour laquelle les fonctionnalités ont été développées. Consultez le mappage des ondes de modification aux fonctionnalités ci-dessous.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Valeurs MSBuildDisableFeaturesFromVersion

Vous recevrez un avertissement et/ou une valeur par défaut pour une vague spécifique si vous n’avez pas défini `MSBuildDisableFeaturesFromVersion` sur une vague de modification valide. Le tableau suivant répertorie les paramètres possibles :

| Valeur `MSBuildDisableFeaturesFromVersion`                         | Résultats        | Recevoir un avertissement ? |
| :-------------                                                    | :----------   | :----------: |
| Non                                                             | Activez toutes les ondes de modification, ce qui signifie que toutes les fonctionnalités situées derrière chaque onde de modification sont activées.               | Non   |
| Toute vague de modification valide et actuelle (par exemple, `16.8` )                      | Désactivez toutes les fonctionnalités en arrière-plan de la modification Wave `16.8` **et supérieure**.                                           | Non   |
| Valeur non valide (par exemple, `16.9` lorsque les vagues valides sont `16.8` et `16.10` )| Par défaut, la valeur valide la plus proche (croissant). Par exemple, la valeur `16.9` par défaut est `16.10` .               | Non   |
| Hors rotation (par exemple, `17.1` lorsque la vague la plus élevée est `17.0` )      | Attachez à la valeur valide la plus proche. Par exemple, les `17.1` colliers de serrage vers `17.0` `16.5``16.8`                    | Oui  |
| Format non valide (par exemple,, `16x8` `17_0` , `garbage` )                    | Activez toutes les ondes de modification, ce qui signifie que toutes les fonctionnalités situées derrière chaque onde de modification sont activées.               | Oui  |

## <a name="change-waves-and-associated-features"></a>Changer les vagues et les fonctionnalités associées

Les liens de la liste ci-dessous permettent d’accéder à la PR GitHub pour la fonctionnalité.

### <a name="168"></a>16,8

- [Activer nowarn](https://github.com/dotnet/msbuild/pull/5671)
- [Tronquer les messages du journal de la cible/de la tâche ignorés à 1024 caractères](https://github.com/dotnet/msbuild/pull/5553)
- [Ne pas développer le lecteur complet modèles glob avec la fausse condition](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Erreur quand une extension de propriété dans une condition contient des espaces blancs](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Il n’y a pas encore d’entrée dans cette vague de modification.

## <a name="change-waves-that-are-out-of-rotation"></a>Changer les vagues qui ne sont pas en rotation

Il n’y a pas de rotation hors rotation pour l’instant.

## <a name="faq"></a>Questions fréquentes (FAQ)

**Pourquoi cibler la mise en forme de toutes les autres versions pour faire pivoter les vagues ?**

Nous pensons qu’il y a suffisamment de temps pour faire des discussions avec celles qui sont affectées et aider à adapter les modifications.

**Pourquoi une variable d’environnement et non une propriété de projet ?**

Dans certains scénarios, nous voulons placer une fonctionnalité sous une vague de modification avant que MSBuild n’ait chargé le projet. Pour cette raison, les ondes de modification requièrent l’utilisation de variables d’environnement.

**Pourquoi annuler l’abonnement ?**

La désactivation est une meilleure approche pour nous. dans le cas contraire, nous obtenons un feedback limité quand une fonctionnalité a un impact sur les builds des clients.

## <a name="see-also"></a>Voir aussi

- [MSBuild](msbuild.md)
- [Nouveautés dans MSBuild 16](whats-new-msbuild-16-0.md)
