---
title: Désinstaller Visual Studio
titleSuffix: ''
description: Découvrez comment désinstaller Visual Studio, étape par étape.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7d34a5be9598682982c3918aafec7725e59d6f92
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306785"
---
# <a name="uninstall-visual-studio"></a>Désinstaller Visual Studio

Cette page vous guide dans la désinstallation de Visual Studio, notre suite intégrée d’outils de productivité pour les développeurs.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Désinstaller Visual Studio pour Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Si vous rencontrez des problèmes avec votre instance de Visual Studio, essayez l’outil de **réparation** . Pour plus d’informations, consultez [réparer Visual Studio](../install/repair-visual-studio.md). 
>
> Si vous souhaitez modifier l’emplacement de certains de vos fichiers Visual Studio, il est possible de le faire sans désinstaller votre instance actuelle. Pour plus d’informations, consultez [Sélectionner les emplacements d’installation dans Visual Studio](../install/change-installation-locations.md).
>
> Pour obtenir des conseils généraux sur la résolution des problèmes, consultez [résoudre les problèmes d’installation et de mise à niveau de Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant la Mise à jour anniversaire Windows 10 ou une version ultérieure, sélectionnez **Démarrer**, puis faites défiler la liste jusqu’à la lettre **V**, où se trouve **Visual Studio Installer**.

     ![Visual Studio Installer](media/locate-the-visual-studio-installer.png "Localiser le programme d’installation de Microsoft Visual Studio")

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

::: moniker range=">=vs-2019"

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

     Dans le menu Démarrer de Windows, vous pouvez rechercher « programme d’installation ».

     ![Visual Studio Installer](media/vs-2019/visual-studio-installer.png "Rechercher le Visual Studio Installer")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée. Choisissez ensuite **Plus**, puis **Désinstaller**.

     ![Désinstaller Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Désinstaller Visual Studio 2019")

1. Cliquez sur **OK** pour confirmer votre choix.

     ![Désinstaller la confirmation de Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Confirmer que vous souhaitez désinstaller Visual Studio 2019")

Si vous changez d’avis par la suite et que vous voulez réinstaller Visual Studio 2019 ou 2022, redémarrez l’Visual Studio Installer, choisissez l’onglet **disponible** , choisissez l’édition de Visual Studio que vous souhaitez installer, puis sélectionnez **installer**.

## <a name="uninstall-visual-studio-installer"></a>Désinstaller Visual Studio Installer

Pour supprimer toutes les installations de Visual Studio 2019, Visual Studio 2022 et du Visual Studio Installer de votre ordinateur, désinstallez-le à partir des applications & des fonctionnalités.

1. Dans Windows 10, tapez **Applications et fonctionnalités** dans la zone « Tapez ici pour effectuer une recherche ».
1. Recherchez **Visual studio 2019** ou **Visual Studio 2022**.
1. Choisissez **Désinstaller**.
1. Ensuite, recherchez **Microsoft Visual Studio Installer**.
1. Choisissez **Désinstaller**.

::: moniker-end

## <a name="remove-all-files"></a>Supprimer tous les fichiers

Si vous rencontrez une erreur catastrophique et que vous ne pouvez pas désinstaller Visual Studio à l’aide des instructions précédentes, vous pouvez envisager d’utiliser à la place une option « dernier recours ». Pour plus d’informations sur la suppression complète de tous les fichiers d’installation et informations sur les produits de Visual Studio, consultez la page [supprimer Visual Studio](remove-visual-studio.md) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
