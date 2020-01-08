---
title: Réparer Visual Studio
titleSuffix: ''
description: Découvrez comment réparer une installation de Visual Studio 2017.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 255995f7ca660d36ae40a6a8fead4b3ea5d70424
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594550"
---
# <a name="repair-visual-studio"></a>Réparer Visual Studio

::: moniker range="vs-2017"

Il peut arriver que votre installation Visual Studio soit endommagée ou corrompue. Une réparation permet de résoudre ces problèmes.

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant la Mise à jour anniversaire Windows 10 ou une version ultérieure, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** pour l’afficher comme **Visual Studio Installer**.

   > [!NOTE]
   > Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.
   >
   > Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Dans le programme d’installation, choisissez **Plus**, puis choisissez **Réparer**.

    ![Réparez Visual Studio à partir de l’Visual Studio Installer](media/repair-visual-studio.png "Réparez Visual Studio à partir de l’Visual Studio Installer")

   > [!NOTE]
   > La réparation de Visual Studio réinitialisera l’environnement. Les personnalisations locales comme les extensions par utilisateur installées sans élévation, les paramètres utilisateurs et les profils seront supprimées. Vos paramètres synchronisés tels que les thèmes, les couleurs et les combinaisons de touches seront restaurés.
   >

   > [!TIP]
   > L’option **Réparer** n’apparaît que pour les instances installées de Visual Studio. Si vous ne voyez pas l’option **Réparer**, c’est sans doute que vous avez sélectionné **Plus** dans une version présentée comme « Disponible » et non « Installé » dans Visual Studio Installer.

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Ouvrez le Visual Studio Installer](media/vs-2019/vs-installer-windows-start.png "Ouvrez le Visual Studio Installer")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée. Cliquez ensuite sur **Plus**, puis choisissez **Réparer**.

     ![Réparer Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Réparer Visual Studio 2019")

   > [!NOTE]
   > La réparation de Visual Studio réinitialisera l’environnement. Les personnalisations locales comme les extensions par utilisateur installées sans élévation, les paramètres utilisateurs et les profils seront supprimées. Vos paramètres synchronisés tels que les thèmes, les couleurs et les combinaisons de touches seront restaurés.
   >

   > [!TIP]
   > L’option **Réparer** n’apparaît que pour les instances installées de Visual Studio. Si vous ne voyez pas l’option **Réparer**, c’est sans doute que vous avez sélectionné **Plus** dans une version présentée comme « Disponible » et non « Installé » dans Visual Studio Installer.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Mettre à jour Visual Studio](update-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
* [Résolution des problèmes d’installation et de mise à niveau de Visual Studio](troubleshooting-installation-issues.md)
