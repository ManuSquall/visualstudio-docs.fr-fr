---
title: Débogage à distance | Microsoft Docs
description: Déboguez une application Visual Studio qui a été déployée sur un autre ordinateur à l’aide du débogueur distant Visual Studio.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e97fd8979235f8ea89b43c6466b3119debe5b3ca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205669"
---
# <a name="remote-debugging"></a>Remote Debugging
Vous pouvez déboguer une application Visual Studio qui a été déployée sur un autre ordinateur. Pour ce faire, utilisez le débogueur distant Visual Studio.

Pour obtenir des instructions détaillées sur le débogage à distance, consultez les rubriques suivantes.

|Scénario|Lien|
|-|-|-|
|Azure App Service|[Débogage à distance ASP.net sur Azure](../debugger/remote-debugging-azure.md) ou, pour Visual Studio Enterprise, la [débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)|
|Azure VM|[Déboguer à distance ASP.NET sur Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Déboguer une application Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Débogage à distance ASP.net Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) ou [débogage à distance ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# ou Visual Basic|[Déboguer à distance un projet C# ou Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Déboguer à distance un projet C++](../debugger/remote-debugging-cpp.md)|
|Applications Windows universelles (UWP)|[Exécuter des applications UWP sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md) ou [Déboguer un package d’application installé](../debugger/debug-installed-app-package.md)|

Si vous souhaitez simplement télécharger et installer le débogueur distant et que vous n’avez pas besoin d’instructions supplémentaires pour votre scénario, suivez les étapes décrites dans cet article.

## <a name="download-and-install-the-remote-tools"></a>Télécharger et installer les outils de contrôle à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Spécifications

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Facultatif Pour exécuter le débogueur distant à partir d’un partage de fichiers

Vous pouvez trouver le débogueur distant (*msvsmon.exe*) sur un ordinateur sur lequel Visual Studio Community, Professional ou Enterprise est déjà installé. Pour certains scénarios, le moyen le plus simple de configurer le débogage à distance consiste à exécuter le débogueur distant (msvsmon.exe) à partir d’un partage de fichiers. Pour plus d’informations sur les limitations d’utilisation, consultez la page d’aide du débogueur distant (**aide > l’utilisation** dans le débogueur distant).

1. Recherchez *msvsmon.exe* dans le répertoire correspondant à votre version de Visual Studio :

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Partagez le dossier **Remote Debugger** sur l’ordinateur Visual Studio.

3. Sur l’ordinateur distant, exécutez *msvsmon.exe* à partir du dossier partagé. Suivez les [instructions d’installation](#bkmk_setup).

> [!TIP]
> Pour l’installation à partir de la ligne de commande et la référence de ligne de commande, consultez la page d’aide de *msvsmon.exe* en tapant ``msvsmon.exe /?`` la ligne de commande sur l’ordinateur sur lequel Visual Studio est installé (ou accédez à **aide > utilisation** dans le débogueur distant).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Configurer le débogueur distant

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configurer le débogueur distant
Vous pouvez modifier certains aspects de la configuration du débogueur distant après l’avoir démarré pour la première fois.

- Si vous devez ajouter des autorisations pour que d’autres utilisateurs se connectent au débogueur distant, choisissez **outils > autorisations**. Vous devez disposer de privilèges d'administrateur pour accorder ou refuser des autorisations.

     > [!IMPORTANT]
     > Vous pouvez exécuter le débogueur distant sous un compte d’utilisateur différent du compte d’utilisateur que vous utilisez sur l’ordinateur Visual Studio, mais vous devez ajouter le compte d’utilisateur différent aux autorisations du débogueur distant.

     Vous pouvez également démarrer le débogueur distant à partir de la ligne de commande avec le paramètre **\<username> /allow** : **msvsmon \<username@computer> /allow**.

- Si vous avez besoin de modifier le mode d’authentification ou le numéro de port, ou de spécifier une valeur de délai d’attente pour les outils de contrôle à distance : choisissez **outils > options**.

     Pour obtenir la liste des numéros de port utilisés par défaut, consultez [affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Vous pouvez choisir d'exécuter les outils de contrôle à distance en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n'existe aucune sécurité du réseau lorsque vous lancez l'exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n’est pas exposé à des failles de sécurité liées à des programmes malveillants ou du trafic dangereux.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Facultatif Configurer le débogueur distant en tant que service
Pour le débogage dans ASP.NET et d’autres environnements de serveur, vous devez exécuter le débogueur distant en tant qu’administrateur ou, si vous souhaitez qu’il soit toujours en cours d’exécution, exécuter le débogueur distant en tant que service.

 Si vous souhaitez configurer le débogueur distant en tant que service, procédez comme suit.

1. Recherchez l’ **Assistant Configuration Remote Debugger** (rdbgwiz.exe). (Il s’agit d’une application distincte du débogueur distant.) Elle est disponible uniquement lorsque vous installez les outils de contrôle à distance. Il n’est pas installé avec Visual Studio.

2. Démarrez l’Assistant Configuration. Quand la première page s’affiche, cliquez sur **Suivant**.

3. Cochez la case **Exécuter le débogueur distant Visual Studio 2015 en tant que service** .

4. Ajoutez le nom du compte d’utilisateur et le mot de passe.

    Vous devrez peut-être ajouter le droit utilisateur **ouvrir une session en tant que service** à ce compte (recherchez **stratégie de sécurité locale** (secpol. msc) dans la page ou la fenêtre de **démarrage** (ou tapez **secpol** dans une invite de commandes). Quand la fenêtre s’affiche, double-cliquez sur **Attribution des droits utilisateur**, puis recherchez **Ouvrir une session en tant que service** dans le volet droit. Double-cliquez dessus. Ajoutez le compte d’utilisateur à la fenêtre **Propriétés** et cliquez sur **OK**). Cliquez sur **Suivant**.

5. Sélectionnez le type de réseau avec lesquel vous voulez que les outils de contrôle à distance communiquent. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément. Cliquez sur **Suivant**.

6. Si le service peut être démarré, le message suivant s’affiche : **L’Assistant Configuration Visual Studio Remote Debugger est terminé**. Si le service ne peut pas être démarré, le message suivant s’affiche : **Échec de l’Assistant Configuration Débogueur distant Visual Studio**. La page fournit également des conseils à suivre pour faire démarrer le service.

7. Cliquez sur **Terminer**.

   À ce stade, le débogueur distant s’exécute en tant que service. Vous pouvez le vérifier en accédant au **panneau de configuration > services** et en recherchant le **débogueur distant Visual Studio 2015**.

   Vous pouvez arrêter et démarrer le service du débogueur distant à partir du **panneau de configuration > services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi

- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Débogage à distance ASP.NET Core sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)