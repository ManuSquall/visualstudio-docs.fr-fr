---
title: Assistant publication (développement Office dans Visual Studio)
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
ms.openlocfilehash: 9ce0be90be111d458229189c2a06624bd726ac05
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604829"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Assistant publication (développement Office dans Visual Studio)
  Utilisez le **Assistant Publication** pour copier les fichiers de solution vers un emplacement spécifié, créer les fichiers manifeste et créer un programme d’installation.

 Pour accéder à cet Assistant, dans le **Build** menu, choisissez **publier** *SolutionName*. Vous pouvez également accéder à la **Assistant Publication** de **l’Explorateur de solutions**. Ouvrez le menu contextuel du nœud de projet, puis choisissez **publier**.

 Chaque section ci-dessous décrit une page de l’Assistant.

## <a name="where-do-you-want-to-publish-the-application"></a>Où voulez-vous publier l’application ?
 **Spécifiez l’emplacement de publication de cette application** requis. L’emplacement de publication est le répertoire où le **Assistant Publication** copie les fichiers solution tels que les manifestes, les assemblys, les certificats temporaires et les autres fichiers de la génération. Vous devez disposer d’un accès en écriture à ce répertoire.

 Tapez l’emplacement en tant qu’un chemin d’accès de disque, un partage de fichiers, un site FTP ou une URL du site web, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement. Le chemin d’accès peut être dans ces formats :

- Un chemin d’accès relatif ou absolu dans la norme Windows mettre en forme, telles que *C:\Deploy\MyApplication* ou *\MyApplication*.

- Un chemin d’accès UNC Universal Naming Convention (), tel que  *\\\ServerName\MyApplication\\*.

- Une URL d’un site web de site, tel que http://www.microsoft.com/MyApplication.

  Par défaut, l’emplacement de publication est *http://localhost/projectname/* si vous avez installé IIS, ou le répertoire publish\ si vous le faites pas IIS installé.

> [!NOTE]
>  Il existe des considérations plus si l’ordinateur cible exécute Windows Vista. Vous devez être administrateur sur l’ordinateur Windows Vista d’utiliser l’option de publication local. En outre, l’emplacement par défaut est toujours le *publier\\*  répertoire, que vous ayez installé IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Qu’est le chemin d’installation par défaut sur les ordinateurs des utilisateurs finaux ?
 Le chemin d’installation est facultative. Vous pouvez définir le chemin d’installation ultérieurement si vous préférez. Pour plus d’informations, consultez [Guide pratique pour Modifier le chemin d’installation d’une solution Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 Le chemin d’installation est le répertoire à partir duquel l’utilisateur final installe la personnalisation. Il s’agit également du chemin que la solution utilise pour vérifier les mises à jour. Le **Assistant Publication** ne déploie pas la solution à cet emplacement, à moins que le chemin d’accès est identique à celui que vous avez entré dans le **spécifier l’emplacement de publication de cette application** zone sur la page précédente.

 **À partir d’un site Web** spécifier l’URL que les utilisateurs finaux suivent pour installer la solution.

 **À partir d’un partage de fichier ou chemin d’accès UNC** spécifier le chemin d’accès UNC que les utilisateurs finaux suivront pour installer la solution.

 **À partir d’un CD-ROM ou DVD-ROM** cette option ne nécessite pas un chemin d’installation.

 Visual Studio ne pas grave le CD ou DVD. Vous devez copier manuellement la sortie vers un CD ou DVD.

## <a name="see-also"></a>Voir aussi
- [Déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Page Publier, Concepteur de projets &#40;développement Office dans Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
