---
title: Mettre à jour Visual Studio 2017
titleSuffix: ''
description: Découvrez comment mettre à jour Visual Studio vers la version la plus récente, étape par étape.
ms.date: 04/06/2021
ms.custom: acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9244c9e234c56b058dbfe92a4ef6a10d8c9c702d
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113187"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Mettre à jour Visual Studio avec la version la plus récente

::: moniker range="vs-2017"

Nous vous encourageons à effectuer la mise à jour vers la [version la plus récente](/visualstudio/releasenotes/vs2017-relnotes/) de Visual Studio 2017 afin de toujours bénéficier des fonctionnalités, correctifs et améliorations les plus récents.

Et si vous souhaitez essayer notre version la plus récente, pensez à télécharger et installer [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) à la place.

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Mettre à jour Visual Studio 2017 version 15.6 ou ultérieure

Nous avez simplifié l’expérience d’installation et de mise à jour pour en faciliter l’utilisation directement à partir de l’IDE. Voici comment mettre à jour à partir des versions 15.6 et ultérieures vers la version la plus récente de Visual Studio.

### <a name="using-the-notifications-hub"></a>Utiliser Notification Hub

Lorsqu’il existe une mise à jour, un indicateur de notification correspondant s’affiche dans Visual Studio.

1. Enregistrez votre travail.

1. Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**, puis choisissez la mise à jour à installer.

   ![Mettre à jour Visual Studio 2017 à l’aide du Hub de notification](media/vs-install-notifications-hub-15dot6.png "Hub de notifications dans Visual Studio 2017")

      > [!TIP]
      > La mise à jour d’une édition de Visual Studio 2017 étant cumulative, choisissez toujours d’installer celle qui porte le numéro de version le plus récent.

1. Lorsque la boîte de dialogue **Mettre à jour**, choisissez **Mettre à jour maintenant**.

    ![Mettre à jour Visual Studio 2017 à l’aide de la boîte de dialogue de mise à jour du Hub de notifications](media/vs-update-now-from-notifications-hub.png "Boîte de dialogue mettre à jour à partir du Hub notifications dans Visual Studio")

     Si une boîte de dialogue Contrôle d’accès utilisateur s’ouvre, choisissez **Oui**. Ensuite, une boîte de dialogue « Veuillez patienter » peut s’afficher pendant un moment, puis le programme d’installation Visual Studio s’ouvre pour démarrer la mise à jour.

     ![Nouvelle expérience Visual Studio Installer dans la version 15,6](media/visual-studio-15dot6-installer.png "Nouvelle expérience Visual Studio Installer dans la version 15,6")

     La mise à jour se poursuit. Ensuite, lorsqu’elle est terminée, Visual Studio redémarre.

     > [!NOTE]
     > Quand vous exécutez Visual Studio en mode administrateur, vous devez redémarrer manuellement Visual Studio après la mise à jour.

### <a name="using-the-ide"></a>Utilisation de l'IDE

Vous pouvez rechercher une mise à jour et ensuite installer la mise à jour à partir de la barre de menus dans Visual Studio.

1. Enregistrez votre travail.

1. Choisissez **aide** > **Rechercher les mises à jour**.

     ![Nouveau menu aide dans Visual Studio version 15,6](media/vs-help-menu-check-for-updates.png "Nouveau menu aide dans Visual Studio version 15,6")

1. Lorsque la boîte de dialogue **Mettre à jour**, choisissez **Mettre à jour maintenant**.

   La mise à niveau s’exécute comme décrit dans la section précédente, puis Visual Studio redémarre une fois la mise à jour terminée.

   > [!NOTE]
   > Quand vous exécutez Visual Studio en mode administrateur, vous devez redémarrer manuellement Visual Studio après la mise à jour.

### <a name="using-the-visual-studio-installer"></a>Utiliser Visual Studio Installer

Comme dans les versions antérieures de Visual Studio, vous pouvez utiliser Visual Studio Installer pour installer une mise à jour.

1. Enregistrez votre travail.

