---
title: Mettre à jour des modèles d’élément de projet existants
description: Découvrez comment utiliser l’Assistant exportation de modèle et d’autres processus manuels pour mettre à jour les modèles d’élément de projet que vous avez déjà créés.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 12005ce6c280a828aa59c281803cb431cc08587a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869087"
---
# <a name="how-to-update-existing-templates"></a>Guide pratique pour mettre à jour des modèles existants

Une fois que vous avez créé un modèle et compressé les fichiers dans un fichier *.zip*, vous pouvez modifier le modèle. Vous pouvez le faire en modifiant les fichiers manuellement dans le modèle ou en exportant un nouveau modèle à partir d’un projet basé sur le modèle.

## <a name="use-the-export-template-wizard"></a>Utiliser l’Assistant Exportation de modèle

Visual Studio fournit un **Assistant exportation de modèle** qui peut être utilisé pour mettre à jour un modèle existant :

1. Choisissez **fichier**  >  **nouveau**  >  **projet** dans la barre de menus.

1. Sélectionnez le modèle que vous voulez mettre à jour et continuez dans les étapes pour créer le nouveau projet.

1. Modifiez le projet dans Visual Studio. Par exemple, changez le type de sortie ou ajoutez un nouveau fichier au projet.

1. Dans le menu **projet** , choisissez **Exporter le modèle**.

    L’Assistant **Exportation de modèle** s’ouvre.

1. Suivez les instructions de l’Assistant pour exporter le modèle en tant que fichier *.zip*.

1. Facultatif Placez le fichier *. zip* dans le répertoire suivant : *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates* pour le rendre disponible pour la sélection. Vous devez effectuer cette étape si vous n’avez pas sélectionné l’option **Importer automatiquement le modèle dans Visual Studio** dans l’**Assistant Exportation de modèle**.

1. Supprimez l’ancien fichier *.zip* du modèle.

## <a name="manually-update-an-existing-template"></a>Mettre à jour manuellement un modèle existant

Vous pouvez mettre à jour un modèle existant sans utiliser l’**Assistant Exportation de modèle**, en modifiant les fichiers contenus dans le fichier *.zip* compressé.

### <a name="to-manually-update-an-existing-template"></a>Pour mettre à jour manuellement un modèle existant

1. Localisez le fichier *. zip* qui contient le modèle. Les modèles de projet utilisateur se trouvent dans *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*.

1. Extrayez le fichier *. zip* .

1. Modifiez ou supprimez les fichiers modèles actuels ou ajoutez de nouveaux fichiers au modèle.

1. Ouvrez, modifiez et enregistrez le fichier XML *.vstemplate* pour prendre en charge le comportement mis à jour ou les nouveaux fichiers.

    Pour plus d’informations sur le schéma *.vstemplate*, consultez [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md). Pour plus d’informations sur ce que vous pouvez paramétrer dans les fichiers sources, consultez [paramètres de modèle](../ide/template-parameters.md).

1. Sélectionnez les fichiers dans votre modèle, puis dans le menu contextuel, cliquez avec le bouton droit et choisissez **Envoyer vers** le  >  **dossier compressé**.

    Les fichiers que vous avez sélectionnés sont compressés dans un fichier *. zip* .

1. Placez le nouveau fichier *. zip* dans le même répertoire que l’ancien fichier *. zip* .

1. Supprimez les fichiers de modèles extraits et l’ancien fichier *. zip* du modèle.

## <a name="see-also"></a>Voir aussi

- [Personnaliser des modèles](../ide/customizing-project-and-item-templates.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Paramètres de modèle](../ide/template-parameters.md)
