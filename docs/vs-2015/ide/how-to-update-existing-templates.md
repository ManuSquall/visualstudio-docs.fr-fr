---
title: 'Comment : mettre à jour des modèles existants | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa7c6f534756298006e07d287b118edfd4944717
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242279"
---
# <a name="how-to-update-existing-templates"></a>Comment : mettre à jour des modèles existants
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier un modèle que vous avez créé et dont vous avez compressé les fichiers dans un fichier .zip. Vous pouvez modifier les fichiers manuellement dans le modèle ou exporter un nouveau modèle à partir d'un projet basé sur le modèle.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Utilisation de l'Assistant Exportation de modèle pour mettre à jour un modèle existant  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit un **Export Template** Assistant qui peut être utilisé pour mettre à jour un modèle existant.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Pour utiliser l'exportation de modèle afin de mettre à jour un modèle existant  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouveau** , puis cliquez sur **Nouveau projet**.  
  
2.  Sélectionnez le modèle que vous souhaitez mettre à jour, entrez un nom et un emplacement pour votre projet temporaire, puis cliquez sur **OK**.  
  
3.  Modifiez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Sur le **fichier** menu, cliquez sur **Export Template**et utiliser le **Export Template** Assistant pour créer un nouveau modèle.  
  
5.  Une fois que le modèle mis à jour est compressé dans un fichier .zip, supprimez l'ancien fichier .zip du modèle.  
  
## <a name="manually-updating-an-existing-template"></a>Mise à jour manuelle d'un modèle existant  
 Pour mettre à jour un modèle existant hors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], modifiez les fichiers inclus dans le fichier .zip compressé.  
  
#### <a name="to-manually-update-an-existing-template"></a>Pour mettre à jour manuellement un modèle existant  
  
1.  Localisez le fichier .zip qui contient le modèle. Par défaut, ce fichier se trouve dans documents\Visual Studio *Version*\My Exported Templates\\.  
  
2.  Extrayez le fichier zip.  
  
3.  Modifiez ou supprimez les fichiers modèles actuels ou ajoutez de nouveaux fichiers au modèle.  
  
4.  Ouvrez, modifiez et enregistrez le fichier XML .vstemplate pour gérer le comportement mis à jour ou les nouveaux fichiers. Pour plus d’informations sur le schéma .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Pour plus d’informations sur ce que vous pouvez paramétrer dans les fichiers sources, consultez [paramètres de modèle](../ide/template-parameters.md)  
  
5.  Sélectionnez les fichiers dans votre modèle, avec le bouton droit, cliquez sur **envoyer vers**, puis cliquez sur **dossier compressé (zippé)**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
6.  Placez le nouveau fichier .zip dans le même répertoire que l'ancien fichier .zip.  
  
7.  Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.  
  
8.  Démarrer (en tant qu’administrateur) une instance de l’invite de commandes développeur (dans le menu Démarrer, sous **Visual Studio 2010 / invite de commandes de Visual Studio Tools/développeur**).  
  
9. Exécutez la commande suivante : `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Guide pratique pour créer des Starter Kits](../ide/how-to-create-starter-kits.md)