1. Ouvrez le programme d’installation. Avant de poursuivre, le programme d’installation de Visual Studio peut nécessiter une mise à jour.

   > [!NOTE]
   > Sur un ordinateur exécutant Windows 10, le programme d’installation se trouve sous la lettre **V** comme **Visual Studio Installer (programme d’installation de Visual Studio)** ou sous la lettre **M** comme **Microsoft Visual Studio Installer (programme d’installation de Microsoft Visual Studio)**.

1. Dans la page **Produit** du programme d’installation, recherchez l’édition de Visual Studio installée précédemment.

1. Si une mise à jour est disponible, un bouton **Mettre à jour** apparaît. (Le programme d’installation peut mettre plusieurs secondes à déterminer si une mise à jour est disponible.)

   Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

     ![Mettre à jour Visual Studio 2017 à l’aide de l’Visual Studio Installer](media/update-visual-studio.png "Mettre à jour Visual Studio 2017 à l’aide de l’Visual Studio Installer")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Mettre à jour Visual Studio 2017 version 15.5 ou version antérieure

Si vous utilisez une version antérieure, voici comment appliquer une mise à jour à partir de Visual Studio 2017 version 15.0 jusqu’à la version 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Mise à jour à l’aide du hub Notifications

1. Lorsqu’il existe des mises à jour, un indicateur de notification correspondant s’affiche dans Visual Studio.

   ![Mettre à jour l’indicateur de notification Visual Studio 2017](media/notification-flag.png "Indicateur de notification de mise à jour dans Visual Studio")

   Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**.

   ![Mise à jour de Visual Studio 2017 dans le hub de notification](media/notifications-hub.png "Mise à jour de Visual Studio 2017 dans le hub de notification")

      > [!TIP]
      > La mise à jour d’une édition de Visual Studio 2017 étant cumulative, choisissez toujours d’installer celle qui porte le numéro de version le plus récent.

1. Choisissez **"Visual Studio Update" est disponible** pour ouvrir la boîte de dialogue **Extensions et mises à jour**.

   ![Choisir la mise à jour de Visual Studio](media/notifications-hub-select.png "Choisir la mise à jour de Visual Studio")

