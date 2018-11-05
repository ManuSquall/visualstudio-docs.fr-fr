---
title: Récupération automatique, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5ad6259ede32304cfe15ef4e79c6b3e56dbd9d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143305"
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options

Utilisez cette page de la boîte de dialogue **Options** pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Cette page vous permet aussi de spécifier si vous souhaitez restaurer les fichiers modifiés en cas d’arrêt inattendu de Visual Studio.

Pour accéder à cette boîte de dialogue, dans le menu **Outils**, sélectionnez **Options**, puis **Environnement** > **Récupération automatique**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

**Enregistrer les informations de récupération automatique toutes les [n] minutes**

Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers déjà enregistrés, une copie du fichier est enregistrée dans *%USERPROFILE%\Documents\Visual Studio \<version>\Fichiers de sauvegarde\\<projectname>*. Si le fichier est nouveau et que vous ne l’avez pas encore enregistré, il est enregistré automatiquement sous un nom de fichier généré de manière aléatoire.

**Conserver les informations de récupération automatique pendant [n] jours**

Utilisez cette option pour spécifier la durée de conservation des fichiers créés pour la récupération automatique par Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Options, boîte de dialogue](../../ide/reference/options-dialog-box-visual-studio.md)