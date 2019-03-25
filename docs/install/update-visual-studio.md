---
title: Mettre à jour Visual Studio 2017
titleSuffix: ''
description: Découvrez comment mettre à jour Visual Studio vers la version la plus récente, étape par étape.
ms.date: 03/09/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e58927f434b5ad5b8d8fe34c29d034cfc4dd57dc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983973"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Mettre à jour Visual Studio avec la version la plus récente

::: moniker range="vs-2017"

Nous vous encourageons à mettre à jour vers la [version la plus récente](/visualstudio/releasenotes/vs2017-relnotes/) de Visual Studio 2017 afin de toujours bénéficier des fonctionnalités, correctifs et améliorations les plus récents.

Si vous souhaitez tester la prochaine version, envisagez aussi de télécharger la [version Release Candidate](//visualstudio/releases/2019/release-notes/) de Visual Studio 2019.

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Mettre à jour Visual Studio 2017 version 15.6 ou ultérieure

Nous avez simplifié l’expérience d’installation et de mise à jour pour en faciliter l’utilisation directement à partir de l’IDE. Voici comment mettre à jour à partir des versions 15.6 et ultérieures vers la version la plus récente de Visual Studio.

### <a name="use-the-notifications-hub"></a>Utiliser le hub Notifications

Lorsqu’il existe une mise à jour, un indicateur de notification correspondant s’affiche dans Visual Studio.

1. Enregistrez votre travail.

1. Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**, puis choisissez la mise à jour à installer.

   ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/vs-install-notifications-hub-15dot6.png "Le hub Notifications dans Visual Studio 2017")

1. Lorsque la boîte de dialogue **Mettre à jour**, choisissez **Mettre à jour maintenant**.

    ![Mettre à jour Visual Studio 2017 à l’aide de la boîte de dialogue Mettre à jour du hub Notifications](media/vs-update-now-from-notifications-hub.png "La boîte de dialogue Mettre à jour dans le hub Notifications dans Visual Studio")

     Si une boîte de dialogue Contrôle d’accès utilisateur s’ouvre, choisissez **Oui**. Ensuite, une boîte de dialogue « Veuillez patienter » peut s’afficher pendant un moment, puis le programme d’installation Visual Studio s’ouvre pour démarrer la mise à jour.

     ![La nouvelle expérience du programme d’installation de Visual Studio dans la version 15.6](media/visual-studio-15dot6-installer.png "La nouvelle expérience du programme d’installation de Visual Studio dans la version 15.6")

     La mise à jour se poursuit. Ensuite, lorsqu’elle est terminée, Visual Studio redémarre.

     > [!NOTE]
     > Quand vous exécutez Visual Studio en mode administrateur, vous devez redémarrer manuellement Visual Studio après la mise à jour.

### <a name="use-the-ide"></a>Utiliser l’IDE

Vous pouvez rechercher une mise à jour et ensuite installer la mise à jour à partir de la barre de menus dans Visual Studio.

1. Enregistrez votre travail.

1. Choisissez **Aide** > **Rechercher les mises à jour**.

     ![Le nouveau menu Aide dans Visual Studio version 15.6](media/vs-help-menu-check-for-updates.png "Le nouveau menu Aide dans Visual Studio version 15.6")

1. Lorsque la boîte de dialogue **Mettre à jour**, choisissez **Mettre à jour maintenant**.

   La mise à niveau s’exécute comme décrit dans la section précédente, puis Visual Studio redémarre une fois la mise à jour terminée.

   > [!NOTE]
   > Quand vous exécutez Visual Studio en mode administrateur, vous devez redémarrer manuellement Visual Studio après la mise à jour.

### <a name="use-the-visual-studio-installer"></a>Utiliser le programme d’installation de Visual Studio

Comme dans les versions antérieures de Visual Studio, vous pouvez utiliser Visual Studio Installer pour installer une mise à jour.

1. Enregistrez votre travail.

1. Ouvrez le programme d’installation. Avant de poursuivre, le programme d’installation de Visual Studio peut nécessiter une mise à jour.

   > [!NOTE]
   > Sur un ordinateur exécutant Windows 10, le programme d’installation se trouve sous la lettre **V** comme **Visual Studio Installer (programme d’installation de Visual Studio)** ou sous la lettre **M** comme **Microsoft Visual Studio Installer (programme d’installation de Microsoft Visual Studio)**.

1. Dans la page **Produit** du programme d’installation, recherchez l’édition de Visual Studio qui est installée.

1. Si une mise à jour est disponible, un bouton **Mettre à jour** apparaît. (Le programme d’installation peut mettre plusieurs secondes à déterminer si une mise à jour est disponible.)

   Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

     ![Mettre à jour Visual Studio 2017 à l’aide du programme d’installation de Visual Studio](media/update-visual-studio.png "Mettre à jour Visual Studio 2017 à l’aide du programme d’installation de Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Mettre à jour Visual Studio 2017 version 15.5 ou version antérieure

Si vous utilisez une version antérieure, voici comment appliquer une mise à jour à partir de Visual Studio 2017 version 15.0 jusqu’à la version 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Mise à jour à l’aide du hub Notifications

1. Lorsqu’il existe des mises à jour, un indicateur de notification correspondant s’affiche dans Visual Studio.

   ![Mettre à jour Visual Studio 2017 à l’aide du hub Notifications](media/notification-flag.png "L’indicateur Notification de mise à jour dans Visual Studio")

   Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**.

   ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-hub.png "Le hub Notifications dans Visual Studio")

