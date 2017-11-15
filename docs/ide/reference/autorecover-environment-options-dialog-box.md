---
title: "Récupération automatique, Environnement, boîte de dialogue Options | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7cc057fbb19b51a6f30092b2f0edce747f03edfb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options
Utilisez cette page de la boîte de dialogue Options pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Cette page vous permet également de spécifier si les fichiers modifiés sont restaurés ou non quand l’environnement de développement intégré (IDE) s’arrête de façon inattendue. Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis la page **Récupération automatique** dans le dossier **Environnement**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Enregistrer les informations de récupération automatique toutes les \<n> minutes**  
 Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers déjà enregistrés, une copie du fichier est enregistrée dans \\...\Mes documents\Visual Studio \<*version*>\Fichiers de sauvegarde\\<*NomProjet*>. Si le fichier est nouveau et n’a pas été enregistré manuellement, le fichier est enregistré automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.  
  
 **Conserver les informations de récupération automatique pendant \<n> jours**  
 Utilisez cette option pour spécifier la durée de conservation des fichiers créés pour la récupération automatique par Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Options, boîte de dialogue](../../ide/reference/options-dialog-box-visual-studio.md)