---
title: 'Procédure : mettre à jour des modèles existants | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670586"
---
# <a name="how-to-update-existing-templates"></a>Comment : mettre à jour des modèles existants
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier un modèle que vous avez créé et dont vous avez compressé les fichiers dans un fichier .zip. Vous pouvez modifier les fichiers manuellement dans le modèle ou exporter un nouveau modèle à partir d'un projet basé sur le modèle.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Utilisation de l'Assistant Exportation de modèle pour mettre à jour un modèle existant
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit un Assistant **Exportation de modèle** qui peut être utilisé pour mettre à jour un modèle existant.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>Pour utiliser l'exportation de modèle afin de mettre à jour un modèle existant

1. Dans le menu **Fichier** , cliquez sur **Nouveau** , puis cliquez sur **Nouveau projet**.

2. Sélectionnez le modèle que vous souhaitez mettre à jour, entrez le nom et l'emplacement de votre projet temporaire, puis cliquez sur **OK**.

3. Modifiez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. Dans le menu **Fichier**, cliquez sur **Exporter le modèle**, puis utilisez l’Assistant **Exportation de modèle** pour créer un modèle.

5. Une fois que le modèle mis à jour est compressé dans un fichier .zip, supprimez l'ancien fichier .zip du modèle.

## <a name="manually-updating-an-existing-template"></a>Mise à jour manuelle d'un modèle existant
 Pour mettre à jour un modèle existant hors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], modifiez les fichiers inclus dans le fichier .zip compressé.

#### <a name="to-manually-update-an-existing-template"></a>Pour mettre à jour manuellement un modèle existant

1. Localisez le fichier .zip qui contient le modèle. Par défaut, ce fichier se trouve dans \Mes documents\Visual Studio *Version*\My Exported Templates\\.

2. Extrayez le fichier zip.

3. Modifiez ou supprimez les fichiers modèles actuels ou ajoutez de nouveaux fichiers au modèle.

4. Ouvrez, modifiez et enregistrez le fichier XML .vstemplate pour gérer le comportement mis à jour ou les nouveaux fichiers. Pour plus d’informations sur le schéma .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Pour plus d’informations sur ce que vous pouvez paramétrer dans les fichiers sources, consultez [Paramètres de modèle](../ide/template-parameters.md).

5. Sélectionnez les fichiers présents dans votre modèle, cliquez avec le bouton droit, cliquez sur **Envoyer vers**, puis sur **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.

6. Placez le nouveau fichier .zip dans le même répertoire que l'ancien fichier .zip.

7. Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.

8. Démarrez (comme administrateur) une instance de l’invite de commandes développeur (dans le menu Démarrer, sous **Visual Studio 2010/Visual Studio Tools/Invite de commandes développeur**).

9. Exécutez la commande suivante : `devenv /installvstemplates`.

## <a name="see-also"></a>Voir aussi
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md) [création de modèles de projet et d’élément modèle de](../ide/creating-project-and-item-templates.md) [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md) [paramètres de modèle](../ide/template-parameters.md) [Comment : créer des Starter Kits](../ide/how-to-create-starter-kits.md)
