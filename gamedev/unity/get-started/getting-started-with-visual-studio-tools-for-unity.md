---
title: Bien démarrer avec Visual Studio Tools pour Unity | Microsoft Docs
description: Découvrez comment installer et configurer Visual Studio pour le développement Unity.
ms.custom: ''
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 791f25b61c86f0115c225d505bdb1edb07869961
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782606"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Prise en main de Visual Studio et Unity

> [!NOTE]
> Ce guide part du principe que vous avez déjà installé Unity à l’aide du programme Unity Hub. Si vous débutez avec Unity, nous vous recommandons de consulter Unity Learn et de terminer le [parcours d’apprentissage Unity Essentials](https://learn.unity.com/pathway/unity-essentials) en premier.

## <a name="install-unity-support-for-visual-studio"></a>Installer la prise en charge d’Unity pour Visual Studio

Outils Visual Studio pour Unity est une extension gratuite qui assure la prise en charge de l’écriture et du débogage de C#, etc. Pour obtenir la liste complète des extensions incluses, consultez la [vue d’ensemble des outils pour Unity](./visual-studio-tools-for-unity.md) .

:::zone pivot="windows"

> [!NOTE]
> Ce guide d’installation est destiné à Visual Studio. Si vous utilisez Visual Studio Code, consultez la [documentation sur le développement Unity avec vs code](https://code.visualstudio.com/docs/other/unity).

1. [Téléchargez le programme d’installation de Visual Studio](/visualstudio/install/install-visual-studio.md)ou exécutez-le s’il est déjà installé.
2. Cliquez sur **Modifier** (s’il est déjà installé) ou **Installer** (pour les nouvelles installations) sur la version souhaitée de Visual Studio.
3. Dans l’onglet **charges de travail** , accédez à la section **jeux** et sélectionnez la charge **de travail développement de jeux avec Unity** .

    ![Zone de charge de travail développement de jeux avec Unity dans le programme d’installation](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Ce guide d’installation est destiné à Visual Studio pour Mac. Si vous utilisez Visual Studio Code, consultez la [documentation sur le développement Unity avec vs code](https://code.visualstudio.com/docs/other/unity).

Les outils pour Unity sont inclus dans l’installation de Visual Studio pour Mac et aucune étape d’installation distincte n’est requise. Vous pouvez le vérifier dans le menu **Visual Studio pour Mac > Extensions > développement de jeux** . **Les outils de Visual Studio pour Mac pour Unity** doivent être activés.

![Vue du gestionnaire d’extensions présentant les outils de Visual Studio pour Mac pour Unity activée](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Rechercher les mises à jour

Il est recommandé de conserver Visual Studio et Visual Studio pour Mac mis à jour pour disposer des derniers correctifs de bogues, fonctionnalités et prise en charge Unity. Cela ne nécessite pas de mise à jour des versions Unity.

:::zone pivot="windows"

1. Cliquez sur le menu **aide > Rechercher des mises à jour** .

    ![Menu Rechercher des mises à jour dans Visual Studio 2019](../media/vs/check-for-updates.png)

2. Si une mise à jour est disponible, le Visual Studio Installer affichera une nouvelle version. Cliquez sur le bouton **Mettre à jour**.

:::zone-end
:::zone pivot="macos"

1. Cliquez sur le menu **Visual Studio pour Mac > Rechercher les mises** à jour... pour ouvrir la boîte de dialogue de **mise à jour de Visual Studio** .
2. Si une mise à jour est disponible, cliquez sur le bouton **installer** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Configurer Unity pour utiliser Visual Studio

Par défaut, Unity doit déjà être configuré pour utiliser Visual Studio ou Visual Studio pour Mac comme éditeur de script. Vous pouvez le confirmer ou modifier l’éditeur de script externe pour une version spécifique de Visual Studio à partir de l’éditeur Unity.

:::zone pivot="windows"

1. Dans l’éditeur Unity, sélectionnez le menu **modifier > préférences** .
2. Sélectionnez l’onglet **outils externes** sur la gauche.
3. La liste déroulante de l' **éditeur de script externe** permet de choisir différentes installations de Visual Studio. Vous pouvez également cliquer sur **Parcourir...** dans la liste déroulante pour ajouter une version non répertoriée.

    ![Menu des préférences des outils externes de l’éditeur Unity sur Windows](../media/vs/preferences-external-tools.png)

4. Si **Parcourir…** a été sélectionné, accédez au répertoire **Common7/IDE** à l’intérieur de votre répertoire d’installation de Visual Studio, puis sélectionnez **devenv.exe**. Cliquez ensuite sur **ouvrir**.
5. Une fois Visual Studio sélectionné dans la liste **Éditeur de scripts externe**, vérifiez que la case **Attachement de l’éditeur** est cochée.
6. Fermez la boîte de dialogue **Préférences** pour terminer le processus de configuration.

:::zone-end
:::zone pivot="macos"

1. Dans l’éditeur Unity, sélectionnez le menu **unity > Preferences** .
2. Sélectionnez l’onglet **outils externes** sur la gauche.
3. La liste déroulante de l' **éditeur de script externe** permet de choisir différentes installations de Visual Studio. Vous pouvez également cliquer sur **Parcourir...** dans la liste déroulante pour ajouter une version non répertoriée.

    ![Menu des préférences des outils externes de l’éditeur Unity sur macOS](../media/vsm/preferences-external-tools.png)

4. Fermez la boîte de dialogue **Préférences** pour terminer le processus de configuration.

:::zone-end

## <a name="next-steps"></a>Étapes suivantes

 Pour savoir comment utiliser et déboguer votre projet Unity dans Visual Studio, consultez [utilisation de outils Visual Studio pour Unity](using-visual-studio-tools-for-unity.md).
