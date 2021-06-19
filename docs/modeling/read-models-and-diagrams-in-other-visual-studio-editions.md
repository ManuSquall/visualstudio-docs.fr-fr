---
title: Lire des modèles et des diagrammes dans d'autres éditions de Visual Studio
description: En savoir plus sur la lecture de modèles et de diagrammes dans Visual Studio, ainsi que sur le comportement en lecture seule lors de l’utilisation d’une version de Visual Studio qui ne prend pas en charge la création de modèles.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95fbf6451a3f07581ff2bdb098428f41904d4276
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389902"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Lire des modèles et des diagrammes dans d'autres éditions de Visual Studio

Quand vous ouvrez un modèle dans une version de Visual Studio qui ne prend pas en charge la création de modèle, le modèle s'ouvre en mode lecture seule. Dans ce mode, vous pouvez modifier la disposition des diagrammes, mais vous ne pouvez pas modifier le modèle.

Pour connaître les versions de Visual Studio qui prennent en charge la création de modèles, consultez [prise en charge des versions pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Obtention de l'accès à un modèle et à des diagrammes

Pour lire un diagramme de dépendance, vous devez d’abord utiliser Visual Studio pour ouvrir le projet de modélisation, puis ouvrir le diagramme à l’intérieur de celui-ci.

Pour cette raison, si vous souhaitez lire un diagramme de dépendances, vous devez également avoir accès au projet de modélisation dans lequel il a été créé. Pour ce faire, vous pouvez accéder au projet à partir du contrôle de code source ou obtenir une copie des fichiers projet.

> [!NOTE]
> Cela ne s'applique pas aux cartes de code et aux diagrammes de classe .NET générés à partir du code. Ces diagrammes peuvent être affichés indépendamment d'un projet de modélisation.

Pour lire un diagramme de dépendance, l’ensemble minimal de fichiers dont vous avez besoin est le suivant :

- Les deux fichiers de diagramme du diagramme que vous souhaitez lire, par exemple, **mondiagramme. classdiagram et mondiagramme. classdiagram. Layout**.

    > [!NOTE]
    > Pour les diagrammes de dépendance, vous devez également avoir le fichier nommé _mondiagramme_**. layerdiagram. Suppress**.

- Fichier de projet de modélisation (**MyModel. modelproj**)

- Fichier de modèle racine (**ModelDefinition\MyModel.Uml**)

- Fichiers de package pour tous les packages référencés dans le diagramme (**ModelDefinition\MyPackage.Uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifications que vous pouvez apporter en mode lecture seule

Si vous ouvrez un modèle et ses diagrammes dans une version de Visual Studio qui ne prend pas en charge la création de modèles, vous ne pouvez pas modifier le modèle. Autrement dit, vous ne pouvez pas modifier les éléments et les relations qui sont affichés dans les diagrammes ou dans l'Explorateur de modèles. En revanche, vous pouvez apporter certaines modifications à la disposition des diagrammes. Vous pouvez :

- réorganiser les formes et connecteurs dans le diagramme ;

- développer et réduire des formes.

Vous pouvez enregistrer ces modifications. Si vous souhaitez que vos modifications soient visibles par d’autres utilisateurs, vous devez au moins envoyer les fichiers **. Layout** mis à jour.

## <a name="see-also"></a>Voir aussi

- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
