---
title: "Guide pratique pour mettre à jour des modèles existants | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28ae63c6dba9d352025d5c87d838772a81cf989d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-existing-templates"></a>Guide pratique pour mettre à jour des modèles existants
Vous pouvez modifier un modèle que vous avez créé et dont vous avez compressé les fichiers dans un fichier .zip. Vous pouvez modifier les fichiers manuellement dans le modèle ou exporter un nouveau modèle à partir d'un projet basé sur le modèle.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Utilisation de l’Assistant Exportation de modèle pour mettre à jour un modèle existant  
Visual Studio fournit un Assistant **Exportation de modèle** qui peut être utilisé pour mettre à jour un modèle existant.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Pour utiliser l'exportation de modèle afin de mettre à jour un modèle existant  
  
1.  Ouvrez la boîte de dialogue **Nouveau projet** en choisissant **Fichier**, **Nouveau**, **Projet**.  
  
2.  Sélectionnez le modèle que vous souhaitez mettre à jour, entrez le nom et l’emplacement de votre projet, puis choisissez **OK**.  
  
3.  Modifiez le projet dans Visual Studio.  
  
4.  Dans le menu **Projet**, choisissez **Exporter le modèle**.  

    L’Assistant **Exportation de modèle** s’ouvre.  

5.  Suivez les instructions de l’Assistant pour exporter le modèle sous la forme d’un fichier .zip.  

6.  Supprimez l’ancien fichier .zip du modèle.  
  
## <a name="manually-updating-an-existing-template"></a>Mise à jour manuelle d’un modèle existant  
Pour mettre à jour un modèle existant hors de Visual Studio, vous devez modifier les fichiers inclus dans le fichier .zip compressé.  
  
#### <a name="to-manually-update-an-existing-template"></a>Pour mettre à jour manuellement un modèle existant  
  
1.  Localisez le fichier .zip qui contient le modèle. Par défaut, ce fichier se trouve dans %USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates\.  
  
2.  Extrayez le fichier zip.  
  
3.  Modifiez ou supprimez les fichiers modèles actuels ou ajoutez de nouveaux fichiers au modèle.  
  
4.  Ouvrez, modifiez et enregistrez le fichier XML .vstemplate pour gérer le comportement mis à jour ou les nouveaux fichiers.  

    Pour plus d’informations sur le schéma .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Pour plus d’informations sur ce que vous pouvez paramétrer dans les fichiers sources, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
5.  Sélectionnez les fichiers présents dans votre modèle, cliquez avec le bouton droit, choisissez **Envoyer vers**, puis **Dossier compressé**.  

    Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
6.  Placez le nouveau fichier .zip dans le même répertoire que l'ancien fichier .zip.  
  
7.  Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.  
  
8.  Démarrez une instance avec élévation de privilèges de l’invite de commandes développeur :  

  1. Dans le menu Démarrer, accédez à **Visual Studio \<version\>**, **Invite de commandes développeur**.  

  2. Dans le menu contextuel (clic droit), choisissez **Plus**, **Exécuter en tant qu’administrateur**.  
  
9. Exécutez la commande suivante : `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Voir aussi  
[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
[Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
[Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Paramètres de modèle](../ide/template-parameters.md)   
[Guide pratique pour créer des Starter Kits](../ide/how-to-create-starter-kits.md)