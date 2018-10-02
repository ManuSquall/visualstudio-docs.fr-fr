---
title: Guide pratique pour localiser et organiser les modèles de projet et d’élément | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08817b551d015481000d3151fb054ee5803ee6f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495187"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Guide pratique pour localiser et organiser les modèles de projet et d'élément
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : localiser et organiser les modèles de projet et élément](https://docs.microsoft.com/visualstudio/ide/how-to-locate-and-organize-project-and-item-templates).  
  
Les fichiers modèles doivent être placés à un emplacement que Visual Studio reconnaît afin que les modèles s’affichent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**. Vous pouvez créer des sous-catégories personnalisées de modèles afin qu'elles apparaissent également dans l'interface utilisateur.  
  
## <a name="locating-templates"></a>Localisation de modèles  
 Par défaut, Visual Studio recherche les modèles de projet et d'élément à deux emplacements. Si un fichier compressé incluant un fichier .vstemplate existe à ces emplacements, un modèle apparaît dans les boîtes de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
### <a name="installed-templates"></a>Modèles installés  
 Par défaut, les modèles installés avec le produit se trouvent dans :  
  
-   \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ItemTemplates\\*Langage*\\*Paramètres_régionaux*\  
  
-   \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ProjectTemplates\\*Langage*\\*Paramètres_régionaux\\*  
  
 Par exemple, le répertoire suivant contient les modèles de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour l'anglais :  
  
 \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Modèles personnalisés  
 Par défaut, les modèles personnalisés se trouvent dans :  
  
-   \Mes documents\Visual Studio *Version*\Templates\ProjectTemplates\\*Langage*\  
  
-   \Mes documents\Visual Studio *Version*\Templates\ItemTemplates\\*Langage*\  
  
 Par exemple, le répertoire suivant contient les modèles de projet [!INCLUDE[csprcs](../includes/csprcs-md.md)] personnalisés :   
  
 C:\Documents and Settings\nom_utilisateur\Mes Documents\\< version de Visual Studio\>\Templates\ProjectTemplates\Visual C# \  
  
 Les modèles personnalisés n'incluent pas de sous-répertoire pour les modèles localisés. Vous pouvez changer le répertoire par défaut des modèles personnalisés dans la boîte de dialogue **Options**, sous **Environnement\Projets et solutions**.  
  
## <a name="organizing-templates"></a>Organisation de modèles  
 Les catégories des boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** reflètent les structures de répertoires qui existent pour les modèles installés et personnalisés. Vous pouvez modifier ces structures de répertoires pour organiser vos modèles selon votre propre logique.  
  
> [!NOTE]
>  Vous ne pouvez pas créer de catégorie au niveau du langage de programmation. Vous ne pouvez créer une catégorie qu'à l'intérieur de chaque langage.  
  
 Si les répertoires des modèles installés et personnalisés pour un langage particulier n’ont pas la même structure (c’est-à-dire un dossier contient des répertoires qui n’existent pas dans l’autre dossier), le jeu de catégories qui apparaît dans la boîte de dialogue **Nouveau projet** est la fusion de toutes les catégories.  
  
### <a name="organizing-installed-templates"></a>Organisation de modèles installés  
 Vous pouvez organiser les modèles installés en créant des sous-répertoires dans le dossier du langage de programmation. Ces sous-répertoires apparaissent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** en tant que dossiers virtuels dans chaque langage.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>Pour créer des catégories de modèles de projet installés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles installés. Par exemple, pour créer une catégorie Office pour les modèles de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pourriez créer le répertoire suivant :   
  
     \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Fermez toutes les instances de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  À l’invite de commandes, localisez le répertoire qui contient devenv.exe et tapez **devenv /installvstemplates**.  
  
6.  Exécutez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7.  Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
8.  Vérifiez que la catégorie Office apparaît dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, sous [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
 Vous pouvez également regrouper dans un dossier personnalisé un sous-ensemble de modèles d’élément de projet.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>Pour créer des catégories de modèles d'élément installés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles installés. Par exemple, pour créer une catégorie Web pour les modèles d'élément [!INCLUDE[csprcs](../includes/csprcs-md.md)], vous pourriez créer le répertoire suivant :   
  
     \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Fermez toutes les instances de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  À l’invite de commandes, localisez le répertoire qui contient devenv.exe et tapez **devenv /setup**.  
  
6.  Exécutez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7.  Créez un projet ou ouvrez un projet existant.  
  
8.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
9. Vérifiez que la catégorie web apparaît dans la boîte de dialogue **Ajouter un nouvel élément**, dans le volet **Types de projets**.  
  
### <a name="organizing-custom-templates"></a>Organisation de modèles personnalisés  
 Pour organiser des modèles personnalisés dans leurs propres catégories, ajoutez de nouveaux dossiers à leur emplacement. La boîte de dialogue **Nouveau projet** reflète toutes les modifications que vous apportez à vos catégories de modèles.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>Pour créer des catégories de modèles de projet personnalisés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles de projet personnalisés. Par exemple, pour créer une catégorie HelloWorld pour les modèles [!INCLUDE[csprcs](../includes/csprcs-md.md)], vous pourriez créer le répertoire suivant :   
  
     \My documents\\< version de Visual Studio\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
4.  Vérifiez que la catégorie HelloWorld apparaît dans la boîte de dialogue **Nouveau projet** dans le volet **Types de projets**, sous [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
 Vous pouvez également regrouper dans un dossier personnalisé un sous-ensemble de modèles d’élément personnalisés.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>Pour créer des catégories de modèles d'élément personnalisés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles d'élément personnalisés. Par exemple, pour créer une catégorie HelloWorld pour les modèles [!INCLUDE[csprcs](../includes/csprcs-md.md)], vous pourriez créer le répertoire suivant :   
  
     \My documents\\< version de Visual Studio\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Créez un projet ou ouvrez un projet existant.  
  
4.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
5.  Vérifiez que la catégorie HelloWorld apparaît dans la boîte de dialogue **Ajouter un nouvel élément** dans le volet **Types de projets**.  
  
### <a name="displaying-templates-in-parent-categories"></a>Affichage de modèles dans des catégories parentes  
 Vous pouvez permettre aux modèles des sous-catégories d'être affichés dans leur catégorie parente à l'aide de l'élément `NumberOfParentCategoriesToRollUp` du fichier .vstemplate. Ces étapes sont identiques pour les modèles de projet et les modèles d'élément.  
  
##### <a name="to-display-templates-in-parent-categories"></a>Pour afficher les modèles dans les catégories parentes  
  
1.  Localisez le fichier .zip qui contient le modèle.  
  
2.  Extrayez le fichier zip.  
  
3.  Ouvrez le fichier .vstemplate dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Dans l'élément `TemplateData`, ajoutez un élément `NumberOfParentCategoriesToRollUp`. Par exemple, le code suivant fait apparaître le modèle dans sa catégorie parente, mais pas plus haut dans la hiérarchie.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  Enregistrez et fermez le fichier .vstemplate.   
  
6.  Sélectionnez les fichiers présents dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers**, puis sur **Dossier compressé**. Les fichiers sont compressés dans un fichier .zip.  
  
7.  Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.  
  
8.  Mettez le nouveau fichier .zip dans le répertoire duquel vous avez supprimé le fichier .zip.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Élément NumberOfParentCategoriesToRollUp (modèles Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)   
 [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)



