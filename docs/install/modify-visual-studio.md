---
title: Modifier Visual Studio 2017
titleSuffix: ''
description: Découvrez comment modifier Visual Studio, étape par étape.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/19/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 07aa8afbb4e4ca3970a0f082ec6649a90bfaf2ed
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76112698"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modifier Visual Studio en ajoutant ou supprimant des charges de travail et des composants

::: moniker range="vs-2019"

Il est facile de modifier Visual Studio afin d’inclure uniquement ce que vous voulez, quand vous le voulez. Pour cela, ouvrez Visual Studio Installer pour ajouter ou supprimer des composants et des charges de travail.

::: moniker-end

::: moniker range="vs-2017"

Nous avons simplifié le travail de personnalisation des tâches Visual Studio, mais aussi de Visual Studio à proprement parler. Pour ce faire, ouvrez le nouveau Visual Studio Installer et apportez les modifications souhaitées.

::: moniker-end

Voici comment procéder.

>[!IMPORTANT]
>Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> Les procédures suivantes supposent que vous disposez d’une connexion Internet.
>
> Pour plus d’informations sur la façon de modifier une installation [hors connexion](create-an-offline-installation-of-visual-studio.md) de Visual Studio précédemment créée, consultez la page [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md) et la page [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

## <a name="open-the-visual-studio-installer"></a>Ouvrez le Visual Studio Installer

::: moniker range="vs-2017"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Visual Studio Installer](media/locate-the-visual-studio-installer.png "Localiser le programme d’installation de Microsoft Visual Studio")

     >[!TIP]
     >Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Ouvrez le programme d’installation, puis choisissez **modifier**.

     ![Lancer ou modifier Visual Studio](media/modify-visual-studio.png "Modifier Visual Studio 2017")

     > [!IMPORTANT]
     > Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour si vous le souhaitez. Cliquez sur **Plus**, puis choisissez **Modifier**.
     >
     > ![Mettre à jour ou modifier Visual Studio](media/modify-or-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Ouvrir le Visual Studio Installer à partir de Windows](media/vs-2019/vs-installer-windows-start.png "Ouvrez le Visual Studio Installer")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée, puis choisissez **Modifier**.

     ![Mettre à jour ou modifier Visual Studio](media/vs-2019/vs-installer-modify.png "Mettre à jour ou modifier Visual Studio 2019")

     > [!IMPORTANT]
     > Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour, si vous le souhaitez. Choisissez **plus**, puis **modifier**.
     >
     > ![Mettre à jour ou modifier Visual Studio](media/vs-2019/modify-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Modifier les charges de travail

::: moniker range="vs-2017"

 Les [charges de travail](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

1. Dans la Visual Studio Installer, choisissez l’onglet **charges de travail** , puis sélectionnez ou désélectionnez les charges de travail de votre choix.

    ![Boîte de dialogue d’installation de Visual Studio 2017](media/modify-workloads.png "Choisir une charge de travail dans Visual Studio 2019")

1. Indiquez si vous voulez accepter l’option **Installer pendant le téléchargement** par défaut ou l’option **Tout télécharger, puis installer**.

    ![Options d’installation de Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Choisir d’installer pendant le téléchargement ou le téléchargement d’abord et l’installation ultérieure")

    L’option « Tout télécharger, puis installer » s’avère pratique si vous voulez d’abord tout télécharger pour installer plus tard.

1. Choisissez **Modifier**.

1. Une fois les nouvelles charges de travail installées, choisissez **lancer** à partir de la Visual Studio installer pour ouvrir Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Les charges de travail contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

1. Dans le Visual Studio Installer, choisissez l’onglet **charges de travail** , puis sélectionnez ou désélectionnez les charges de travail de votre choix.

    ![Boîte de dialogue d’installation de Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Choisir une charge de travail dans Visual Studio 2019")

1. Indiquez si vous voulez accepter l’option **Installer pendant le téléchargement** par défaut ou l’option **Tout télécharger, puis installer**.

    ![Options d’installation de Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Choisir d’installer pendant le téléchargement ou le téléchargement d’abord et l’installation ultérieure")

    L’option « Tout télécharger, puis installer » s’avère pratique si vous voulez d’abord tout télécharger pour installer plus tard.

1. Choisissez **Modifier**.

1. Une fois les nouvelles charges de travail installées, choisissez **lancer** à partir de la Visual Studio installer pour ouvrir Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modifier des composants individuels

Si vous ne souhaitez pas utiliser les charges de travail pour personnaliser votre installation de Visual Studio, choisissez l’onglet **composants individuels** dans le Visual Studio installer, sélectionnez les composants souhaités, puis suivez les invites.

## <a name="modify-language-packs"></a>Modifier les modules linguistiques

Par défaut, le programme d’installation correspond à la langue du système d’exploitation lorsqu’il s’exécute pour la première fois. Toutefois, vous pouvez modifier la langue chaque fois que vous le souhaitez. Pour ce faire, choisissez l’onglet **modules linguistiques** dans la Visual Studio installer, sélectionnez la langue de votre choix, puis suivez les invites.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Liste des ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Mettre à jour Visual Studio](update-visual-studio.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance](update-servicing-baseline.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
