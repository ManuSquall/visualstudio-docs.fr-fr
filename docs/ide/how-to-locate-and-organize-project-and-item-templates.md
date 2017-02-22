---
title: "Comment&#160;: localiser et organiser les mod&#232;les de projet et d&#39;&#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "emplacements des modèles personnalisés (Visual Studio)"
  - "modèles d'élément, emplacements"
  - "modèles de projet (Visual Studio), afficher"
  - "modèles de projet (Visual Studio), emplacements"
  - "modèles (Visual Studio), emplacements"
  - "modèles Visual Studio, emplacements"
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: localiser et organiser les mod&#232;les de projet et d&#39;&#233;l&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les fichiers modèles doivent être placés à un emplacement que Visual Studio reconnaît afin que les modèles s'affichent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**.  Vous pouvez créer des sous\-catégories personnalisées de modèles afin qu'elles apparaissent également dans l'interface utilisateur.  
  
## Localisation de modèles  
 Par défaut, Visual Studio recherche les modèles de projet et d'élément à deux emplacements.  Si un fichier compressé incluant un fichier .vstemplate existe à ces emplacements, un modèle apparaît dans les boîtes de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
### Modèles installés  
 Par défaut, les modèles installés avec le produit se trouvent dans :  
  
-   \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\*Language*\\*Locale*\\  
  
-   \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ProjectTemplates\\*Language*\\*Locale\\*  
  
 Par exemple, le répertoire suivant contient les modèles de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour l'anglais :  
  
 C:\\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033\\  
  
### Modèles personnalisés  
 Par défaut, les modèles personnalisés se trouvent dans :  
  
-   \\Mes documents\\*Version* Visual Studio\\Templates\\ProjectTemplates\\*Language*\\  
  
-   \\Mes documents\\*Version* Visual Studio\\Templates\\ItemTemplates\\*Language*\\  
  
 Par exemple, le répertoire suivant contient les modèles de projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] personnalisés :  
  
 C:\\Documents and Settings\\nom\_utilisateur\\Mes documents\\\<version de Visual Studio\>\\Templates\\ProjectTemplates\\Visual C\#\\  
  
 Les modèles personnalisés n'incluent pas de sous\-répertoire pour les modèles localisés.  Vous pouvez modifier le répertoire par défaut des modèles personnalisés dans la boîte de dialogue **Options** sous **Environnement\\Projets et solutions**.  
  
## Organisation de modèles  
 Les catégories des boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** reflètent les structures de répertoires qui existent pour les modèles installés et personnalisés.  Vous pouvez modifier ces structures de répertoires pour organiser vos modèles selon votre propre logique.  
  
> [!NOTE]
>  Vous ne pouvez pas créer de catégorie au niveau du langage de programmation.  Vous ne pouvez créer une catégorie qu'à l'intérieur de chaque langage.  
  
 Si les répertoires des modèles installés et personnalisés pour un langage particulier n'ont pas la même structure \(c'est\-à\-dire un dossier contient des répertoires qui n'existent pas dans l'autre dossier\), le jeu de catégories qui apparaît dans la boîte de dialogue **Nouveau projet** est la fusion de toutes les catégories.  
  
### Organisation de modèles installés  
 Vous pouvez organiser les modèles installés en créant des sous\-répertoires dans le dossier du langage de programmation.  Ces sous\-répertoires apparaissent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** en tant que dossiers virtuels dans chaque langage.  
  
##### Pour créer des catégories de modèles de projet installés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles installés.  Par exemple, pour créer une catégorie Office pour les modèles de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pourriez créer le répertoire suivant :  
  
     \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ProjectTemplates\\VisualBasic\\1033\\Office\\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Fermez toutes les instances de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  À l'invite de commandes, localisez le répertoire qui contient devenv.exe et tapez **devenv \/installvstemplates**.  
  
6.  Exécutez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
7.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.  
  
8.  Vérifiez que la catégorie Office apparaît dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, sous [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
 Vous pouvez également regrouper dans un dossier personnalisé un sous\-ensemble de modèles d'élément de projet.  
  
##### Pour créer des catégories de modèles d'élément installés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles installés.  Par exemple, pour créer une catégorie Web pour les modèles d'élément [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vous pourriez créer le répertoire suivant :  
  
     \\*VisualStudioInstallationDirectory*\\Common7\\IDE\\ItemTemplates\\CSharp\\1033\\Web\\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Fermez toutes les instances de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  À l'invite de commandes, localisez le répertoire qui contient devenv.exe et tapez **devenv \/setup**.  
  
6.  Exécutez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
7.  Créez un projet ou ouvrez un projet existant.  
  
8.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
9. Vérifiez que la catégorie Web apparaît dans la boîte de dialogue **Ajouter un nouvel élément**, dans le volet **Types de projets**.  
  
### Organisation de modèles personnalisés  
 Pour organiser des modèles personnalisés dans leurs propres catégories, ajoutez de nouveaux dossiers à leur emplacement.  La boîte de dialogue **Nouveau projet** reflète toutes les modifications que vous apportez à vos catégories de modèles.  
  
##### Pour créer des catégories de modèles de projet personnalisés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles de projet personnalisés.  Par exemple, pour créer une catégorie HelloWorld pour les modèles [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vous pourriez créer le répertoire suivant :  
  
     \\Mes documents\\\<version de Visual Studio\>\\Templates\\ProjectTemplates\\CSharp\\HelloWorld\\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.  
  
4.  Vérifiez que la catégorie HelloWorld apparaît dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, sous [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
 Vous pouvez également regrouper dans un dossier personnalisé un sous\-ensemble de modèles d'élément personnalisés.  
  
##### Pour créer des catégories de modèles d'élément personnalisés  
  
1.  Créez un dossier dans le dossier du langage du répertoire des modèles d'élément personnalisés.  Par exemple, pour créer une catégorie HelloWorld pour les modèles [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vous pourriez créer le répertoire suivant :  
  
     \\Mes documents\\\<version de Visual Studio\>\\Templates\\ItemTemplates\\CSharp\\HelloWorld\\  
  
2.  Placez tous les modèles de cette catégorie dans le nouveau dossier.  
  
3.  Créez un projet ou ouvrez un projet existant.  
  
4.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
5.  Vérifiez que la catégorie HelloWorld apparaît dans la boîte de dialogue **Ajouter un nouvel élément**, dans le volet **Types de projets**.  
  
### Affichage de modèles dans des catégories parentes  
 Vous pouvez permettre aux modèles des sous\-catégories d'être affichés dans leur catégorie parente à l'aide de l'élément `NumberOfParentCategoriesToRollUp` du fichier .vstemplate.  Ces étapes sont identiques pour les modèles de projet et les modèles d'élément.  
  
##### Pour afficher les modèles dans les catégories parentes  
  
1.  Localisez le fichier .zip qui contient le modèle.  
  
2.  Extrayez le fichier zip.  
  
3.  Ouvrez le fichier .vstemplate dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Dans l'élément `TemplateData`, ajoutez un élément `NumberOfParentCategoriesToRollUp`.  Par exemple, le code suivant fait apparaître le modèle dans sa catégorie parente, mais pas plus haut dans la hiérarchie.  
  
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
  
6.  Sélectionnez les fichiers présents dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers**, puis sur **Dossier compressé**.  Les fichiers sont compressés dans un fichier .zip.  
  
7.  Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.  
  
8.  Mettez le nouveau fichier .zip dans le répertoire duquel vous avez supprimé le fichier .zip.  
  
## Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp \(modèles Visual Studio\)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md)   
 [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md)