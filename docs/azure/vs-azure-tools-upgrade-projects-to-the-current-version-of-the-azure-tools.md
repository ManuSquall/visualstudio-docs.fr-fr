---
title: Mettre à niveau des projets vers la version actuelle d’Azure Tools
description: Découvrez comment mettre à niveau un projet Azure dans Visual Studio vers la version actuelle d’Azure Tools
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: fce77f6417a14c204df883efd2f64655fa79b432
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901906"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Mise à niveau des projets vers la version actuelle d’Azure Tools pour Visual Studio
## <a name="overview"></a>Vue d’ensemble
Une fois installée la version actuelle d’Azure Tools (ou une autre version ultérieure à la version 1.6), tous les projets ayant été créés à l’aide d’une version d’Azure Tools antérieure à la version 1.6 (novembre 2011) seront automatiquement mis à niveau au moment de leur ouverture. Si vous avez créé des projets à l’aide de la version 1.6 (novembre 2011) et que celle-ci est encore installée, vous pourrez ouvrir ces projets dans l’ancienne version et décider plus tard s’ils doivent être mis à niveau.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Changements provoqués par la mise à niveau de votre projet
Si un projet est mis à niveau automatiquement ou si vous spécifiez que vous voulez le mettre à niveau, il sera modifié en vue de fonctionner avec les versions actuelles de certains assemblys. En outre, certaines propriétés seront également modifiées, comme le décrit cette section. Si votre projet nécessite que d’autres modifications soient compatibles avec la version la plus récente d’Azure Tools, vous devrez apporter ces modifications manuellement.

* Le fichier web.config pour les rôles web et le fichier app.config pour les rôles de travail sont mis à jour afin de référencer la version la plus récente de Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll.
* Les assemblys Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll et Microsoft.WindowsAzure.ServiceRuntime.dll sont mis à niveau vers les nouvelles versions.
* Les profils de publication qui étaient stockés dans le fichier projet Azure (.ccproj) sont déplacés vers un autre fichier ayant une extension .azurePubXml, situé dans le sous-répertoire **Publier** .
* Certaines propriétés du profil de publication sont mises à jour de manière à prendre en charge les nouvelles fonctionnalités et les fonctionnalités modifiées. **AllowUpgrade** est remplacé par **DeploymentReplacementMethod** car vous pouvez mettre à jour un service cloud déployé simultanément ou de manière incrémentielle.
* La propriété **UseIISExpressByDefault** est ajoutée et la valeur false lui est affectée afin que le serveur Web qui est utilisé pour le débogage ne passe pas automatiquement des services Internet (IIS) à IIS Express. IIS Express est le serveur web par défaut des projets créés à l’aide des versions récentes d’Azure Tools.
* Si Azure Caching est hébergé dans un ou plusieurs rôles de votre projet, certaines propriétés de la configuration du service (fichier .cscfg) et de la définition du service (fichier .csdef) seront modifiées au moment de la mise à niveau d’un projet. Si le projet utilise le package NuGet d’Azure Caching, il sera mis à niveau vers la version la plus récente du package. Vous devez ouvrir le fichier web.config et vérifier que la configuration du client a été conservée pendant la mise à niveau. Si vous avez ajouté les références aux assemblys clients Azure Caching sans utiliser le package NuGet, les assemblys ne seront pas mis à jour. Vous devrez mettre à jour manuellement les références aux nouvelles versions.

> [!IMPORTANT]
> Pour les projets en langage F#, vous devrez mettre à jour manuellement les références aux assemblys Azure pour que les versions les plus récentes de ces assemblys soient référencées.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Mise à niveau d’un projet Azure vers la version actuelle
1. Installez la version actuelle d’Azure Tools dans l’installation de Visual Studio à utiliser pour le projet mis à niveau, puis ouvrez celui-ci. Si le projet a été créé avec Azure Tools version 1.6 (novembre 2011), il sera automatiquement mis à niveau vers la version actuelle. Si le projet a été créé avec la version de novembre 2011 et que celle-ci est toujours installée, le projet s’ouvrira dans cette version.
2. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud du projet, choisissez **Propriétés**, puis choisissez l’onglet **Application** de la boîte de dialogue qui s’affiche.

    L'onglet **Application** affiche la version des outils qui est associée au projet. Si la version actuelle d’Azure Tools s’affiche, le projet a déjà été mis à niveau. Si vous avez installé une version plus récente des outils que celle indiquée dans l'onglet, un bouton **Mettre à niveau** apparaît.
3. Cliquez sur le bouton **Mettre à niveau** pour mettre à niveau un projet vers la version actuelle des outils.
4. Générez le projet, puis résolvez les erreurs qui résultent des modifications de l’API. Pour plus d’informations sur la modification de votre code pour la nouvelle version, consultez la documentation de l’API concernée.