1. Choisissez **"Visual Studio Update" est disponible** pour ouvrir la boîte de dialogue **Extensions et mises à jour**.

   ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-hub-select.png "Le hub Notification dans Visual Studio")

1. Dans la boîte de dialogue **Extensions et mises à jour**, choisissez le bouton **Mise à jour**.

   ![Mettre à jour Visual Studio 2017 à l’aide du hub de notification](media/notifications-extensions-and-updates.png "La boîte de dialogue Extensions et mises à jour dans Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Informations supplémentaires concernant les notifications Visual Studio

Visual Studio vous avertit quand une mise à jour est disponible pour Visual Studio ou l’un de ses composants, et également quand certains événements se produisent dans l’environnement Visual Studio.

* Quand l’indicateur de notification est jaune, cela signifie qu’une mise à jour de produit Visual Studio est disponible pour être installée.
* Quand l’indicateur de notification est rouge, vous avez un problème avec votre licence.
* Quand l’indicateur de notification est noir, vous avez des messages facultatifs ou d’information à consulter.

Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**, puis choisissez les notifications sur lesquelles vous souhaitez agir. Vous pouvez aussi choisir d’ignorer ou de faire disparaître une notification.

 ![Afficher un message facultatif ou d’information dans le hub de notification](media/notification-flag-optional.png "L’indicateur de notification de message facultatif ou d’information dans Visual Studio")

Si vous choisissez d’ignorer une notification, Visual Studio cesse de l’afficher. Si vous souhaitez réinitialiser la liste des notifications ignorées, cliquez sur le bouton **Paramètres** dans le hub Notifications.

   ![Choisissez le bouton Paramètres dans le hub de notifications pour afficher les options de notifications](media/vs-notifications-hub-settings-button.png "Choisissez le bouton Paramètres dans le hub de notifications pour afficher les options de notifications")

### <a name="update-by-using-the-visual-studio-installer"></a>Mise à jour à l’aide du programme d’installation de Visual Studio

1. Ouvrez le programme d’installation. Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Si c’est le cas, vous êtes invité à le faire.

   > [!NOTE]
   > Sur un ordinateur exécutant Windows 10, le programme d’installation se trouve sous la lettre **V** comme **Visual Studio Installer (programme d’installation de Visual Studio)** ou sous la lettre **M** comme **Microsoft Visual Studio Installer (programme d’installation de Microsoft Visual Studio)**.

1. Dans la page **Produit** du programme d’installation, recherchez l’édition de Visual Studio qui est installée.

1. Si une mise à jour est disponible, un bouton **Mettre à jour** apparaît. (Le programme d’installation peut mettre plusieurs secondes à déterminer si une mise à jour est disponible.)

   Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

     ![Mettre à jour Visual Studio 2017 à l’aide du programme d’installation de Visual Studio](media/update-visual-studio.png "Mettre à jour Visual Studio à l’aide de Visual Studio Installer")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Modifier Visual Studio](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
* [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update)

::: moniker-end

::: moniker range="vs-2019"

Nous vous encourageons à effectuer la mise à jour vers la [version la plus récente](/visualstudio/releases/2019/release-notes/) de Visual Studio 2019 afin de toujours bénéficier des fonctionnalités, correctifs et améliorations les plus récents.

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2019"></a>Mettre à jour Visual Studio 2019

Voici comment utiliser Visual Studio Installer pour mettre à jour Visual&nbsp;Studio&nbsp;2019&nbsp;Preview ou Visual&nbsp;Studio&nbsp;2019&nbsp;RC.

1. Ouvrez le programme d’installation.

     ![Ouvrir Visual Studio Installer](media/vs2019-visual-studio-installer.png "Ouvrir Visual Studio Installer")

   Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée.

   Par exemple, si vous avez déjà installé Visual&nbsp;Studio Community&nbsp;2019&nbsp;RC et qu’il existe une mise à jour associée, un message **Mise à jour disponible** s’affiche dans le programme d’installation.

     ![Sélectionner l’édition de Visual Studio 2019 que vous souhaitez mettre à jour](media/vs2019-update-visual-studio-community-rc.png "Sélectionner l’édition de Visual Studio 2019 que vous souhaitez mettre à jour")

1. Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

    ![Sélectionner le bouton Mettre à jour pour installer les mises à jour](media/vs2019-choose-update-visual-studio-community-rc.png "Sélectionner le bouton Mettre à jour pour installer les mises à jour")

1. Une fois la mise à jour terminée, sélectionnez **Lancer** pour démarrer Visual Studio.

    ![Sélectionner le bouton Lancer pour démarrer Visual Studio](media/vs2019-choose-launch-visual-studio-community-rc.png "Sélectionner le bouton Lancer pour démarrer Visual Studio")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update)

::: moniker-end
