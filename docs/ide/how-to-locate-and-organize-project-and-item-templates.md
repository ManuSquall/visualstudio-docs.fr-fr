---
title: "Organiser les modèles dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c58bda5570be9cdb7fba7a8f90a282df7b7167a2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Guide pratique pour localiser et organiser les modèles de projet et d’élément

Les fichiers de modèle doivent être placés à un emplacement que Visual Studio reconnaît pour que les modèles s’affichent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**. Vous pouvez également créer des sous-catégories personnalisées à l’emplacement du modèle utilisateur, et les catégories apparaissent dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**.

## <a name="locate-templates"></a>Localiser les modèles

Les modèles installés et les modèles utilisateur sont stockés à deux emplacements différents.

### <a name="user-templates"></a>Modèles utilisateur

Si vous ajoutez un fichier compressé (.zip) incluant un fichier .vstemplate au répertoire du modèle utilisateur, le modèle apparaît dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**. Par défaut, les modèles utilisateur se trouvent dans :

- %USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates

- %USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates

Par exemple, le répertoire suivant contient les modèles de projet utilisateur pour C# :

   C:\Utilisateurs\Nom_Utilisateur\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\

> [!TIP]
> Vous pouvez définir l’emplacement des modèles utilisateur dans **Outils** > **Options** > **Projets et solutions** > **Emplacements**.

### <a name="installed-templates"></a>Modèles installés

Par défaut, les modèles installés avec Visual Studio se trouvent dans :

- \\*Répertoire_Installation_Visual Studio*\Common7\IDE\ItemTemplates\\*Langage de programmation*\\*ID de paramètres régionaux*

- \\*Répertoire_Installation_Visual Studio*\Common7\IDE\ProjectTemplates\\*Langage de programmation*\\*ID de paramètres régionaux*

Par exemple, le répertoire suivant contient les modèles d’élément Visual Basic pour l’anglais (LCID 1033) :

   \\*Répertoire_Installation_Visual_Studio*\Common7\IDE\ItemTemplates\VisualBasic\1033\

## <a name="organize-templates"></a>Organiser les modèles

Les catégories des boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** reflètent les structures de répertoires qui existent aux emplacements des modèles installés et utilisateur. Pour organiser les modèles utilisateur dans leurs propres catégories, ajoutez de nouveaux dossiers au répertoire du modèle utilisateur. Les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément** reflètent toutes les modifications que vous apportez à vos catégories de modèle utilisateur.

> [!NOTE]
> Vous ne pouvez pas créer de catégorie au niveau du langage de programmation. Vous ne pouvez créer une catégorie qu'à l'intérieur de chaque langage.

### <a name="to-create-new-user-project-template-categories"></a>Pour créer des catégories de modèles de projet utilisateur

1. Créez un sous-dossier dans le dossier du langage de programmation du répertoire des modèles de projet utilisateur. Par exemple, pour créer une catégorie **HelloWorld** pour les modèles de projet C#, créez le répertoire suivant :

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld\

1. Placez tous les modèles de cette catégorie dans le nouveau dossier.

1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**.

   La catégorie **HelloWorld** apparaît dans la boîte de dialogue **Nouveau projet**, sous **Installé** > **Visual C#**.

### <a name="to-create-new-user-item-template-categories"></a>Pour créer des catégories de modèles d’élément utilisateur

1. Créez un sous-dossier dans le dossier du langage de programmation du répertoire des modèles d’élément utilisateur. Par exemple, pour créer une catégorie **HelloWorld** pour les modèles d’élément C#, créez le répertoire suivant :

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld\

1. Placez tous les modèles de cette catégorie dans le nouveau dossier.

1. Créez un projet ou ouvrez un projet existant. Ensuite, dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.

   La catégorie **HelloWorld** apparaît dans la boîte de dialogue **Ajouter un nouvel élément**, sous **Installé** > **Éléments Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Afficher les modèles dans les catégories parentes

Vous pouvez permettre aux modèles des sous-catégories d'être affichés dans leur catégorie parente à l'aide de l'élément `NumberOfParentCategoriesToRollUp` du fichier .vstemplate. Ces étapes sont identiques pour les modèles de projet et les modèles d’élément.

#### <a name="to-display-templates-in-parent-categories"></a>Pour afficher les modèles dans les catégories parentes

1. Localisez le fichier .zip qui contient le modèle.

1. Extrayez le fichier zip.

1. Ouvrez le fichier .vstemplate dans Visual Studio.

1. Dans l'élément `TemplateData`, ajoutez un élément `NumberOfParentCategoriesToRollUp`. Par exemple, le code suivant fait apparaître le modèle dans sa catégorie parente, mais pas plus haut dans la hiérarchie.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Enregistrez et fermez le fichier .vstemplate. 

1. Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers** > **Dossier compressé**.

   Les fichiers sont compressés dans un fichier .zip.

1. Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.

1. Mettez le nouveau fichier .zip dans le répertoire duquel vous avez supprimé le fichier .zip.

## <a name="see-also"></a>Voir aussi

[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)  
[Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)  
[Élément NumberOfParentCategoriesToRollUp (modèles Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)  
[Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)
