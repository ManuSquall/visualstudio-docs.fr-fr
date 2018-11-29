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
ms.openlocfilehash: 804ea0baa47925e35a282a615598ea66c843b911
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388800"
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options

Utilisez cette page de la boîte de dialogue **Options** pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Vous pouvez aussi spécifier si vous souhaitez restaurer les fichiers modifiés en cas d’arrêt inattendu de Visual Studio.

Pour accéder à cette boîte de dialogue, dans le menu **Outils**, sélectionnez **Options**, puis **Environnement** > **Récupération automatique**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

**Enregistrer les informations de récupération automatique toutes les [n] minutes**

Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers déjà enregistrés, une copie du fichier est enregistrée dans *%USERPROFILE%\Documents\Visual Studio\\[version]\Backup Files\\[nom_projet]*. Si le fichier est nouveau et que vous ne l’avez pas encore enregistré, il est enregistré automatiquement sous un nom de fichier généré de manière aléatoire.

**Conserver les informations de récupération automatique pendant [n] jours**

Utilisez cette option pour spécifier la durée de conservation des fichiers créés pour la récupération automatique par Visual Studio.

### <a name="see-also"></a>Voir aussi

- [Boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md)