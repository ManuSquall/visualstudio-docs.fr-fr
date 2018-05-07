---
title: Mettre à jour des modèles de projet et d’élément existants dans Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f5cf764f76d72b17128c46f2b7ec16ffcf4153cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-update-existing-templates"></a>Guide pratique pour mettre à jour des modèles existants

Une fois que vous avez créé un modèle et compressé les fichiers dans un fichier *.zip*, vous pouvez modifier le modèle. Vous pouvez modifier les fichiers manuellement dans le modèle ou exporter un nouveau modèle à partir d'un projet basé sur le modèle.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Utilisation de l’Assistant Exportation de modèle pour mettre à jour un modèle de projet existant

Visual Studio fournit un **Assistant Exportation de modèle** utilisable pour mettre à jour un modèle existant :

1. Ouvrez la boîte de dialogue **Nouveau projet** en choisissant **Fichier** > **Nouveau** > **Projet**.

1. Sélectionnez le modèle que vous souhaitez mettre à jour, entrez le nom et l’emplacement de votre projet, puis choisissez **OK**.

1. Modifiez le projet dans Visual Studio.

1. Dans le menu **Projet**, choisissez **Exporter le modèle**.

    L’Assistant **Exportation de modèle** s’ouvre.

1. Suivez les instructions de l’Assistant pour exporter le modèle en tant que fichier *.zip*.

1. (Facultatif) Pour ajouter le modèle à la boîte de dialogue **Nouveau projet**, placez le fichier *.zip* dans le répertoire suivant : *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*. Vous devez effectuer cette étape si vous n’avez pas sélectionné l’option **Importer automatiquement le modèle dans Visual Studio** dans l’**Assistant Exportation de modèle**.

1. Supprimez l’ancien fichier *.zip* du modèle.

## <a name="manually-update-an-existing-template"></a>Mettre à jour manuellement un modèle existant

Vous pouvez mettre à jour un modèle existant sans utiliser l’**Assistant Exportation de modèle**, en modifiant les fichiers contenus dans le fichier *.zip* compressé.

### <a name="to-manually-update-an-existing-template"></a>Pour mettre à jour manuellement un modèle existant

1. Localisez le fichier *.zip* qui contient le modèle. Les modèles de projet utilisateur se trouvent dans *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

1. Extrayez le fichier *.zip*.

1. Modifiez ou supprimez les fichiers modèles actuels ou ajoutez de nouveaux fichiers au modèle.

1. Ouvrez, modifiez et enregistrez le fichier XML *.vstemplate* pour prendre en charge le comportement mis à jour ou les nouveaux fichiers.

    Pour plus d’informations sur le schéma *.vstemplate*, consultez [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md). Pour plus d’informations sur ce que vous pouvez paramétrer dans les fichiers sources, consultez [Paramètres de modèle](../ide/template-parameters.md).

1. Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit pour faire apparaître un menu contextuel, puis choisissez **Envoyer vers** > **Dossier compressé**.

    Les fichiers que vous avez sélectionnés sont compressés dans un fichier *.zip*.

1. Placez le nouveau fichier *.zip* dans le même répertoire que l’ancien fichier *.zip*.

1. Supprimez les fichiers de modèles extraits et l’ancien fichier *.zip* de modèle.

## <a name="see-also"></a>Voir aussi

- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Guide pratique pour créer des Starter Kits](../ide/how-to-create-starter-kits.md)