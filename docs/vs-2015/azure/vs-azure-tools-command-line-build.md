---
title: Génération de ligne de commande pour Azure | Microsoft Docs
description: Génération de ligne de commande pour Azure
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002006"
---
# <a name="building-azure-projects-from-the-command-line"></a>Génération de projets Azure à partir de la ligne de commande
À l’aide de Microsoft Build Engine (MSBuild), vous pouvez générer des produits dans les environnements de laboratoire de génération où Visual Studio n’est pas installé. MSBuild utilise un format XML pour les fichiers de projet extensible et entièrement pris en charge par Microsoft. Utilisez le format de fichier MSBuild, vous pouvez décrire quels éléments doivent être générés pour une ou plusieurs plateformes et configurations.

Vous pouvez également exécuter MSBuild à la ligne de commande, et cette rubrique décrit cette approche. En définissant des propriétés sur la ligne de commande, vous pouvez créer des configurations spécifiques d’un projet. De même, vous pouvez également définir les cibles que MSBuild va générer. Pour plus d’informations sur les paramètres de ligne de commande et MSBuild, consultez [MSBuild de ligne de commande référence](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Paramètres MSBuild
La façon la plus simple pour créer un package consiste à exécuter MSBuild avec le `/t:Publish` option. Par défaut, cette commande crée un répertoire en relation avec le dossier racine du projet, tel que `<ProjectDirectory>\bin\Configuration\app.publish\`. Lorsque vous générez un projet Azure, deux fichiers sont générés : le fichier de package lui-même et le fichier de configuration associé :

* Fichier de package (`project.cspkg`)
* Fichier de configuration (`ServiceConfiguration.TargetProfile.cscfg`)

Par défaut, tous les projets Azure comprennent un fichier de configuration de service pour les versions locales (débogage) et l’autre pour les versions cloud (intermédiaire ou production). Toutefois, vous pouvez ajouter ou supprimer des fichiers de configuration de service selon vos besoins. Lorsque vous générez un package dans Visual Studio, vous êtes invité le fichier de configuration de service à inclure avec le package. Lorsque vous générez un package à l’aide de MSBuild, le fichier de configuration de service local est inclus par défaut. Pour inclure un fichier de configuration de service différent, définissez le `TargetProfile` propriété de la commande MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Si vous souhaitez utiliser un autre répertoire pour les fichiers de configuration et de package stockés, définissez le chemin d’accès à l’aide de la `/p:PublishDir=Directory\` option, y compris le séparateur de barre oblique inverse de fin.

## <a name="next-steps"></a>Étapes suivantes
Une fois que le package est créé, vous pouvez la déployer vers Azure.