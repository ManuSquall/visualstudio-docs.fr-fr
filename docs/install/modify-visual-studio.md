---
title: Modifier les charges de travail Visual Studio, les composants, les & les modules linguistiques
titleSuffix: ''
description: Découvrez comment modifier Visual Studio, étape par étape.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperf-fy21q2
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 30b28af562e5dbaa8c05624f6cc9d531cf652419
ms.sourcegitcommit: 8d3d51042261df603487169a7a008fe8f71404ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109501770"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Modifier les charges de travail, les composants et les modules linguistiques de Visual Studio

::: moniker range="vs-2019"

Il est facile de modifier Visual Studio afin d’inclure uniquement ce que vous voulez, quand vous le voulez. Pour cela, ouvrez Visual Studio Installer pour ajouter ou supprimer des composants et des charges de travail.

::: moniker-end

::: moniker range="vs-2017"

Nous avons simplifié le travail de personnalisation des tâches Visual Studio, mais aussi de Visual Studio à proprement parler. Pour ce faire, ouvrez le nouveau Visual Studio Installer et apportez les modifications souhaitées.

::: moniker-end

## <a name="prerequisites"></a>Prérequis

+ Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ Les procédures suivantes supposent que vous disposez d’une connexion Internet. Pour plus d’informations sur la façon de modifier une installation [hors connexion](create-an-offline-installation-of-visual-studio.md) de Visual Studio précédemment créée, consultez la page [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md) et la page [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

## <a name="launch-the-installer"></a>Exécutez le programme d’installation

Pour apporter des modifications à votre installation, vous devez lancer le programme d’installation de Visual Studio.

::: moniker range="vs-2017"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Visual Studio Installer](media/locate-the-visual-studio-installer.png "Localiser le programme d’installation de Microsoft Visual Studio")

     >[!TIP]
     >Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Ouvrez le programme d’installation, puis choisissez **modifier**.

     ![Lancer ou modifier Visual Studio](media/modify-visual-studio.png "Modifier Visual Studio 2017")

     > [!IMPORTANT]
     > Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour si vous le souhaitez. Cliquez sur **Plus**, puis choisissez **Modifier**.
     >
     > ![Mettre à jour ou modifier Visual Studio](media/modify-or-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

     Dans le menu Démarrer de Windows, vous pouvez rechercher « programme d’installation ».

     ![Visual Studio Installer](media/vs-2019/visual-studio-installer.png "Rechercher le Visual Studio Installer")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée, puis choisissez **Modifier**.

     ![Choisissez Visual Studio Edition, puis modifiez](media/vs-2019/vs-installer-modify.png "Choisissez Visual Studio 2019 Edition, puis modifiez")

     > [!IMPORTANT]
     > Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour, si vous le souhaitez. Choisissez **plus**, puis **modifier**.
     >
     > ![Mettre à jour ou modifier Visual Studio](media/vs-2019/modify-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2019")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Modifier les charges de travail ou les composants individuels

::: moniker range="vs-2017"

 Les [charges de travail](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

1. Dans la Visual Studio Installer, choisissez l’onglet **charges de travail** , puis sélectionnez ou désélectionnez les charges de travail de votre choix.

   Sinon, si vous ne souhaitez pas utiliser les charges de travail pour personnaliser votre installation de Visual Studio, choisissez l’onglet **composants individuels** et sélectionnez les composants souhaités, puis suivez les invites.

    ![Boîte de dialogue de configuration de Visual Studio 2017](media/modify-workloads.png "Choisir une charge de travail dans Visual Studio 2019")

1. Indiquez si vous voulez accepter l’option **Installer pendant le téléchargement** par défaut ou l’option **Tout télécharger, puis installer**.

    ![Options d’installation de Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Choisir d’installer pendant le téléchargement ou le téléchargement d’abord et l’installation ultérieure")

    L’option « Tout télécharger, puis installer » s’avère pratique si vous voulez d’abord tout télécharger pour installer plus tard.

1. Choisissez **Modifier**.

1. Si vous le souhaitez, choisissez l’onglet **charges de travail** , puis sélectionnez ou désélectionnez les charges de travail de votre choix.


1. Une fois les nouvelles charges de travail installées, choisissez **lancer** à partir de la Visual Studio installer pour ouvrir Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Les charges de travail contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

 > [!TIP]
>Pour plus d’informations sur les outils et les groupes de composants dont vous avez besoin pour le développement, consultez [charges de travail Visual Studio](https://visualstudio.microsoft.com/vs/#workloads).

1. Dans la Visual Studio Installer, choisissez l’onglet **charges de travail** , puis sélectionnez ou désélectionnez les charges de travail de votre choix.

    ![Boîte de dialogue d’installation de Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Choisir une charge de travail dans Visual Studio 2019")

1. Indiquez si vous voulez accepter l’option **Installer pendant le téléchargement** par défaut ou l’option **Tout télécharger, puis installer**.

    ![Options d’installation de Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Choisir d’installer pendant le téléchargement ou le téléchargement d’abord et l’installation ultérieure")

    L’option « Tout télécharger, puis installer » s’avère pratique si vous voulez d’abord tout télécharger pour installer plus tard.

1. Choisissez **Modifier**.

1. Une fois les nouvelles charges de travail installées, choisissez **lancer** à partir de la Visual Studio installer pour ouvrir Visual Studio.

::: moniker-end


>[!TIP]
> Pour plus d’informations sur le composant SQL Server Data Tools (SSDT), consultez [Télécharger et installer SSDT pour Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Modifier les modules linguistiques

Par défaut, le programme d’installation correspond à la langue du système d’exploitation lorsqu’il s’exécute pour la première fois. Toutefois, vous pouvez modifier la langue chaque fois que vous le souhaitez. 

Pour cela, procédez de la façon suivante :
1. Choisissez l’onglet **modules linguistiques** dans la Visual Studio installer.
2. Sélectionnez la langue de votre choix.
3. Suivez les invites.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Liste des ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
