---
title: Test unitaire d’une application en conteneur
author: ghogen
description: Exécuter des tests unitaires avec chaque Build pour un projet d’ancrage dans Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "70312039"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Procédure : Exécuter des tests unitaires pour une application en conteneur

Vous pouvez exécuter des tests unitaires avec chaque Build de votre projet en conteneur en modifiant votre fichier dockerfile.

## <a name="prerequisites"></a>Prérequis

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Installer [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Tests unitaires configurés pour s’exécuter à l’aide de [dotnet test](/dotnet/core/tools/dotnet-test)
- Installer l' [extension de fenêtre conteneurs](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Ajouter des tests unitaires à fichier dockerfile

Visual Studio effectue des optimisations de performances spéciales avant de modifier le fichier dockerfile. Lors de la génération de la configuration de **débogage** , Visual Studio génère des projets sur l’ordinateur local et copie les résultats dans le conteneur. Ainsi, seule la première étape du fichier dockerfile multiétape est exécutée comme spécifié dans le fichier dockerfile. Pour plus d’informations, consultez [processus de génération des outils de conteneur pour Visual Studio](container-build.md).

Pour ajouter des tests unitaires à un fichier dockerfile à plusieurs étapes `unit-test` , ajoutez une étape au fichier dockerfile `build` entre `publish` les étapes et.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio exécute uniquement la première étape de la configuration de **débogage** , de sorte que l' `unit-test` étape est exécutée uniquement dans la configuration **Release** . Toutefois, même dans la configuration **Release** , les résultats du journal ne sont pas inclus dans l’image finale, car l’image finale `base` est créée à partir de `unit-test` l’étape, et non à partir de l’étape. Pour exécuter les tests et produire une image dans laquelle vous pouvez afficher les journaux, utilisez la commande suivante :

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez ensuite utiliser la [fenêtre conteneurs](view-and-diagnose-containers.md) (si vous avez installé l’extension) pour afficher les journaux des tests.  

Pour afficher vos journaux de tests, utilisez **CTRL**+**Q** et recherchez **conteneurs** pour ouvrir la fenêtre **conteneurs** . Dans la fenêtre **conteneurs** , recherchez votre conteneur, ouvrez l’onglet **fichiers** , recherchez le fichier de résultats des tests (. trx) dans le système de fichiers du conteneur, puis ouvrez-le pour afficher les résultats dans Visual Studio.

