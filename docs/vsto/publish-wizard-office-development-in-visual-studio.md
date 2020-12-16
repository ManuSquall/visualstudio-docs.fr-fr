---
title: Assistant Publication (développement Office dans Visual Studio)
description: Découvrez comment vous pouvez utiliser l’Assistant Publication pour copier des fichiers de solution vers un emplacement spécifié, créer les fichiers manifeste et créer un programme d’installation dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528013"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Assistant Publication (développement Office dans Visual Studio)
  Utilisez l' **Assistant Publication** pour copier des fichiers de solution vers un emplacement spécifié, créer les fichiers manifeste et créer un programme d’installation.

 Pour accéder à cet Assistant, dans le menu **générer** , choisissez **publier** *NomSolution*. Vous pouvez également accéder à l' **Assistant Publication** à partir de **Explorateur de solutions**. Ouvrez le menu contextuel du nœud de projet, puis choisissez **publier**.

 Chaque section ci-dessous décrit une page de l’Assistant.

## <a name="where-do-you-want-to-publish-the-application"></a>Où voulez-vous publier l’application ?
 **Spécifier l’emplacement de publication de cette application** Obligatoire. L’emplacement de publication est le répertoire dans lequel l' **Assistant Publication** copie les fichiers de la solution, tels que les manifestes, les assemblys, le certificat temporaire et d’autres fichiers de la Build. Vous devez disposer d’un accès en écriture à ce répertoire.

 Tapez l’emplacement sous la forme d’un chemin d’accès de disque, d’un partage de fichiers, d’un site FTP ou d’une URL de site Web, ou cliquez sur le bouton **Parcourir** pour Rechercher l’emplacement. Le chemin d’accès peut être dans les formats suivants :

- Chemin d’accès relatif ou absolu dans le format Windows standard, tel que *C:\Deploy\MyApplication* ou *\MyApplication*.

- Un chemin d’accès UNC (Universal Naming Convention), tel que *\\ \ServerName\MyApplication \\*.

- URL d’un site Web, telle que `http://www.contoso.com/MyApplication` .

  Par défaut, l’emplacement de publication est *http://localhost/projectname/* si IIS est installé, ou le répertoire publish \ si IIS n’est pas installé.

> [!NOTE]
> Il y a plus de points à prendre en compte si l’ordinateur cible exécute Windows Vista. Pour utiliser l’option de publication locale, vous devez être administrateur sur l’ordinateur Windows Vista. En outre, l’emplacement par défaut est toujours le répertoire de *publication \\* , qu’IIS soit installé ou non.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Quel est le chemin d’installation par défaut sur les ordinateurs des utilisateurs finaux ?
 Le chemin d’installation est facultatif. Vous pouvez définir le chemin d’installation ultérieurement si vous préférez. Pour plus d’informations, consultez [Comment : modifier le chemin d’installation d’une solution Office](/previous-versions/bb608626(v=vs.110)).

 Le chemin d’installation est le répertoire à partir duquel l’utilisateur final installe la personnalisation. Il s’agit également du chemin que la solution utilise pour vérifier les mises à jour. L' **Assistant Publication** ne déploie pas la solution à cet emplacement, sauf si le chemin d’accès est identique à celui que vous avez entré dans la zone **Spécifiez l’emplacement de publication de cette application** sur la page précédente.

 **À partir d’un site Web** Spécifiez l’URL que les utilisateurs finaux devront suivre pour installer la solution.

 **À partir d’un chemin UNC ou d’un partage de fichiers** Spécifiez le chemin d’accès UNC que les utilisateurs finaux devront suivre pour installer la solution.

 **À partir d’un CD-ROM ou DVD-ROM** Cette option ne nécessite pas de chemin d’installation.

 Visual Studio ne grave pas le CD ou le DVD. Vous devez copier la sortie manuellement sur un CD ou un DVD.

## <a name="see-also"></a>Voir aussi
- [Déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Page publier, concepteur de projets &#40;développement Office dans Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)