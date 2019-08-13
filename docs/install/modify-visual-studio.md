---
title: Modifier Visual Studio 2017
titleSuffix: ''
description: Découvrez comment modifier Visual Studio, étape par étape.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 07/31/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ad5b8a0c261ed967710480b0abd3a2b9d34f01ce
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681395"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modifier Visual Studio en ajoutant ou supprimant des charges de travail et des composants

::: moniker range="vs-2019"

Il est facile de modifier Visual Studio afin d’inclure uniquement ce que vous voulez, quand vous le voulez. Pour cela, ouvrez Visual Studio Installer pour ajouter ou supprimer des composants et des charges de travail.

::: moniker-end

::: moniker range="vs-2017"

Nous avons simplifié le travail de personnalisation des tâches Visual Studio, mais aussi de Visual Studio à proprement parler. Pour ce faire, démarrez le nouveau programme d’installation de Visual Studio et apportez les modifications souhaitées.

::: moniker-end

Voici comment procéder.

## <a name="modify-workloads"></a>Modifier les charges de travail

 Les charges de travail contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

>[!IMPORTANT]
>Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!TIP]
> La procédure suivante suppose que vous avez une connexion Internet. Pour plus d’informations sur la façon de modifier une [installation hors connexion](create-an-offline-installation-of-visual-studio.md) précédemment créée de Visual Studio, consultez la page [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

::: moniker range="vs-2017"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Programme d’installation de Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Localiser le programme d’installation de Microsoft Visual Studio")

     >[!NOTE]
     >Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Cliquez ou appuyez pour démarrer le programme d’installation, puis choisissez **Modifier**.

     ![Lancer ou modifier Visual Studio](media/modify-visual-studio.png "Modifier Visual Studio 2017")

     Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour si vous le souhaitez. Cliquez sur **Plus**, puis choisissez **Modifier**.

     ![Mettre à jour ou modifier Visual Studio](media/modify-or-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2017")

1. Dans l’écran **Charges de travail**, sélectionnez ou désélectionnez les charges de travail que vous voulez installer ou désinstaller.

    ![Boîte de dialogue d’installation de Visual Studio 2017](media/vs2017-modify-workloads.PNG "Choisir une charge de travail dans Visual Studio 2017")

1. Choisissez à nouveau **Modifier**.

1. Une fois les nouveaux composants et charges de travail installés, choisissez **Lancer**.

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Ouvrir Visual Studio Installer à partir de Windows](media/vs-2019/vs-installer-windows-start.png "Ouvrir Visual Studio Installer à partir de Windows")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée, puis choisissez **Modifier**.

     ![Mettre à jour ou modifier Visual Studio](media/vs-2019/vs-installer-modify.png "Mettre à jour ou modifier Visual Studio 2019")

1. Sous l’onglet **Charges de travail**, sélectionnez ou désélectionnez les charges de travail à installer ou désinstaller.

    ![Boîte de dialogue d’installation de Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Choisir une charge de travail dans Visual Studio 2019")

1. Indiquez si vous voulez accepter l’option **Installer pendant le téléchargement** par défaut ou l’option **Tout télécharger, puis installer**.

    ![Options d’installation de Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Choisir d’installer pendant le téléchargement ou de tout télécharger d’abord pour installer ultérieurement")

    L’option « Tout télécharger, puis installer » s’avère pratique si vous voulez d’abord tout télécharger pour installer plus tard.

1. Choisissez **Modifier**.

1. Une fois les nouveaux composants et charges de travail installés, choisissez **Lancer** depuis Visual Studio Installer.

::: moniker-end

## <a name="modify-individual-components"></a>Modifier des composants individuels

Si vous ne voulez pas installer des charges de travail pour personnaliser votre installation de Visual Studio, choisissez l’onglet **Composants individuels** dans Visual Studio Installer, sélectionnez les composants que vous voulez, puis suivez les invites.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Mettre à jour Visual Studio](update-visual-studio.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance](update-servicing-baseline.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
