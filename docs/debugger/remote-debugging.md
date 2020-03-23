---
title: Débogage à distance Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
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
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302076"
---
# <a name="remote-debugging"></a>Débogage à distance
Vous pouvez déboguer une application Visual Studio qui a été déployée sur un autre ordinateur. Pour ce faire, utilisez le débogueur distant Visual Studio.

Pour des instructions approfondies sur le débogage à distance, voir ces sujets.

|Scénario|Lien|
|-|-|-|
|Azure App Service|[Snapshot Debugger](../debugger/debug-live-azure-applications.md) ou [Remote debug ASP.NET sur Azure](../debugger/remote-debugging-azure.md)|
|Azure VM|[Déboguer à distance ASP.NET sur Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debug une application Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Débogé à distance ASP.NET cœur](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) ou [ASP.NET de débogé à distance](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# ou Visual Basic|[Débogage distant d’un projet C# ou Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Débogé à distance d’un projet de C](../debugger/remote-debugging-cpp.md)|
|Applications Windows universelles (UWP)|[Exécutez des applications UWP sur une machine distante](../debugger/run-windows-store-apps-on-a-remote-machine.md) ou [Debug un paquet d’applications installé](../debugger/debug-installed-app-package.md)|

Si vous voulez juste télécharger et installer le débbuggeur à distance et n’avez pas besoin d’instructions supplémentaires pour votre scénario, suivez les étapes de cet article.

## <a name="download-and-install-the-remote-tools"></a>Télécharger et installer les outils de contrôle à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Exigences

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Facultatif) Pour exécuter le débbugger à distance à partir d’une part de fichier

Vous pouvez trouver le débbugger à distance (*msvsmon.exe*) sur un ordinateur avec Visual Studio Community, Professional, ou Enterprise déjà installé. Pour certains scénarios, la façon la plus simple de configurer le débogage à distance est d’exécuter le débbuggeur à distance (msvsmon.exe) à partir d’une part de fichier. Pour les limitations d’utilisation, voir la page d’aide du débbuggeur à distance **(Aide > Utilisation** dans le débbuggeur à distance).

1. Trouvez *msvsmon.exe* dans le répertoire correspondant à votre version de Visual Studio:

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
> Pour l’installation de la ligne de commande et la référence de ``msvsmon.exe /?`` la ligne de commande, voir la page d’aide pour *msvsmon.exe* en tapant dans la ligne de commande sur l’ordinateur avec Visual Studio installé (ou aller à Help > **Usage** dans le débbugger à distance).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurer le débbugger à distance

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Configurer le débbuggeur à distance
Vous pouvez modifier certains aspects de la configuration du débogueur distant après l’avoir démarré pour la première fois.

- Si vous avez besoin d’ajouter des autorisations pour que d’autres utilisateurs se connectent au débbuggeur distant, choisissez **Tools > Permissions**. Vous devez disposer de privilèges d'administrateur pour accorder ou refuser des autorisations.

     > [!IMPORTANT]
     > Vous pouvez exécuter le débbugger à distance sous un compte utilisateur qui diffère du compte utilisateur que vous utilisez sur l’ordinateur Visual Studio, mais vous devez ajouter le compte utilisateur différent aux autorisations du débbuggeur à distance.

     Alternativement, vous pouvez démarrer le débbuggeur à distance de la ligne de commande avec le **nom d’utilisateur \</autoriser>** paramètre: **msvsmon \< username@computer /allow>**.

- Si vous avez besoin de modifier le mode Authentification ou le numéro de port, ou spécifier une valeur de délai d’attente pour les outils distants: choisissez **Des outils > Options**.

     Pour une liste des numéros portuaires utilisés par défaut, voir [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Vous pouvez choisir d'exécuter les outils de contrôle à distance en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n'existe aucune sécurité du réseau lorsque vous lancez l'exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n’est pas exposé à des failles de sécurité liées à des programmes malveillants ou du trafic dangereux.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Facultatif) Configurer le débbugger à distance comme un service
Pour débogage dans ASP.NET et d’autres environnements serveur, vous devez soit exécuter le débbugger à distance en tant qu’administrateur ou, si vous voulez qu’il fonctionne toujours, exécuter le débbugger à distance comme un service.

 Si vous souhaitez configurer le débbuggeur à distance comme un service, suivez ces étapes.

1. Recherchez l’ **Assistant Configuration Remote Debugger** (rdbgwiz.exe). (Il s’agit d’une application distincte du Debugger à distance.) Il n’est disponible que lorsque vous installez les outils distants. Il n’est pas installé avec Visual Studio.

2. Démarrez l’Assistant Configuration. Quand la première page s’affiche, cliquez sur **Suivant**.

3. Cochez la case **Exécuter le débogueur distant Visual Studio 2015 en tant que service** .

4. Ajoutez le nom du compte d’utilisateur et le mot de passe.

    Vous devrez peut-être ajouter le **Journal en tant qu’utilisateur de service** droit à ce compte (Trouver la politique de sécurité **locale** (secpol.msc) dans la page **de démarrage** ou la fenêtre (ou **tapez secpol** à une invite de commande). Quand la fenêtre s’affiche, double-cliquez sur **Attribution des droits utilisateur**, puis recherchez **Ouvrir une session en tant que service** dans le volet droit. Double-cliquez dessus. Ajoutez le compte d’utilisateur à la fenêtre **Propriétés** et cliquez sur **OK**). Cliquez sur **Suivant**.

5. Sélectionnez le type de réseau avec lesquel vous voulez que les outils de contrôle à distance communiquent. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément. Cliquez sur **Suivant**.

6. Si le service peut être démarré, le message suivant s’affiche : **L’Assistant Configuration Visual Studio Remote Debugger est terminé**. Si le service ne peut pas être démarré, le message suivant s’affiche : **Échec de l’Assistant Configuration Débogueur distant Visual Studio**. La page fournit également des conseils à suivre pour faire démarrer le service.

7. Cliquez sur **Terminer**.

   À ce stade, le débogueur distant s’exécute en tant que service. Vous pouvez le vérifier en allant à **Control Panel > Services** et à la recherche de Visual Studio **2015 Remote Debugger**.

   Vous pouvez arrêter et démarrer le service de débbuggeur à distance à partir de **Control Panel > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi

- [Premier regard sur le débbugger](../debugger/debugger-feature-tour.md)
- [Configurer le pare-feu Windows pour le débugging à distance](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Debugging à distance ASP.NET cœur sur un ordinateur à distance IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)