---
title: Débogage d’un service cloud ou d’une machine virtuelle Azure
description: Débogage d’un service cloud ou d’une machine virtuelle dans Visual Studio
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 8669e4636be28d6462c6658a54fc818bae577905
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997668"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Débogage d'un service cloud ou d'une machine virtuelle Azure dans Visual Studio

Visual Studio vous offre différentes options de débogage des machines virtuelles et services cloud Azure.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Déboguer votre service cloud sur votre ordinateur local

Vous pouvez gagner du temps et de l’argent en utilisant l’émulateur de calcul Azure pour déboguer votre service Cloud sur un ordinateur local. Déboguer un service localement avant de le déployer vous permet d’améliorer la fiabilité et les performances, tout en évitant les coûts de temps de calcul. Certaines erreurs peuvent toutefois se produire quand vous exécutez un service cloud directement dans Azure. Vous pouvez déboguer ces erreurs si vous activez le débogage distant quand vous publiez votre service, puis attachez le débogueur à une instance de rôle.

L’émulateur simule le service de calcul Azure et s’exécute dans votre environnement local pour vous permettre de tester et déboguer votre service cloud avant son déploiement. Il gère le cycle de vie de vos instances de rôle et donne accès aux ressources simulées, telles que le stockage local. Quand vous déboguez ou exécutez votre service à partir de Visual Studio, le programme démarre automatiquement l’émulateur comme une application d’arrière-plan, puis déploie votre service vers l’émulateur. Vous pouvez utiliser l’émulateur pour voir votre service en cours d’exécution dans l’environnement local. Vous pouvez exécuter la version complète ou express de l’émulateur. (À partir d’Azure 2,3, la version Express de l’émulateur est celle par défaut.) Consultez [utilisation de l’émulateur Express pour exécuter et déboguer un service Cloud localement](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Pour déboguer votre service cloud sur votre ordinateur local

1. Dans la barre de menus, sélectionnez **Déboguer**  >  **Démarrer le débogage** pour exécuter votre projet de service Cloud Azure. Vous pouvez aussi appuyer sur F5. Un message s’affiche, indiquant que l’émulateur de calcul est en cours de démarrage. Une icône s’affiche dans la zone de notification pour confirmer le démarrage de l’émulateur.

    ![Émulateur Azure dans la zone de notification](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Affichez l’interface utilisateur de l’émulateur de calcul en ouvrant le menu contextuel de l’icône Azure dans la zone de notification, puis en sélectionnant **Afficher l’interface utilisateur de l’émulateur de calcul**.

    Le volet gauche de l'interface utilisateur montre les services actuellement déployés sur l'émulateur de calcul et les instances de rôle en cours d'exécution sur chaque service. Vous pouvez sélectionner le service ou des rôles pour afficher les informations liées au cycle de vie, aux journaux et aux diagnostics dans le volet de droite. Si vous placez le focus dans la marge supérieure d’une fenêtre incluse, celle-ci se développe pour remplir le volet droit.

3. Parcourez l’application en choisissant des commandes dans le menu **Déboguer** et en définissant des points d’arrêt dans votre code. À mesure que vous parcourez l'application dans le débogueur, les volets sont mis à jour avec l'état actuel de l'application. Lorsque vous arrêtez le débogage, le déploiement de l’application est supprimé. Si votre application inclut un rôle web et que vous avez réglé la propriété Action de démarrage pour démarrer le navigateur web, Visual Studio démarre votre application web dans le navigateur. Si vous modifiez le nombre d’instances d’un rôle dans la configuration du service, vous devez arrêter votre service cloud, puis redémarrer le débogage afin de pouvoir déboguer ces nouvelles instances du rôle.

    > [!NOTE]
    > Quand vous cessez l’exécution ou le débogage de votre service, les émulateurs de calcul et de stockage locaux ne s’arrêtent pas. Vous devez les arrêter explicitement à partir de la zone de notification.

## <a name="debug-a-cloud-service-in-azure"></a>Déboguer un service cloud dans Azure

Pour déboguer un service cloud à partir d’une machine distante, vous devez activer cette fonctionnalité de façon explicite au moment du déploiement de ce service. Tous les services nécessaires (msvsmon.exe, par exemple) sont alors installés sur les machines virtuelles qui exécutent vos instances de rôle. Si vous n’avez pas activé le débogage distant quand vous avez publié le service, vous devez republier ce service avec le débogage distant activé.

L’activation du débogage distant pour un service cloud n’entraîne pas de baisse des performances, ni de coûts supplémentaires. N’utilisez pas le débogage distant pour un service de production, car cela peut avoir un impact pour les clients qui utilisent ce service.

> [!NOTE]
> Quand vous publiez un service cloud à partir de Visual Studio, vous pouvez activer **IntelliTrace** pour tous les rôles de ce service qui ciblent .NET Framework 4 ou .NET Framework 4.5. Avec **IntelliTrace**, vous pouvez examiner des événements qui se sont déjà produits dans une instance de rôle et reproduire le contexte de ce moment-là. Consultez [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) et [Utilisation d’IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Pour activer le débogage distant pour un service cloud

1. Ouvrez le menu contextuel du projet Azure, puis sélectionnez **Publier**.

2. Sélectionnez l’environnement **Intermédiaire** et la configuration **Débogage**.

    Il s’agit simplement d’une indication. Vous pouvez choisir d’exécuter vos environnements de test dans un environnement de production. L’activation du débogage distant sur l’environnement de production risque toutefois d’avoir un impact pour les utilisateurs. Vous pouvez choisir la configuration Release, mais la configuration Debug présente l’avantage de simplifier le débogage.

    ![Choisir la configuration Debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Suivez les étapes habituelles, en veillant à cocher la case **Activer le débogueur distant pour tous les rôles** dans l’onglet **Paramètres avancés**.

    ![Configuration Debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Pour attacher le débogueur à un service cloud dans Azure

1. Dans l’Explorateur de serveurs, développez le nœud de votre service cloud.

2. Ouvrez le menu contextuel du rôle ou de l’instance de rôle auquel vous souhaitez joindre le débogueur, puis sélectionnez **Attacher le débogueur**.

    Si vous déboguez un rôle, le débogueur Visual Studio s'attache à chaque instance de ce rôle. Le débogueur s’arrêtera sur un point d’arrêt pour la première instance de rôle qui exécute cette ligne de code et remplit les conditions de ce point d’arrêt. Si vous déboguez une instance, le débogueur est attaché uniquement à cette instance, et s’arrête sur un point d’arrêt quand cette instance spécifique exécute cette ligne de code et remplit les conditions du point d’arrêt.

    ![Attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Une fois que le débogueur est joint à une instance, déboguez comme vous le feriez normalement. Le débogueur se joint automatiquement au processus hôte approprié pour votre rôle. Selon le rôle, le débogueur est attaché à w3wp.exe, WaWorkerHost.exe ou WaIISHost.exe. Pour identifier le processus auquel le débogueur est attaché, développez le nœud de l’instance dans l’Explorateur de serveurs. Pour plus d’informations sur les processus Azure, consultez [Architecture de rôle Azure](/archive/blogs/kwill/windows-azure-role-architecture).

    ![Boîte de dialogue Sélectionner le type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Pour identifier les processus auxquels le débogueur est attaché, dans la barre de menus, sélectionnez **Déboguer** les  >    >  **processus** Windows, puis ouvrez la boîte de dialogue **processus** . (Raccourci : Ctrl+Alt+Z) Pour détacher un processus spécifique, ouvrez son menu contextuel, puis sélectionnez **Détacher le processus**. Vous pouvez aussi afficher le nœud d’instance dans l’Explorateur de serveurs, rechercher le processus et ouvrir son menu contextuel, puis sélectionnez **Détacher le processus**.

    ![Processus de débogage](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Évitez les arrêts longs aux points d'arrêt avec le débogage à distance. Azure considère qu’un processus arrêté depuis plusieurs minutes ne répond pas, et cesse d’envoyer du trafic vers cette instance. Si l’arrêt est trop long, msvsmon.exe est détaché du processus.

Pour détacher le débogueur de tous les processus dans votre instance ou rôle, ouvrez le menu contextuel du rôle ou de l’instance que vous déboguez, puis sélectionnez **Détacher le débogueur**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitations du débogage distant dans Azure

À partir de la version 2.3 du Kit de développement logiciel (SDK), le débogage à distance présente les limitations ci-dessous :

* Quand le débogage distant est activé, vous ne pouvez pas publier un service cloud dans lequel un rôle comporte plus de 25 instances.
* Le débogueur utilise les ports 30400 à 30424, 31400 à 31424 et 32400 à 32424. Si vous essayez d’utiliser ces ports, vous ne pourrez pas publier votre service, et l’un des messages d’erreur suivants s’affichera dans le journal des activités Azure :

  * Erreur lors de la validation du fichier .cscfg par rapport au fichier .csdef.
    La plage de ports réservée ('range') pour le point de terminaison Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector du rôle ('role') chevauche une plage ou un port déjà défini.
  * L’allocation a échoué. Réessayez ultérieurement, essayez de réduire la taille de la machine virtuelle ou le nombre d’instances de rôle, ou essayez de déployer dans une autre région.

## <a name="debugging-azure-virtual-machines"></a>Déboguer des machines virtuelles Azure

Vous pouvez déboguer des programmes exécutés sur des machines virtuelles Azure à l’aide de l’Explorateur de serveurs dans Visual Studio. Quand vous activez le débogage distant sur une machine virtuelle Azure, Azure installe l’extension de débogage distant sur cette machine virtuelle. Vous pouvez ensuite l’attacher aux processus sur la machine virtuelle et procéder au débogage normalement.

> [!NOTE]
> Les machines virtuelles créées via la pile Azure Resource Manager peuvent être déboguées à distance à l’aide de Cloud Explorer dans Visual Studio 2015. Pour plus d’informations, consultez [Gestion des ressources Azure avec Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Pour déboguer une machine virtuelle Azure

1. Dans l’Explorateur de serveurs, développez le nœud Machines virtuelles, puis sélectionnez le nœud de la machine virtuelle à déboguer.

2. Ouvrez le menu contextuel, puis sélectionnez **Activer le débogage**. Quand vous êtes invité à confirmer l’activation du débogage sur la machine virtuelle, sélectionnez **Oui**.

    Azure installe l’extension de débogage distant sur la machine virtuelle pour activer le débogage.

    ![Commande d’activation du débogage de machine virtuelle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Journal des activités Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Une fois l’extension de débogage à distance installée, ouvrez le menu contextuel de la machine virtuelle et sélectionnez **Attacher le débogueur...**

    Azure récupère la liste des processus sur la machine virtuelle et les affiche dans la boîte de dialogue **Attacher au processus**.

    ![Commande Attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. Dans la boîte de dialogue **Attacher au processus**, sélectionnez **Sélectionner** pour limiter la liste des résultats et afficher uniquement les types de code que vous voulez déboguer. Vous pouvez déboguer du code managé 32 ou 64 bits, du code natif ou les deux.

    ![Boîte de dialogue Sélectionner le type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Choisissez les processus que vous souhaitez déboguer sur la machine virtuelle, puis cliquez sur **attacher**. Par exemple, vous pouvez choisir le processus w3wp.exe pour déboguer une application web sur la machine virtuelle. Pour plus d’informations, consultez [Déboguer un ou plusieurs processus dans Visual Studio](../debugger/debug-multiple-processes.md) et [Architecture de rôle Azure](/archive/blogs/kwill/windows-azure-role-architecture).

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Créer un projet web et une machine virtuelle pour le débogage

Avant de publier votre projet Azure, il peut être utile de le tester dans un environnement contrôlé qui prend en charge les scénarios de test et de débogage, et où vous pouvez installer les programmes de test et de surveillance. Pour effectuer de tels tests, vous pouvez déboguer votre application à distance sur une machine virtuelle.

Les projets Visual Studio ASP.NET permettent de créer une machine virtuelle que vous pouvez utiliser pour tester les applications. La machine virtuelle inclut les points de terminaison généralement requis tels que PowerShell, le Bureau à distance et WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Pour créer un projet web et une machine virtuelle pour le débogage

1. Dans Visual Studio, créez une application web ASP.NET.

2. Dans la boîte de dialogue Nouveau projet ASP.NET, dans la section Azure, sélectionnez **machine virtuelle** dans la zone de liste déroulante. Laissez la case à cocher **Créer des ressources distantes** activée. Sélectionnez **OK** pour poursuivre.

    La boîte de dialogue **Créer une machine virtuelle sur Azure** apparaît.

    ![Boîte de dialogue de création de projet web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Vous êtes invité à vous connecter à votre compte Azure si vous ne l’êtes pas déjà.

3. Choisissez les différents paramètres de la machine virtuelle, puis cliquez sur **OK**. Pour plus d’informations, consultez [Machines virtuelles](/azure/virtual-machines/) .

    Le nom que vous entrez dans le champ Nom DNS sera le nom de votre machine virtuelle.

    ![Boîte de dialogue Créer une machine virtuelle sur Microsoft Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crée la machine virtuelle, puis provisionne et configure les points de terminaison, tels que Bureau à distance et Web Deploy.

4. Une fois la machine virtuelle entièrement configurée, sélectionnez son nœud dans l’Explorateur de serveurs.

5. Ouvrez le menu contextuel, puis sélectionnez **Activer le débogage**. Quand vous êtes invité à confirmer l’activation du débogage sur la machine virtuelle, sélectionnez **Oui**.

    Azure installe l’extension de débogage distant sur la machine virtuelle pour activer le débogage.

    ![Commande d’activation du débogage de machine virtuelle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Journal des activités Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publiez votre projet comme décrit dans la rubrique [Déploiement d’un projet web à l’aide de la publication en un clic dans Visual Studio](/previous-versions/aspnet/dd465337(v=vs.110)). Comme vous voulez effectuer le débogage sur la machine virtuelle, sur la page **Paramètres** de l’Assistant **Publier le site web**, sélectionnez la configuration **Débogage**. Ceci permet de s’assurer que les symboles de code sont disponibles pendant le débogage.

    ![Paramètres de publication](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Dans les **Options de publication des fichiers**, sélectionnez **Supprimer les fichiers supplémentaires à la destination** si le projet a déjà été déployé précédemment.

8. Une fois le projet publié, dans le menu contextuel de la machine virtuelle dans l’Explorateur de serveurs, sélectionnez **Attacher le débogueur...**

    Azure récupère la liste des processus sur la machine virtuelle et les affiche dans la boîte de dialogue **Attacher au processus**.

    ![Commande Attacher le débogueur](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. Dans la boîte de dialogue **Attacher au processus**, sélectionnez **Sélectionner** pour limiter la liste des résultats et afficher uniquement les types de code que vous voulez déboguer. Vous pouvez déboguer du code managé 32 ou 64 bits, du code natif ou les deux.

    ![Boîte de dialogue Sélectionner le type de code](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Choisissez les processus que vous souhaitez déboguer sur la machine virtuelle, puis cliquez sur **attacher**. Par exemple, vous pouvez choisir le processus w3wp.exe pour déboguer une application web sur la machine virtuelle. Pour plus d’informations, consultez [Déboguer un ou plusieurs processus dans Visual Studio](../debugger/debug-multiple-processes.md) .

## <a name="next-steps"></a>Étapes suivantes

* Utilisez **IntelliTrace** pour collecter un journal des appels et des événements à partir d’un serveur de mise en sortie. Consultez [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Utilisez les **Diagnostics Azure** pour collecter des informations détaillées du code actuellement exécuté dans des rôles qui sont eux-mêmes exécutés dans l’environnement de développement ou dans Azure. Consultez [Collecter des données de journalisation avec les diagnostics Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).