1. Dans la boîte de dialogue **Extensions et mises à jour**, choisissez le bouton **Mise à jour**.

   ![Choisissez mettre à jour dans la boîte de dialogue extensions et mises à jour](media/notifications-extensions-and-updates.png "Boîte de dialogue extensions et mises à jour dans Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Informations supplémentaires concernant les notifications Visual Studio

Visual Studio vous avertit quand une mise à jour est disponible pour Visual Studio ou l’un de ses composants, et également quand certains événements se produisent dans l’environnement Visual Studio.

* Quand l’indicateur de notification est jaune, cela signifie qu’une mise à jour de produit Visual Studio est disponible pour être installée.
* Quand l’indicateur de notification est rouge, vous avez un problème avec votre licence.
* Quand l’indicateur de notification est noir, vous avez des messages facultatifs ou d’information à consulter.

Choisissez l’indicateur de notification pour ouvrir le hub **Notifications**, puis choisissez les notifications sur lesquelles vous souhaitez agir. Vous pouvez aussi choisir d’ignorer ou de faire disparaître une notification.

 ![Afficher un message d’information ou facultatif dans le hub de notification](media/notification-flag-optional.png "Indicateur de notification de message d’information facultatif ou facultatif dans Visual Studio")

Si vous choisissez d’ignorer une notification, Visual Studio cesse de l’afficher. Si vous souhaitez réinitialiser la liste des notifications ignorées, cliquez sur le bouton **Paramètres** dans le hub Notifications.

   ![Cliquez sur le bouton Paramètres dans le hub de notifications pour afficher les options de notification.](media/vs-notifications-hub-settings-button.png "Cliquez sur le bouton Paramètres dans le hub de notifications pour afficher les options de notification.")

### <a name="update-by-using-the-visual-studio-installer"></a>Mise à jour à l’aide du programme d’installation de Visual Studio

1. Ouvrez le programme d’installation. Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Si c’est le cas, vous êtes invité à le faire.

   > [!NOTE]
   > Sur un ordinateur exécutant Windows 10, le programme d’installation se trouve sous la lettre **V** comme **Visual Studio Installer (programme d’installation de Visual Studio)** ou sous la lettre **M** comme **Microsoft Visual Studio Installer (programme d’installation de Microsoft Visual Studio)**.

1. Dans la page **Produit** du programme d’installation, recherchez l’édition de Visual Studio qui est installée.

1. Si une mise à jour est disponible, un bouton **Mettre à jour** apparaît. (Le programme d’installation peut mettre plusieurs secondes à déterminer si une mise à jour est disponible.)

   Choisissez le bouton **Mettre à jour** pour installer les mises à jour.

     ![Mettre à jour Visual Studio 2017 à l’aide de l’Visual Studio Installer](media/update-visual-studio.png "Mettre à jour Visual Studio à l’aide de l’Visual Studio Installer")

::: moniker-end

::: moniker range="vs-2019"

Nous vous encourageons à effectuer la mise à jour vers la [version la plus récente](/visualstudio/releases/2019/release-notes/) de Visual Studio 2019 afin de toujours bénéficier des fonctionnalités, correctifs et améliorations les plus récents.

Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement. Si vous utilisez actuellement une autre version de Visual Studio, vous pouvez soit [installer les versions de Visual Studio côte à côte](../install/install-visual-studio-versions-side-by-side.md), soit [désinstaller les versions antérieures de Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Mettre à jour Visual Studio pour Mac](/visualstudio/mac/update).

Voici comment mettre à jour Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Utiliser le programme d’installation de Visual Studio

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

   Dans le menu Démarrer de Windows, vous pouvez rechercher « programme d’installation ».

   ![Visual Studio Installer](media/vs-2019/visual-studio-installer.png "Rechercher le Visual Studio Installer")

   Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée.

   Par exemple, si vous avez déjà installé Visual&nbsp;Studio Community&nbsp;2019 et qu’il existe une mise à jour associée, un message **Mise à jour disponible** s’affiche dans le programme d’installation.

     ![Sélectionnez l’édition de Visual Studio 2019 que vous souhaitez mettre à jour](media/vs-2019/vs-installer-update-visual-studio-community.png "Sélectionnez l’édition de Visual Studio 2019 que vous souhaitez mettre à jour")

1. Choisissez **Mettre à jour** pour installer les mises à jour.

    ![Sélectionner le bouton mettre à jour pour installer les mises à jour](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Sélectionner le bouton mettre à jour pour installer les mises à jour")

1. Une fois la mise à jour effectuée, vous pouvez être amené à redémarrer votre ordinateur. Si tel est le cas, redémarrez l’ordinateur, puis démarrez Visual Studio de manière normale.

   Si vous n’êtes pas invité à redémarrer l’ordinateur, choisissez **Lancer** pour démarrer Visual Studio à partir du programme d’installation.

    ![Sélectionnez le bouton lancer pour démarrer Visual Studio.](media/vs-2019/choose-launch-visual-studio-community.png "Sélectionnez le bouton lancer pour démarrer Visual Studio.")

## <a name="use-the-ide"></a>Utiliser l’IDE

Pour rechercher une mise à jour et l’installer, vous pouvez utiliser la barre de menus ou la zone de recherche dans Visual Studio 2019.

### <a name="open-visual-studio"></a>Ouvrez Visual Studio.

1. Dans le menu **Démarrer** de Windows, choisissez **Visual Studio 2019**.

    ![Ouvrir Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Ouvrir Visual Studio 2019 à partir de Windows")

1. Sous **Prise en main**, choisissez une option pour ouvrir l’IDE.

    ![Ouvrez le Visual Studio Installer](media/vs2019-choose-option-from-get-started.png "Ouvrez le Visual Studio Installer")

    Visual Studio s’ouvre. Dans l’IDE, un message **Mise à jour de Visual Studio 2019** s’affiche.

    ![Message « Visual Studio 2019 Update » dans l’IDE](media/vs-2019/update-visual-studio-ide-message.png "Message « Visual Studio 2019 Update » dans l’IDE")

1. Dans le message **Mise à jour de Visual Studio 2019**, choisissez **Afficher les détails**.

   ![Cliquez sur le bouton afficher les détails dans le message de mise à jour de l’IDE de Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Cliquez sur le bouton afficher les détails dans le message de mise à jour de Visual Studio 2019")

1. Dans la boîte de dialogue **Mise à jour téléchargée et prête à être installée**, sélectionnez **Mettre à jour**.

     ![Choisissez le bouton mettre à jour dans la boîte de dialogue « mettre à jour téléchargé et prêt pour l’installation »](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Choisissez le bouton mettre à jour dans la boîte de dialogue « mettre à jour téléchargé et prêt pour l’installation »")

   Visual Studio se met à jour, se ferme, puis se rouvre.

### <a name="in-visual-studio"></a>Dans Visual Studio

1. Dans la barre de menus, choisissez **Aide**, puis **Rechercher les mises à jour**.

     ![Choisissez « Rechercher des mises à jour » dans le menu aide.](media/vs-2019/vs-ide-check-updates-help-menu.png "Choisissez « Rechercher des mises à jour » dans le menu aide.")

    > [!NOTE]
    > Vous pouvez également utiliser la zone de recherche de l’environnement IDE pour rechercher les mises à jour. Appuyez sur **CTRL** + **Q**, tapez « Rechercher les mises à jour », puis choisissez le résultat de la recherche correspondant à.

1. Dans la boîte de dialogue **Mise à jour disponible**, choisissez **Mettre à jour**.

     ![Choisissez le bouton mettre à jour dans la boîte de dialogue « mise à jour disponible »](media/vs-2019/update-visual-studio-community-from-ide.png "Choisissez le bouton mettre à jour dans la boîte de dialogue « mise à jour disponible »")

   Visual Studio se met à jour, se ferme, puis se rouvre.

## <a name="use-the-notifications-hub"></a>Utiliser le hub Notifications

1. Dans Visual Studio, enregistrez votre travail.

1. Choisissez l’icône de notification en bas à droite de l’environnement IDE de Visual Studio pour ouvrir le hub **Notifications**.

   ![Icône de notification dans l’IDE de Visual Studio](media/vs-2019/notification-bar.png "Icône de notification dans l’IDE de Visual Studio")

1. Dans le **hub Notifications**, choisissez la mise à jour à installer, puis **Afficher les détails**.

     ![Le hub de notification dans Visual Studio 2019](media/vs-2019/notification-hub-update.png "Le hub de notification dans Visual Studio 2019")

      > [!TIP]
      > La mise à jour d’une édition de Visual Studio 2019 étant cumulative, choisissez toujours d’installer celle qui porte le numéro de version le plus récent.

1. Dans la boîte de dialogue **Mise à jour disponible**, choisissez **Mettre à jour**.

   Visual Studio se met à jour, se ferme, puis se rouvre.

## <a name="customize-update-settings"></a>Personnaliser les paramètres de mise à jour

Vous pouvez personnaliser les paramètres de mise à jour dans Visual Studio de plusieurs façons, par exemple en modifiant le mode d’installation et en sélectionnant les téléchargements automatiques.

Il existe deux modes d’installation au choix :

* **Installer pendant le téléchargement**
* **Tout télécharger, puis installer**

Vous pouvez également choisir le paramètre **Télécharger automatiquement les mises à jour**, qui autorise le téléchargement des mises à jour à télécharger alors que votre ordinateur est inactif.

Voici comment faire :

1. Dans la barre de menus, choisissez **Outils** > **options**.

2. Développez **Environnement**, puis choisissez **Mises à jour de produits**.

    ![Paramètres des mises à jour dans Visual Studio](media/vs-2019/update-settings-options.png)

3. Choisissez le mode d’installation et les options de téléchargement automatique pour vos mises à jour de Visual Studio.

::: moniker-end

## <a name="administrator-updates"></a>Mises à jour de l’administrateur 

Si vous êtes membre d’une organisation qui centralise la gestion des installations logicielles, votre administrateur d’entreprise peut mettre à jour Visual Studio sur votre ordinateur. Pour plus d’informations sur la façon de contrôler ou de configurer les types de mises à jour que votre ordinateur peut accepter, consultez [utilisation de Configuration Manager pour déployer des mises à jour de Visual Studio](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates). 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer des versions de Visual Studio côte à côte](install-visual-studio-versions-side-by-side.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Guide Visual Studio Enterprise](visual-studio-enterprise-guide.md)
* [Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance](update-servicing-baseline.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
