---
title: Désinstaller Visual Studio
titleSuffix: ''
description: Découvrez comment désinstaller Visual Studio, étape par étape.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd21f01f89cb4fe4507775670968496cbb5f99f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115017"
---
# <a name="uninstall-visual-studio"></a>Désinstaller Visual Studio

Cette page vous guide dans la désinstallation de Visual Studio, notre suite intégrée d’outils de productivité pour les développeurs.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Désinstaller Visual Studio pour Mac](/visualstudio/mac/uninstall).

::: moniker range="vs-2017"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant la Mise à jour anniversaire Windows 10 ou une version ultérieure, sélectionnez **Démarrer**, puis faites défiler la liste jusqu’à la lettre **V**, où se trouve **Visual Studio Installer**.

     ![Installateur de studio visuel](media/locate-the-visual-studio-installer.png "Localiser l’installateur Microsoft Visual Studio")

   > [!NOTE]
   > Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée. Choisissez ensuite **Plus**, puis **Désinstaller**.

     ![Désinstaller Visual Studio 2017](media/uninstall-visual-studio.png "Désinstaller Visual Studio 2017")

1. Cliquez sur **OK** pour confirmer votre choix.

Si vous changez d’avis par la suite et que vous voulez réinstaller Visual Studio 2017, redémarrez Visual Studio Installer, puis cliquez sur **Installer** à partir de l’écran de sélection.

## <a name="uninstall-visual-studio-installer"></a>Désinstaller Visual Studio Installer

Pour supprimer complètement toutes les installations de Visual Studio 2017 et de Visual Studio Installer sur votre machine, désinstallez-les à partir de Applications et fonctionnalités.

1. Dans Windows 10, tapez **Applications et fonctionnalités** dans la zone « Tapez ici pour effectuer une recherche ».
1. Recherchez **Microsoft Visual Studio 2017** (ou **Visual Studio 2017**).
1. Choisissez **Désinstaller**.
1. Ensuite, recherchez **Microsoft Visual Studio Installer**.
1. Choisissez **Désinstaller**.

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Ouvrez l’installateur visual studio](media/vs-2019/vs-installer-windows-start.png "Ouvrez l’installateur visual studio")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée. Choisissez ensuite **Plus**, puis **Désinstaller**.

     ![Uninstall Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Uninstall Visual Studio 2019")

1. Cliquez sur **OK** pour confirmer votre choix.

     ![Désinstaller la confirmation visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Confirmez que vous souhaitez désinstaller Visual Studio 2019")

Si vous changez d’avis ultérieurement et voulez réinstaller Visual Studio 2019, redémarrez Visual Studio Installer, choisissez l’onglet **Disponibles**, choisissez l’édition de Visual Studio à installer, puis sélectionnez ** Installer**.

## <a name="uninstall-visual-studio-installer"></a>Désinstaller Visual Studio Installer

Pour supprimer toutes les installations de Visual Studio 2019 et de Visual Studio Installer sur votre machine, désinstallez-les à partir de Applications et fonctionnalités.

1. Dans Windows 10, tapez **Applications et fonctionnalités** dans la zone « Tapez ici pour effectuer une recherche ».
1. Recherchez **Visual Studio 2019**.
1. Choisissez **Désinstaller**.
1. Ensuite, recherchez **Microsoft Visual Studio Installer**.
1. Choisissez **Désinstaller**.

::: moniker-end

## <a name="remove-all-files"></a>Supprimer tous les fichiers

Si vous rencontrez une erreur catastrophique et ne pouvez pas désinstaller Visual Studio en utilisant les instructions précédentes, il existe une option de « dernier recours » que vous pouvez envisager d’utiliser à la place. Pour plus d’informations sur la façon de supprimer complètement tous les fichiers d’installation visual studio et les informations sur le produit, consultez la page [Supprimer Visual Studio.](remove-visual-studio.md)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
