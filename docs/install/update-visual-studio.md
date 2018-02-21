---
title: "Mettre à jour Visual Studio 2017 │ Microsoft Docs"
description: "Découvrez comment mettre à jour Visual Studio, étape par étape."
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8e61def66e68d7f889349d0e7b7337238e220dce
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Mettre à jour Visual Studio 2017 vers la version la plus récente
Nous mettons souvent à jour Visual Studio pour étendre ses fonctionnalités et résoudre les problèmes signalés par les clients. Pour faire en sorte de disposer de la [version optimisée la plus récente de Visual Studio](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#release-history), vous devez la mettre à jour. Voici comment procéder.

>[!IMPORTANT]
>Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="update-by-using-the-notifications-hub"></a>Mise à jour à l’aide du hub Notifications
1. Quand des mises à jour sont disponibles, un indicateur de notification s’affiche dans Visual Studio.

  ![Mettre à jour Visual Studio 2017 à l’aide du hub Notifications](media/notification-flag.png "L’indicateur Notification de mise à jour dans Visual Studio")

  Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**.

  ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-hub.png "Le hub Notifications dans Visual Studio")

2. Choisissez **"Visual Studio Update" est disponible** pour ouvrir la boîte de dialogue **Extensions et mises à jour**.

  ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-hub-select.png "Le hub Notification dans Visual Studio")

3. Dans la boîte de dialogue **Extensions et mises à jour**, choisissez le bouton **Mise à jour**.

  ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-extensions-and-updates.png "La boîte de dialogue Extensions et mises à jour dans Visual Studio")

### <a name="more-about-visual-studio-notifications"></a>Informations supplémentaires concernant les notifications Visual Studio

Visual Studio vous avertit quand une mise à jour est disponible pour Visual Studio ou l’un de ses composants, et également quand certains événements se produisent dans l’environnement Visual Studio.

* Quand l’indicateur de notification est jaune, cela signifie qu’une mise à jour de produit Visual Studio est disponible pour être installée.
* Quand l’indicateur de notification est rouge, vous avez un problème avec votre licence.
* Quand l’indicateur de notification est noir, vous avez des messages facultatifs ou d’information à consulter.

Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**, puis choisissez les notifications sur lesquelles vous souhaitez agir. Vous pouvez aussi choisir d’ignorer ou de faire disparaître une notification.

 ![Afficher un message facultatif ou d’information dans le hub de notification](media/notification-flag-optional.png "L’indicateur de notification de message facultatif ou d’information dans Visual Studio")

Si vous choisissez d’ignorer une notification, Visual Studio cesse de l’afficher. Si vous souhaitez réinitialiser la liste des notifications ignorées, cliquez sur le bouton **Paramètres** dans le hub de notifications.

   ![Choisissez le bouton Paramètres dans le hub de notifications pour afficher les options de notifications](media/vs-notifications-hub-settings-button.png "Choisissez le bouton Paramètres dans le hub de notifications pour afficher les options de notifications")

## <a name="update-by-using-the-visual-studio-installer"></a>Mise à jour à l’aide du programme d’installation de Visual Studio
1.  Ouvrez le programme d’installation. Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Si c’est le cas, vous serez invité à le faire.
 >[!NOTE]
 > Sur un ordinateur exécutant Windows 10, le programme d’installation se trouve sous la lettre **V** comme **Visual Studio Installer (programme d’installation de Visual Studio)** ou sous la lettre **M** comme **Microsoft Visual Studio Installer (programme d’installation de Microsoft Visual Studio)**.

2.  Dans la page **Produit** du programme d’installation, recherchez l’édition de Visual Studio qui est installée.

3.  Si une mise à jour est disponible, un bouton **Mettre à jour** apparaît. (Le programme d’installation peut mettre plusieurs secondes à déterminer si une mise à jour est disponible.)

  Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

     ![Mettre à jour Visual Studio 2017 à l’aide du programme d’installation de Visual Studio](media/update-visual-studio.png "Mettre à jour Visual Studio 2017 à l’aide du programme d’installation de Visual Studio")

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
