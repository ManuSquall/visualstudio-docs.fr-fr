---
title: Assistant publication (développement Office dans Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2481557d1d75d64b5eb3f52f2755953ca344d323
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692718"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Assistant publication (développement Office dans Visual Studio)
  Utilisez le **Assistant Publication** pour copier les fichiers solution vers un emplacement spécifié, créer les fichiers manifeste et créer un programme d’installation.  
  
 Pour accéder à cet Assistant, dans le **générer** menu, choisissez **publier** *SolutionName*. Vous pouvez également accéder à la **Assistant Publication** de **l’Explorateur de solutions**. Ouvrez le menu contextuel du nœud de projet, puis choisissez **publier**.  
  
 Chaque section ci-dessous décrit une page de l’Assistant.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Où voulez-vous publier l’application ?  
 **Spécifiez l’emplacement de publication de cette application**  
 Obligatoire. L’emplacement de publication est le répertoire où le **Assistant Publication** copie les fichiers solution tels que les manifestes, les assemblys, les certificats temporaires et les autres fichiers de la build. Vous devez disposer d’un accès en écriture à ce répertoire.  
  
 Tapez l’emplacement comme chemin d’accès de disque, partage de fichiers, site FTP ou URL du site web, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement. Le chemin d’accès peut être aux formats suivants :  
  
-   Un chemin d’accès relatif ou absolu dans la norme Windows mettre en forme, telles que *C:\Deploy\MyApplication* ou *\MyApplication*.  
  
-   Un chemin d’accès UNC Universal Naming Convention (), tel que  *\\\ServerName\MyApplication\\*.  
  
-   Site d’une URL d’un site web, tel que http://www.microsoft.com/MyApplication.  
  
 Par défaut, l’emplacement de publication est *http://localhost/projectname/* si vous avez installé IIS, ou le répertoire Publish si vous le faites pas IIS installé.  
  
> [!NOTE]  
>  Il existe plus d’informations sur l’ordinateur cible exécute Windows Vista. Vous devez être administrateur sur l’ordinateur Windows Vista d’utiliser l’option de publication locale. En outre, l’emplacement par défaut est toujours le *publier\\*  répertoire, indépendamment de si vous avez installé IIS.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Qu’est le chemin d’installation par défaut sur les ordinateurs des utilisateurs finaux ?  
 Le chemin d’installation est facultative. Vous pouvez définir le chemin d’installation plus tard, si vous préférez. Pour plus d’informations, consultez [Comment : modifier le chemin d’accès de l’installation d’une solution Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Le chemin d’installation est le répertoire à partir duquel l’utilisateur final installe la personnalisation. Il s’agit également du chemin que la solution utilise pour vérifier les mises à jour. Le **Assistant Publication** ne déploie pas la solution à cet emplacement, à moins que le chemin d’accès est identique à celui que vous avez entré dans le **spécifier l’emplacement de publication de cette application** zone sur la page précédente.  
  
 **À partir d’un site Web**  
 Spécifiez l’URL que les utilisateurs finaux suivront pour installer la solution.  
  
 **À partir d’un partage de fichier ou chemin d’accès UNC**  
 Spécifiez le chemin d’accès UNC que les utilisateurs finaux suivront pour installer la solution.  
  
 **À partir d’un CD-ROM ou DVD-ROM**  
 Cette option ne requiert pas un chemin d’installation.  
  
 Visual Studio ne grave pas le CD ou DVD. Vous devez copier manuellement la sortie à un CD ou DVD.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Page Publier, Concepteur de projets &#40;développement Office dans Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)  
  
  