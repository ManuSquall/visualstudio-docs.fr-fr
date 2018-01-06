---
title: "Comment : créer des projets Office dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: "96"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: aca002dc7f9793dc379fb4e1a325342704e4d6c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Comment : créer des projets Office dans Visual Studio
  Vous pouvez utiliser [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour créer le complément VSTO et au niveau du document personnalisations pour les applications Microsoft Office. Pour plus d’informations sur ces types de projets, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Pour créer un projet de complément VSTO  
  
1.  Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**. Si votre environnement de développement intégré (IDE) est définie pour utiliser [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] des paramètres de développement, dans le **fichier** menu, choisissez **nouveau**, **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
    > [!NOTE]  
    >  Par défaut, les projets Office ciblent le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour plus d’informations, consultez [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  Dans le volet Modèles, sous le nœud correspondant à la langue que vous souhaitez utiliser, développez **Office/SharePoint**.  
  
3.  Choisissez le **compléments Office** nœud.  
  
4.  Dans la liste des modèles de projet, sélectionnez un modèle de projet de complément VSTO. Pour obtenir la liste des modèles de projet disponibles complément VSTO, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Si les modèles de projet ne sont pas visibles quand vous sélectionnez le **compléments Office** nœud, vérifiez que **.NET Framework 4** ou version ultérieure est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue. Les modèles de projet Office sont visibles pour les deux versions du .NET Framework.  
  
5.  Dans le **nom** , tapez un nom pour le projet. Par défaut, le nom du projet est également utilisé comme nom de solution.  
  
6.  Dans le **emplacement** , entrez le chemin d’accès où vous souhaitez créer le projet. Vous pouvez utiliser des chemins d’accès UNC absolus et universels. N’utilisez pas HTTP, FTP ni d’autres chemins d’accès de protocole.  
  
     Les emplacements ont les formats suivants :  
  
    -   [*lecteur*\]: \  
  
    -   \\\\*Serveur*\\*partage*  
  
     N'utilisez pas les caractères suivants dans l'emplacement :  
  
    -   astérisque (*)  
  
    -   barre verticale (|)  
  
    -   deux-points (:) (sauf après la lettre de lecteur)  
  
    -   guillemet double (") (les chemins d’accès qui contiennent des espaces n’ont pas besoin de guillemets.)  
  
    -   Inférieur à (\<)  
  
    -   Supérieur à (>)  
  
    -   point d'interrogation (?)  
  
    -   pourcentage (%)  
  
7.  Sélectionnez le bouton **OK** .  
  
    > [!NOTE]  
    >  Les projets de complément sont toujours enregistrés quand ils sont créés. Ils ne peuvent pas être créés en tant que projets temporaires. Pour plus d’informations sur les projets temporaires, consultez [projets temporaires](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Pour créer un projet de personnalisation au niveau du document  
  
1.  Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**. Si votre interface IDE est définie pour utiliser des paramètres de développement Visual Basic, sur le **fichier** menu, choisissez **nouveau**, **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
    > [!NOTE]  
    >  Par défaut, les projets Office ciblent le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Pour plus d’informations, consultez [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  Dans le volet Modèles, sous le nœud correspondant à la langue que vous souhaitez utiliser, développez **Office/SharePoint**.  
  
3.  Sélectionnez le nœud **Compléments Office** .  
  
4.  Dans la liste des modèles de projet, sélectionnez un modèle de projet au niveau du document. Pour obtenir la liste des modèles de projet au niveau du document disponibles, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Si les modèles de projet ne sont pas visibles quand vous sélectionnez le **compléments Office** nœud, vérifiez que **.NET Framework 4** ou version ultérieure est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue. Les modèles de projet Office sont visibles pour les deux versions du .NET Framework.  
  
5.  Dans le **nom** , tapez un nom pour le projet. Par défaut, ce nom est également utilisé pour le document. Si votre interface IDE est configurée pour utiliser des paramètres de développement Visual C# ou des paramètres de développement généraux, entrez également un emplacement et un nom de solution.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas utiliser de caractères de substitution dans le chemin d’accès à l’emplacement du projet ou dans le nom du projet. En outre, si vous envisagez de déployer la solution pour une utilisation en mode hors connexion, les caractères du nom du projet doivent respecter les spécifications du protocole HTTP.  
  
6.  Sélectionnez le bouton **OK** .  
  
     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
7.  Sélectionnez **créer un nouveau document** si vous souhaitez créer un document de la solution, ou sélectionnez **copier un document existant** si vous souhaitez personnaliser un document existant.  
  
     Si vous créez un nouveau document, spécifiez le nom de la **nom** zone, puis sélectionnez le format du document à l’aide de la **Format** boîte. Pour plus d’informations sur les formats disponibles, consultez [Architecture des personnalisations de niveau Document](../vsto/architecture-of-document-level-customizations.md).  
  
     Si vous utilisez un document existant, spécifiez l’emplacement du document dans le **chemin d’accès complet du document existant** boîte. Vous pouvez utiliser des chemins d’accès absolus ou UNC. N’utilisez aucun chemin d’accès de protocole, notamment HTTP ou FTP, vers le document.  
  
     Les emplacements ont les formats suivants :  
  
    -   [*lecteur*\]: \  
  
    -   \\\\*Serveur*\\*partage*  
  
     N'utilisez pas les caractères suivants dans l'emplacement :  
  
    -   astérisque (*)  
  
    -   barre verticale (|)  
  
    -   deux-points (:) (sauf après la lettre de lecteur)  
  
    -   guillemet double (") (les chemins d’accès qui contiennent des espaces n’ont pas besoin de guillemets.)  
  
    -   Inférieur à (\<)  
  
    -   Supérieur à (>)  
  
    -   point d'interrogation (?)  
  
    -   pourcentage (%)  
  
    > [!NOTE]  
    >  Si vous utilisez un document existant dans un projet [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], utilisez uniquement des documents qui ont été créés ou convertis dans [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. De même, si vous utilisez un document existant dans un projet Word 2010, utilisez uniquement des documents qui ont été créés dans Word 2010 ou convertis dans ce format. Certaines fonctionnalités seront désactivées dans le document si celui-ci a été créé dans une version antérieure de Word. Si vous tentez d’écrire du code qui utilise ces fonctionnalités, vous pouvez rencontrer des erreurs dans votre projet. Pour convertir un document, ouvrez-le dans [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou Word 2010, sur le **fichier** onglet sur le ruban, choisissez **Info**, **convertir**.  
  
8.  Choisissez **Terminer**.  
  
9. Ajoutez le dossier du projet et ses sous-dossiers à la liste d’emplacements approuvés dans le Centre de gestion de la confidentialité dans Word, dans les cas suivants :  
  
    -   Vous créez un document Word basé sur un fichier .docm, et le document contient un projet VBA ou héberge des contrôles Windows Forms. L'ajout du dossier du projet à la liste d'emplacements approuvés aidera à s'assurer que le document fonctionne comme prévu au moment du design.  
  
    -   Vous créez un projet de modèle basé sur un fichier .dotx. Vous devez ajouter le dossier du projet à la liste d’emplacements approuvés afin de pouvoir exécuter et déboguer le projet.  
  
     Pour plus d’informations sur l’ajout d’un document aux emplacements approuvés, consultez le site web Microsoft Office Online [créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)   
 [Développement collaboratif de Solutions Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Bien démarrer avec la programmation des compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  