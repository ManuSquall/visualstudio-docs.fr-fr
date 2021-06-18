---
title: Récupération automatique, Environnement, boîte de dialogue Options
description: Découvrez la boîte de dialogue récupération automatique, environnement, options et comment l’utiliser pour spécifier si les fichiers doivent ou non être sauvegardés automatiquement.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007e82ee7c1c2839ba266794432605f1f92a1669
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307789"
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options

Utilisez cette page de la boîte de dialogue **Options** pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Vous pouvez aussi spécifier si vous souhaitez restaurer les fichiers modifiés en cas d’arrêt inattendu de Visual Studio.

Pour accéder à cette boîte de dialogue, accédez à **Outils**  >  **options**  >    >  **récupération automatique** de l’environnement.

:::image type="content" source="media/autorecover-options.png" alt-text="Capture d’écran de la section récupération automatique de la boîte de dialogue Options":::

**Enregistrer les informations de récupération automatique toutes les [n] minutes**

::: moniker range=">=vs-2022"

Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers précédemment enregistrés, Visual Studio enregistre une copie du fichier dans ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [ProjectName]***. Si le fichier est nouveau et que vous ne l’avez pas encore enregistré, Visual Studio l’enregistre automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.

::: moniker-end

::: moniker range="vs-2019"

Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers précédemment enregistrés, Visual Studio 2019 version 16,2 et les versions ultérieures enregistrent une copie du fichier dans ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [ProjectName]***. Si le fichier est nouveau et que vous ne l’avez pas encore enregistré, Visual Studio l’enregistre automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.

> [!NOTE]
> Si vous utilisez Visual Studio 2019 version 16,1 ou antérieure, l’emplacement du fichier est *%USERPROFILE%\Documents\Visual Studio [version] \Sauvegarde Files \\ [ProjectName]*. Pour plus d’informations, consultez la page [historique des notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/) .

::: moniker-end

::: moniker range="vs-2017"

Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers précédemment enregistrés, Visual Studio 2017 enregistre une copie du fichier dans *%USERPROFILE%\Documents\Visual Studio [version] \Sauvegarde fichiers \\ [ProjectName]*. Si le fichier est nouveau et que vous ne l’avez pas encore enregistré, Visual Studio l’enregistre automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.

::: moniker-end

**Conserver les informations de récupération automatique pour [n] jours**

Utilisez cette option pour spécifier la durée de conservation des fichiers créés pour la récupération automatique par Visual Studio.

### <a name="see-also"></a>Voir aussi

- [Options (boîte de dialogue)](../../ide/reference/options-dialog-box-visual-studio.md)
