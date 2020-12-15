---
title: 'Résolution des problèmes : Comment faire de publier une nouvelle version de mon extension existante ?'
description: Guide sur la mise à jour des extensions existantes par le biais du flux de travail de publication.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488464"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Résolution des problèmes : Comment faire de publier une nouvelle version de mon extension existante ?

> [!IMPORTANT]
> Actuellement, la création de nouvelles extensions n’est pas officiellement prise en charge dans Visual Studio 2019 pour Mac.

Le serveur de référentiels d’extensions de Visual Studio pour Mac sera déplacé le 15 janvier 2021. Ce déplacement n’aura pas d’impact sur les utilisateurs qui ont déjà téléchargé votre extension, mais va changer la façon dont vous publiez les nouvelles versions de votre extension après cette date.

En tant qu’auteur d’une extension existante, vous devez suivre un flux de travail différent pour publier d’autres mises à jour. Ce processus se décompose ainsi :
- Configuration d’un référentiel GitHub public pour chaque extension
- Partage de l’URL du référentiel avec l’équipe Visual Studio pour Mac par le biais de la [liste de distribution de publication d’extension](mailto:vsmextpub@microsoft.com)
- Mise à jour de votre extension à l’aide de la fonctionnalité releases dans GitHub


## <a name="initial-setup"></a>Configuration initiale 

Pour poursuivre la publication des mises à jour de vos extensions, vous devez créer un référentiel GitHub public. Si vous publiez plusieurs extensions, vous devez disposer d’un référentiel distinct pour chacun d’eux, sauf si vous utilisez toujours la version et que vous les publiez ensemble, auquel cas vous pouvez utiliser un référentiel unique.

> [!NOTE]
> Alors que le référentiel GitHub pour votre extension doit être public, vous n’avez pas besoin d’héberger votre code ici. Le fait de suivre ce processus ne nécessite pas que vous ayez votre code dans GitHub.


## <a name="share-the-location-of-your-repository"></a>Partager l’emplacement de votre référentiel

Une fois que vous avez configuré le référentiel, envoyez un e-mail à la [liste de diffusion de publication d’extension](mailto:vsmextpub@microsoft.com) avec l’URL.


## <a name="release-a-new-version"></a>Publier une nouvelle version

Vous allez utiliser le lien « créer une nouvelle version » sur la page principale du référentiel pour commencer le processus de mise à jour de votre extension. Une fois que vous avez sélectionné ce lien, procédez comme suit :

1. Ajoutez des informations à la **version tag** de la version au format suivant

    > v \<releaseVersion> \- VSM\<targetVersion>

    Où :
     - **&lt; releaseVersion &gt;** est le numéro de version de votre extension
     - **&lt; TargetVersion &gt;** est la version minimale de Visual Studio pour Mac que votre extension cible

2. Facultatif Vous pouvez renseigner les champs **titre** et **Description** à l’aide des informations de votre choix. ce flux de travail n’utilise pas les informations de ces champs.

3. Vérifiez que la case à cocher **en** préversion est désactivée. Si elle est activée, la mise en service n’est pas récupérée par ce processus de publication.

4. Attachez le ou les fichiers **. mPack** qui implémentent votre extension dans la section **binaires** . Il est possible d’attacher plusieurs fichiers **. mPack** dans une version.

Visual Studio pour Mac affiche la dernière version de votre extension qui est compatible avec l’installation Visual Studio pour Mac qui a été utilisée pour accéder au référentiel d’extension.

Tant que vous avez enregistré votre dépôt GitHub auprès de l’équipe Visual Studio pour Mac, la version de votre extension est récupérée par Visual Studio pour Mac dans les 24 heures.

## <a name="additional-information"></a>Informations supplémentaires

- Les mises en production qui ne sont pas conformes à la configuration requise décrite ci-dessus ne sont pas publiées. 
- Après le 15 janvier 2021, les mises à jour d’extension s’affichent uniquement dans le Visual Studio pour Mac 8,0 ou plus récent.
- Les extensions existantes restent à la disposition des utilisateurs Visual Studio pour Mac sans aucune action de votre part. Il vous suffit de suivre les instructions de ce guide si vous publiez une nouvelle version après le 15 janvier 2021.
