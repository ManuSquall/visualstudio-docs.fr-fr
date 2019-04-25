---
title: Récupération automatique, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59a28d73677011ef2de3ce4dd844757108b317ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790887"
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