---
title: "Modifier Visual Studio 2017 │ Microsoft Docs"
description: "Découvrez comment modifier Visual Studio, étape par étape."
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8278b138e8cf7a8780ad83d591a823fdb85f2b08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Modifier Visual Studio 2017 en ajoutant ou supprimant des charges de travail et des composants
Non seulement nous avons simplifié la personnalisation de Visual Studio en fonction des tâches que vous avez à accomplir, mais nous en avons aussi simplifié la personnalisation. Vous n’avez plus besoin d’utiliser le Panneau de configuration ; à la place, démarrez le nouveau Visual Studio Installer et apportez les modifications souhaitées.

Voici comment procéder.  

## <a name="modify-workloads"></a>Modifier les charges de travail  
 Les charges de travail contiennent les fonctionnalités dont vous avez besoin pour le langage de programmation ou la plateforme que vous utilisez. Utilisez les charges de travail pour modifier Visual Studio pour qu’il prenne en charge le travail à effectuer, au moment où vous voulez l’effectuer.  

>[!IMPORTANT]
>Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Recherchez le programme d’installation de Visual Studio sur votre ordinateur.  

     Par exemple, sur un ordinateur exécutant la Mise à jour anniversaire Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** pour l’afficher comme **Visual Studio Installer**.  

     ![Programme d’installation de Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Localiser le programme d’installation de Microsoft Visual Studio")

     >[!NOTE]
     Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.<br/><br/> Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  Cliquez ou appuyez pour démarrer le programme d’installation, puis cliquez sur **Modifier**.  

     ![Lancer ou modifier Visual Studio](media/vs2017-modify.PNG "Modifier Visual Studio 2017")  

3.  Dans l’écran **Charges de travail**, sélectionnez ou désélectionnez les charges de travail que vous voulez installer ou désinstaller.  

    ![Boîte de dialogue d’installation de Visual Studio 2017](media/vs2017-modify-workloads.PNG "Choisir une charge de travail dans Visual Studio 2017")

4. Cliquez ou appuyez à nouveau sur **Modifier**.  

5. Une fois les nouveaux composants et charges de travail installés, cliquez sur **Lancer**.

## <a name="modify-individual-components"></a>Modifier des composants individuels

Si vous ne voulez pas utiliser la fonctionnalité pratique Charges de travail pour personnaliser votre installation de Visual Studio, choisissez l’option **Composants individuels** dans le programme d’installation de Visual Studio, sélectionnez les composants que vous voulez, puis suivez les invites.  

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)
