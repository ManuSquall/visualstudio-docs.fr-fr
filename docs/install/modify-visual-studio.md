---
title: Modifier Visual Studio 2017
titleSuffix: ''
description: Découvrez comment modifier Visual Studio, étape par étape.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 06/12/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c11e20343eea33a01c81525855e56078865340e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831847"
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Modifier Visual Studio 2017 en ajoutant ou supprimant des charges de travail et des composants

Nous avons simplifié le travail de personnalisation des tâches Visual Studio, mais aussi de Visual Studio à proprement parler. Pour ce faire, démarrez le nouveau programme d’installation de Visual Studio et apportez les modifications souhaitées.

Voici comment procéder.

## <a name="modify-workloads"></a>Modifier les charges de travail

 Les charges de travail contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.

>[!IMPORTANT]
>Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Programme d’installation de Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Localiser le programme d’installation de Microsoft Visual Studio")

     >[!NOTE]
     >Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. Cliquez ou appuyez pour démarrer le programme d’installation, puis choisissez **Modifier**.

     ![Lancer ou modifier Visual Studio](media/modify-visual-studio.png "Modifier Visual Studio 2017")

     Si vous disposez d’une mise à jour en attente, le bouton Modifier est à un emplacement différent. De cette façon, vous pouvez modifier Visual Studio sans le mettre à jour si vous le souhaitez. Cliquez sur **Plus**, puis choisissez **Modifier**.

     ![Mettre à jour ou modifier Visual Studio](media/modify-or-update-visual-studio.png "Mettre à jour ou modifier Visual Studio 2017")

3. Dans l’écran **Charges de travail**, sélectionnez ou désélectionnez les charges de travail que vous voulez installer ou désinstaller.

    ![Boîte de dialogue d’installation de Visual Studio 2017](media/vs2017-modify-workloads.PNG "Choisir une charge de travail dans Visual Studio 2017")

4. Choisissez à nouveau **Modifier**.

5. Une fois les nouveaux composants et charges de travail installés, choisissez **Lancer**.

## <a name="modify-individual-components"></a>Modifier des composants individuels

Si vous ne voulez pas utiliser la fonctionnalité pratique Charges de travail pour personnaliser votre installation de Visual Studio, choisissez l’option **Composants individuels** dans le programme d’installation de Visual Studio, sélectionnez les composants que vous voulez, puis suivez les invites.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio 2017](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)
