---
title: Génération en mode ligne de commande pour Azure | Microsoft Docs
description: Génération en ligne de commande pour Azure
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: b60e076c50c9465f54c3c05dda0318f56fa5e9ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844266"
---
# <a name="building-azure-projects-from-the-command-line"></a>Génération de projets Azure à partir de la ligne de commande
À l’aide de Microsoft Build Engine (MSBuild), vous pouvez générer des produits dans des environnements de laboratoire-génération où Visual Studio n’est pas installé. MSBuild utilise pour les fichiers projet un format XML extensible et entièrement pris en charge par Microsoft. En utilisant le format de fichier MSBuild, vous pouvez décrire quels éléments doivent être générés pour une ou plusieurs plateformes et configurations.

Vous pouvez également exécuter MSBuild dans une ligne de commande, et cette rubrique décrit cette approche. En définissant des propriétés dans la ligne de commandes, vous pouvez créer des configurations propres à un projet. De même, vous pouvez également définir les cibles que MSBuild va générer. Pour plus d’informations sur les paramètres de ligne de commande et MSBuild, consultez la page [Référence de la ligne de commande MSBuild](../msbuild/msbuild-command-line-reference.md).

## <a name="msbuild-parameters"></a>Paramètres MSBuild
La façon la plus simple de créer un package consiste à exécuter MSBuild avec l’option `/t:Publish` . Par défaut, cette commande crée un répertoire en relation avec le dossier racine du projet, par exemple `<ProjectDirectory>\bin\Configuration\app.publish\`. Lorsque vous générez un projet Azure, deux fichiers sont générés : le fichier de package et le fichier de configuration qui l'accompagne :

* Fichier de package (`project.cspkg`)
* Fichier de configuration (`ServiceConfiguration.TargetProfile.cscfg`)

Par défaut, tous les projets Azure comprennent un fichier de configuration de service pour les versions locales (débogage) et un autre pour les versions cloud (gestion intermédiaire ou production). Mais vous pouvez ajouter ou supprimer des fichiers de configuration de service selon vos besoins. Lorsque vous générez un package dans Visual Studio, il vous est demandé quels fichiers de configuration de service vous voulez inclure avec le package. Lorsque vous générez un package avec MSBuild, le fichier de configuration de service local est inclus par défaut. Pour inclure un autre fichier de configuration de service, définissez la propriété `TargetProfile` de la commande MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Si vous souhaitez utiliser un autre répertoire pour les fichiers de configuration et de package stockés, définissez le chemin d'accès à l'aide de l’option `/p:PublishDir=Directory\`, en incluant la barre oblique inverse de fin comme séparateur.

## <a name="next-steps"></a>Étapes suivantes
Une fois le package créé, vous pouvez le déployer sur Azure.
