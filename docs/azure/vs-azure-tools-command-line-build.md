---
title: Génération en mode ligne de commande pour Azure | Microsoft Docs
description: Génération en ligne de commande pour Azure
services: visual-studio-online
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 03/05/2017
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: bc65d64f4dad2ac38c1f0c64ce6c7297d3c37d3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572420"
---
# <a name="building-azure-projects-from-the-command-line"></a>Génération de projets Azure à partir de la ligne de commande
À l’aide de Microsoft Build Engine (MSBuild), vous pouvez générer des produits dans des environnements de laboratoire-génération où Visual Studio n’est pas installé. MSBuild utilise pour les fichiers projet un format XML extensible et entièrement pris en charge par Microsoft. En utilisant le format de fichier MSBuild, vous pouvez décrire quels éléments doivent être générés pour une ou plusieurs plateformes et configurations.

Vous pouvez également exécuter MSBuild dans une ligne de commande, et cette rubrique décrit cette approche. En définissant des propriétés dans la ligne de commandes, vous pouvez créer des configurations propres à un projet. De même, vous pouvez également définir les cibles que MSBuild va générer. Pour plus d’informations sur les paramètres de ligne de commande et MSBuild, consultez la page [Référence de la ligne de commande MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Paramètres MSBuild
La façon la plus simple de créer un package consiste à exécuter MSBuild avec l’option `/t:Publish` . Par défaut, cette commande crée un répertoire en relation avec le dossier racine du projet, par exemple `<ProjectDirectory>\bin\Configuration\app.publish\`. Lorsque vous générez un projet Azure, deux fichiers sont générés : le fichier de package et le fichier de configuration qui l'accompagne :

- Fichier de package (`project.cspkg`)
- Fichier de configuration (`ServiceConfiguration.TargetProfile.cscfg`)

Par défaut, tous les projets Azure comprennent un fichier de configuration de service pour les versions locales (débogage) et un autre pour les versions cloud (gestion intermédiaire ou production). Mais vous pouvez ajouter ou supprimer des fichiers de configuration de service selon vos besoins. Lorsque vous générez un package dans Visual Studio, il vous est demandé quels fichiers de configuration de service vous voulez inclure avec le package. Lorsque vous générez un package avec MSBuild, le fichier de configuration de service local est inclus par défaut. Pour inclure un autre fichier de configuration de service, définissez la propriété `TargetProfile` de la commande MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Si vous souhaitez utiliser un autre répertoire pour les fichiers de configuration et de package stockés, définissez le chemin d'accès à l'aide de l’option `/p:PublishDir=Directory\`, en incluant la barre oblique inverse de fin comme séparateur.

## <a name="next-steps"></a>Étapes suivantes
Une fois le package créé, vous pouvez le déployer sur Azure.

<!-- Update_Description: update metedata properties -->