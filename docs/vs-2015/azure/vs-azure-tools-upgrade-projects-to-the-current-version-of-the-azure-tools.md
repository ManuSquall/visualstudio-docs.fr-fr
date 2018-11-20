---
title: Comment mettre à niveau des projets vers la version actuelle d’Azure tools | Microsoft Docs
description: Découvrez comment mettre à niveau un projet Azure dans Visual Studio vers la version actuelle d’Azure tools
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001988"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Guide pratique pour mettre à niveau des projets vers la version actuelle d’Azure Tools pour Visual Studio
## <a name="overview"></a>Vue d'ensemble
Après avoir installé la version actuelle de Windows Azure Tools (ou une version précédente est plus récente que 1.6), tous les projets qui ont été créés à l’aide d’Azure Tools version 1.6 (novembre 2011) sera mis à niveau automatiquement dès que vous les ouvrez. Si vous avez créé des projets à l’aide de la version 1.6 (novembre 2011) de ces outils et que vous avez toujours cette version installée, vous pouvez ouvrir ces projets dans l’ancienne version et décidez ultérieurement s’il faut mettre à niveau.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Comment votre projet change lorsque vous mettez à niveau
Si un projet est mis à niveau automatiquement ou si vous spécifiez que vous souhaitez mettre à niveau, votre projet est modifié pour fonctionner avec les versions actuelles de certains assemblys, et certaines propriétés sont également modifiées comme décrit dans cette section. Si votre projet a besoin d’autres modifications pour être compatible avec la version la plus récente des outils, vous devez effectuer ces modifications manuellement.

* Le fichier web.config pour les rôles web et le fichier app.config pour les rôles de travail sont mis à jour pour faire référence à la version la plus récente de Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll.
* Les assemblys Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll et Microsoft.WindowsAzure.ServiceRuntime.dll sont mis à niveau vers les nouvelles versions.
* Profils de publication qui ont été stockées dans le fichier de projet Windows Azure (.ccproj) sont déplacés vers un fichier distinct, avec l’extension .azurePubXml, dans le **publier** sous-répertoire.
* Certaines propriétés dans le profil de publication sont mises à jour pour prendre en charge des fonctionnalités nouvelles et modifiées. **AllowUpgrade** est remplacé par **DeploymentReplacementMethod** , car vous pouvez mettre à jour un service cloud déployé simultanément ou incrémentielle.
* La propriété **UseIISExpressByDefault** est ajouté et défini sur false pour que le serveur web qui est utilisé pour le débogage ne changer pas automatiquement à partir de Internet Information Services (IIS) pour IIS Express. IIS Express est le serveur web par défaut pour les projets qui sont créés avec les versions plus récentes des outils.
* Si la mise en cache Azure est hébergé dans un ou plusieurs des rôles de votre projet, certaines propriétés dans la configuration du service (fichier .cscfg) et la définition de service (fichier .csdef) seront modifiées lorsqu’un projet est mis à niveau. Si le projet utilise le package NuGet de la mise en cache Azure, le projet est mis à niveau vers la version la plus récente du package. Vous devez ouvrir le fichier web.config et vérifier que la configuration du client a été conservée pendant la mise à niveau. Si vous avez ajouté les références aux assemblys clients Azure Caching sans utiliser le package NuGet, ces assemblys ne sont pas mises à jour ; Vous devez manuellement mettre à jour ces références aux nouvelles versions.

> [!IMPORTANT]
> Pour F# projets, vous devez manuellement mettre à jour des références aux assemblys Azure afin qu’ils référencent les versions plus récentes de ces assemblys.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Comment mettre à niveau un projet Azure vers la version actuelle
1. Installer la version actuelle de Windows Azure Tools dans l’installation de Visual Studio que vous souhaitez utiliser pour le projet mis à niveau, puis ouvrez le projet que vous souhaitez mettre à niveau. Si le projet a été créé avec Azure Tools version 1.6 (novembre 2011), il est automatiquement mis à niveau vers la version actuelle. Si le projet a été créé avec le novembre 2011 version et cette version est toujours installée, le projet s’ouvre dans cette version.
2. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud de projet, choisissez **propriétés**, puis choisissez le **Application** onglet de la boîte de dialogue qui s’affiche.
   
    Le **Application** onglet affiche la version des outils qui est associé le projet. Si la version actuelle de Windows Azure Tools s’affiche, le projet a déjà été mis à niveau. Si vous avez installé une version plus récente des outils que celle indiquée dans l’onglet, un **mise à niveau** bouton s’affiche.
3. Choisissez le **mise à niveau** bouton Mettre à niveau un projet vers la version actuelle des outils.
4. Générez le projet, puis résolvez les erreurs qui résultent de modifications de l’API. Pour plus d’informations sur la façon de modifier votre code pour la nouvelle version, consultez la documentation de l’API concernée.

