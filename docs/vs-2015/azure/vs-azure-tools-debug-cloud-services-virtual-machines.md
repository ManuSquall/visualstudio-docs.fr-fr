---
title: Débogage d’un service cloud Azure ou une machine virtuelle dans Visual Studio | Microsoft Docs
description: Débogage d’un service cloud ou d’une machine virtuelle dans Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: b2c67ce81a42df4a17761fcee2dcd2f8a67c4941
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002007"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Débogage d’un service cloud Azure ou une machine virtuelle dans Visual Studio

Visual Studio vous offre différentes options pour le débogage des services cloud Azure et machines virtuelles.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Déboguer votre service cloud sur votre ordinateur local

Vous pouvez gagner du temps et argent à l’aide d’Azure compute émulateur pour déboguer votre service cloud sur un ordinateur local. Déboguer un service localement avant de le déployer, vous pouvez améliorer la fiabilité et les performances sans devoir payer de temps de calcul. Toutefois, certaines erreurs peuvent se produire uniquement lorsque vous exécutez un service cloud dans Azure lui-même. Vous pouvez déboguer ces erreurs si vous activez le débogage à distance lorsque vous publiez votre service, puis attacherez le débogueur à une instance de rôle.

L’émulateur simule le service de calcul Azure et s’exécute dans votre environnement local afin que vous pouvez tester et déboguer votre service cloud avant de le déployer. L’émulateur gère le cycle de vie de vos instances de rôle et donne accès aux ressources simulées, telles que le stockage local. Lorsque vous déboguez ou exécutez votre service à partir de Visual Studio, il démarre automatiquement l’émulateur comme une application d’arrière-plan et puis déploie votre service à l’émulateur. Vous pouvez utiliser l’émulateur pour afficher votre service lorsqu’il s’exécute dans l’environnement local. Vous pouvez exécuter la version complète ou la version express de l’émulateur. (La version express de l’émulateur à partir de Azure 2.3, est la valeur par défaut.) Consultez [à l’aide de l’émulateur Express pour exécuter et déboguer un Service Cloud localement](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Pour déboguer votre service cloud sur votre ordinateur local

1. Dans la barre de menus, choisissez **déboguer**, **démarrer le débogage** pour exécuter votre projet de service cloud Azure. Comme alternative, vous pouvez appuyer sur F5. Vous verrez un message qui démarre l’émulateur de calcul. Lorsque l’émulateur démarre, l’icône de barre d’état système le confirme.

    ![Émulateur Azure dans la barre d’état système](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Afficher l’interface utilisateur pour l’émulateur de calcul en ouvrant le menu contextuel de l’icône Azure dans la zone de notification, puis sélectionnez **Show Compute Emulator UI**.

    Le volet gauche de l’interface utilisateur montre les services actuellement déployés sur l’émulateur de calcul et les instances de rôle chaque service est en cours d’exécution. Vous pouvez choisir le service ou les rôles pour afficher le cycle de vie, la journalisation et les informations de diagnostic dans le volet droit. Si vous placez le focus dans la marge supérieure d’une fenêtre incluse, celle-ci se développe pour remplir le volet droit.

3. Parcourez l’application en sélectionnant des commandes sur le **déboguer** menu et en définissant des points d’arrêt dans votre code. À mesure que vous parcourez l’application dans le débogueur, les volets sont mis à jour avec l’état actuel de l’application. Lorsque vous arrêtez le débogage, le déploiement d’application est supprimé. Si votre application inclut un rôle web et que vous avez défini la propriété action de démarrage pour démarrer le navigateur web, Visual Studio démarre votre application web dans le navigateur. Si vous modifiez le nombre d’instances d’un rôle dans la configuration du service, vous devez arrêter votre service cloud et puis redémarrez le débogage afin que vous puissiez déboguer ces nouvelles instances du rôle.

    **Remarque :** lorsque vous arrêtez l’exécution ou de débogage de votre service, l’émulateur de calcul local et l’émulateur de stockage ne sont pas arrêtés. Vous devez les arrêter explicitement à partir de la zone de notification.

## <a name="debug-a-cloud-service-in-azure"></a>Déboguer un service cloud dans Azure

Pour déboguer un service cloud à partir d’un ordinateur distant, vous devez activer cette fonctionnalité explicitement lorsque vous déployez votre service cloud afin que nécessaires (msvsmon.exe, par exemple) de services sont installées sur les ordinateurs virtuels qui exécutent vos instances de rôle. Si vous n’avez pas activé le débogage à distance quand vous avez publié le service, vous devez republier le service avec le débogage distant activé.

Si vous activez le débogage à distance pour un service cloud, il ne présentent une dégradation des performances ou des frais supplémentaires. N’utilisez pas le débogage à distance sur un service de production, car les clients qui utilisent le service peuvent être compromises.

> [!NOTE]
> Lorsque vous publiez un service cloud à partir de Visual Studio, vous pouvez activer **IntelliTrace** pour tous les rôles de ce service qui ciblent le .NET Framework 4 ou .NET Framework 4.5. À l’aide de **IntelliTrace**, vous pouvez examiner des événements qui s’est produite dans une instance de rôle dans le passé et reproduire le contexte à partir de ce moment-là. Consultez [débogage d’un service cloud publié avec IntelliTrace et Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016) et [IntelliTrace à l’aide de](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Pour activer le débogage à distance pour un service cloud

1. Ouvrez le menu contextuel du projet Azure, puis sélectionnez **publier**.

2. Sélectionnez le **intermédiaire** environnement et le **déboguer** configuration.

    Il s’agit uniquement à titre indicatif. Vous pouvez choisir d’exécuter vos environnements de test dans un environnement de Production. Toutefois, vous pourrez affecter les utilisateurs si vous activez le débogage à distance sur l’environnement de Production. Vous pouvez choisir la configuration Release, mais la configuration Debug rend le débogage plus facile.

    ![Choisissez la configuration Debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Suivez les étapes habituelles, mais sélectionnez le **activer le débogueur distant pour tous les rôles** case à cocher sur la **paramètres avancés** onglet.

    ![Configuration de débogage](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Pour attacher le débogueur à un service cloud dans Azure

1. Dans l’Explorateur de serveurs, développez le nœud pour votre service cloud.

2. Ouvrez le menu contextuel pour le rôle ou l’instance de rôle auquel vous souhaitez attacher, puis sélectionnez **attacher le débogueur**.

    Si vous déboguez un rôle, le débogueur Visual Studio s’attache à chaque instance de ce rôle. Le débogueur s’arrête à un point d’arrêt pour la première instance de rôle qui exécute cette ligne de code et remplit les conditions de ce point d’arrêt. Si vous déboguez une instance, le débogueur est attaché uniquement cette instance et s’arrête sur un point d’arrêt uniquement lorsque cette instance spécifique exécute cette ligne de code et remplit les conditions du point d’arrêt.

    ![Attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Une fois que le débogueur s’attache à une instance, de débogage comme d’habitude. Le débogueur s’attache automatiquement au processus hôte approprié pour votre rôle. Selon le rôle, le débogueur est attaché à w3wp.exe, WaWorkerHost.exe ou WaIISHost.exe. Pour vérifier le processus auquel le débogueur est attaché, développez le nœud d’instance dans l’Explorateur de serveurs. Consultez [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) pour plus d’informations sur les processus Azure.

    ![Sélectionnez la boîte de dialogue de type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Pour identifier les processus auxquels le débogueur est attaché, ouvrez la boîte de dialogue processus, sur la barre de menus, choisissez le déboguer, Windows, le processus. (Clavier : Ctrl + Alt + Z) Pour détacher un processus spécifique, ouvrez son menu contextuel, puis sélectionnez **détacher le processus**. Ou, recherchez le nœud d’instance dans l’Explorateur de serveurs, recherchez le processus, ouvrez son menu contextuel, puis sélectionnez **détacher le processus**.

    ![Déboguer les processus](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Évitez les arrêts longs aux points d’arrêt à distance de débogage. Azure considère un processus est arrêté pendant plus de quelques minutes comme ne répondant pas et arrête d’envoyer le trafic vers cette instance. Si vous arrêtez pendant trop longtemps, msvsmon.exe se détache du processus.

Pour détacher le débogueur de tous les processus dans votre instance ou rôle, ouvrez le menu contextuel pour le rôle ou l’instance que vous déboguez, puis sélectionnez **détacher le débogueur**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitations du débogage à distance dans Azure

À partir de la version 2.3 du Kit de développement logiciel Azure, le débogage à distance présente les limitations suivantes :

* Avec le débogage distant activé, vous ne pouvez pas publier un service cloud dans lequel un rôle comporte plus de 25 instances.
* Le débogueur utilise les ports 30400 à 30424, 31400 à 31424 et 32400 à 32424. Si vous essayez d’utiliser ces ports, vous ne pourrez pas publier votre service, et un des messages d’erreur suivants s’affiche dans le journal d’activité pour Azure :

  * Erreur lors de la validation du fichier .cscfg par rapport au fichier .csdef.
    Le port réservé plage « range » pour le point de terminaison Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector du rôle « rôle » chevauche un port déjà défini ou une plage.
  * Allocation failed. Veuillez réessayer plus tard, essayez de réduire la taille de machine virtuelle ou le nombre d’instances de rôle ou essayez de déployer vers une autre région.

## <a name="debugging-azure-virtual-machines"></a>Débogage des machines virtuelles Azure

Vous pouvez déboguer des programmes qui s’exécutent sur des machines virtuelles à l’aide de l’Explorateur de serveurs dans Visual Studio. Lorsque vous activez le débogage à distance sur une machine virtuelle Azure, Azure installe l’extension de débogage à distance sur la machine virtuelle. Ensuite, vous pouvez attacher aux processus sur l’ordinateur virtuel et déboguer comme vous le feriez normalement.

> [!NOTE]
> Les machines virtuelles créées via la pile Azure resource manager peuvent être déboguées à distance à l’aide de Cloud Explorer dans Visual Studio 2015. Pour plus d’informations, consultez [la gestion des ressources Azure avec Cloud Explorer](http://go.microsoft.com/fwlink/?LinkId=623031).

### <a name="to-debug-an-azure-virtual-machine"></a>Pour déboguer une machine virtuelle Azure

1. Dans l’Explorateur de serveurs, développez le nœud Machines virtuelles et sélectionnez le nœud de la machine virtuelle que vous souhaitez déboguer.

2. Ouvrez le menu contextuel et sélectionnez **activer le débogage**. Lorsque vous êtes invité si vous ne savez si vous souhaitez activer le débogage sur la machine virtuelle, sélectionnez **Oui**.

    Azure installe l’extension de débogage à distance sur la machine virtuelle pour activer le débogage.

    ![Machine virtuelle activer une commande de débogage](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Journal d’activité Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Une fois que l’extension de débogage à distance a terminé l’installation, ouvrez le menu contextuel de la machine virtuelle et sélectionnez **attacher le débogueur...**

    Azure Obtient une liste des processus sur l’ordinateur virtuel et les affiche dans l’attachement à la boîte de dialogue processus.

    ![Commande attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. Dans le **attacher au processus** boîte de dialogue, sélectionnez **sélectionnez** pour limiter la liste des résultats pour afficher uniquement les types de code que vous souhaitez déboguer. Vous pouvez déboguer le code managé 32 bits ou 64 bits, le code natif ou les deux.

    ![Sélectionnez la boîte de dialogue de type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sélectionnez les processus que vous souhaitez déboguer sur l’ordinateur virtuel, puis sélectionnez **attacher**. Par exemple, vous pouvez choisir le processus w3wp.exe si vous souhaitez déboguer une application web sur la machine virtuelle. Consultez [déboguer un ou plusieurs processus dans Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) et [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) pour plus d’informations.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Créer un projet web et une machine virtuelle pour le débogage

Avant de publier votre projet Windows Azure, vous pouvez s’avérer utile pour le tester dans un environnement de relation contenant-contenu qui prend en charge les scénarios de test et de débogage, et où vous pouvez installer le test et surveillance des programmes. Un pour exécuter ces tests consiste à déboguer votre application sur une machine virtuelle à distance.

Projets Visual Studio ASP.NET offrent une option permettant de créer une machine virtuelle que vous pouvez utiliser pour tester les applications. La machine virtuelle inclut des points de terminaison généralement requis tels que PowerShell, Bureau à distance et WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Pour créer un projet web et une machine virtuelle pour le débogage

1. Dans Visual Studio, créez une Application Web ASP.NET.

2. Dans la boîte de dialogue Nouveau projet ASP.NET, dans la section Azure, choisissez **Machine virtuelle** dans la zone de liste déroulante. Laissez le **créer des ressources distantes** case cochée. Sélectionnez **OK** pour continuer.

    Le **créer la machine virtuelle sur Azure** boîte de dialogue s’affiche.

    ![Créer la boîte de dialogue projet web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **Remarque :** vous devrez vous connecter à votre compte Azure si vous n’êtes pas déjà connecté.

3. Sélectionnez les différents paramètres de la machine virtuelle, puis **OK**. Consultez [Machines virtuelles](http://go.microsoft.com/fwlink/?LinkId=623033) pour plus d’informations.

    Le nom que vous entrez pour le nom DNS sera le nom de la machine virtuelle.

    ![Créer la machine virtuelle sur la boîte de dialogue Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crée la machine virtuelle, puis déploie et configure les points de terminaison, tels que le Bureau à distance et Web Deploy

4. Une fois la machine virtuelle est entièrement configurée, sélectionnez le nœud de l’ordinateur virtuel dans l’Explorateur de serveurs.

5. Ouvrez le menu contextuel et sélectionnez **activer le débogage**. Lorsque vous êtes invité si vous ne savez si vous souhaitez activer le débogage sur la machine virtuelle, sélectionnez **Oui**.

    Azure installe l’extension de débogage à distance à la machine virtuelle pour activer le débogage.

    ![Machine virtuelle activer une commande de débogage](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Journal d’activité Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publiez votre projet comme décrit dans [Comment : déployer un projet Web à l’aide de clic publication dans Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Étant donné que vous souhaitez déboguer sur la machine virtuelle, sur le **paramètres** page de la **publier le site Web** Assistant, sélectionnez **déboguer** en tant que la configuration. Cela permet de s’assurer que les symboles de code sont disponibles pendant le débogage.

    ![Paramètres de publication](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Dans le **Options de publication du fichier**, sélectionnez **supprimer les fichiers supplémentaires à la destination** si le projet a déjà été déployé à un moment antérieur.

8. Une fois le projet publié, dans le menu contextuel de la machine virtuelle dans l’Explorateur de serveurs, sélectionnez **attacher le débogueur...**

    Azure Obtient une liste des processus sur l’ordinateur virtuel et les affiche dans l’attachement à la boîte de dialogue processus.

    ![Commande attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. Dans le **attacher au processus** boîte de dialogue, sélectionnez **sélectionnez** pour limiter la liste des résultats pour afficher uniquement les types de code que vous souhaitez déboguer. Vous pouvez déboguer le code managé 32 bits ou 64 bits, le code natif ou les deux.

    ![Sélectionnez la boîte de dialogue de type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sélectionnez les processus que vous souhaitez déboguer sur l’ordinateur virtuel, puis sélectionnez **attacher**. Par exemple, vous pouvez choisir le processus w3wp.exe si vous souhaitez déboguer une application web sur la machine virtuelle. Consultez [déboguer un ou plusieurs processus dans Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) pour plus d’informations.

## <a name="next-steps"></a>Étapes suivantes

* Utilisez **Intellitrace** pour collecter un journal des appels et des événements à partir d’un serveur de publication. Consultez [débogage d’un Service Cloud publié avec IntelliTrace et Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016).

* Utilisez **Azure Diagnostics** pour consigner des informations détaillées à partir de l’exécution de code au sein de rôles, si les rôles sont en cours d’exécution dans l’environnement de développement ou dans Azure. Consultez [collecte les données de journalisation à l’aide d’Azure Diagnostics](http://go.microsoft.com/fwlink/p/?LinkId=400450).
