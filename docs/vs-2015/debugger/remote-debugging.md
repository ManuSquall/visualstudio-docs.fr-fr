---
title: Débogage à distance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300563"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez déboguer une application Visual Studio qui a été déployée sur un autre ordinateur.  Pour ce faire, utilisez le débogueur distant Visual Studio.  
  
 Ces informations s’appliquent aux applications de bureau Windows et aux applications ASP.NET.  Pour plus d’informations sur le débogage distant d’applications du Windows Store et d’applications Azure, consultez [débogage à distance sur les applications Windows Store et Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Procurez-vous les outils de contrôle à distance  
Vous pouvez télécharger les outils de contrôle à distance directement sur l’appareil ou le serveur que vous souhaitez déboguer, ou vous pouvez obtenir les outils de contrôle à distance à partir de votre ordinateur hôte sur lequel Visual Studio est installé.

### <a name="to-download-and-install-the-remote-tools"></a>Pour télécharger et installer les outils de contrôle à distance
  
1. Sur l’appareil ou le serveur que vous souhaitez déboguer (plutôt que sur l’ordinateur exécutant Visual Studio), procurez-vous la version appropriée des outils de contrôle à distance.

    |Version|Lien|Remarques|
    |-|-|-|
    |Visual Studio 2015 Update 3|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, joignez le groupe de Visual Studio Dev Essentials gratuit. vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Rouvrez ensuite le lien si nécessaire. Téléchargez toujours la version correspondant au système d’exploitation de votre appareil (version x86, x64 ou ARM)|
    |Visual Studio 2015 (plus ancien)|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, joignez le groupe de Visual Studio Dev Essentials gratuit. vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Rouvrez ensuite le lien si nécessaire.|
    |Visual Studio 2013|[outils de contrôle à distance.](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Page de téléchargement dans Visual Studio 2013 documentation|
    |Visual Studio 2012|[outils de contrôle à distance.](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Page de téléchargement dans la documentation de Visual Studio 2012|
  
2. Sur la page de téléchargement, choisissez la version des outils qui correspond à votre système d’exploitation (version x86, x64 ou ARM) et téléchargez les outils de contrôle à distance.
  
    > [!IMPORTANT]
    > Nous vous recommandons d’installer la version la plus récente des outils de contrôle à distance qui correspond à votre version de Visual Studio. Les versions incompatibles ne sont pas recommandées.  
    >   
    >  En outre, vous devez installer les outils de contrôle à distance qui ont la même architecture que le système d’exploitation sur lequel vous souhaitez l’installer. En d’autres termes, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation 64 bits, vous devez installer la version 64 bits des outils de contrôle à distance sur l’ordinateur distant.  
  
3. Une fois que vous avez terminé de télécharger le fichier exécutable, suivez les instructions pour installer l’application sur l’ordinateur distant. Voir les [instructions d’installation](#bkmk_setup)

Si vous essayez de copier le débogueur distant (msvsmon.exe) sur l’ordinateur distant et que vous l’exécutez, sachez que l' **Assistant Configuration du débogueur distant** (**rdbgwiz.exe**) est installé uniquement lorsque vous téléchargez les outils, et vous devrez peut-être utiliser l’Assistant pour la configuration ultérieurement, en particulier si vous souhaitez que le débogueur distant s’exécute en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](#bkmk_configureService) ci-dessous.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Pour exécuter le débogueur distant à partir d’un partage de fichiers

Vous pouvez trouver le débogueur distant (**msvsmon.exe**) sur un ordinateur sur lequel Visual Studio 2015 Community, Professional ou Enterprise est déjà installé. Pour de nombreux scénarios, le moyen le plus simple de configurer le débogage à distance consiste à exécuter le débogueur distant (msvsmon.exe) à partir d’un partage de fichiers. Pour connaître les limitations d’utilisation, consultez la page d’aide du débogueur distant (**aide/utilisation** dans le débogueur distant).

1. Recherchez **msvsmon.exe** dans le répertoire correspondant à votre version de Visual Studio. Pour Visual Studio 2015 :

      **Program Files\Microsoft Visual Studio 14.0 \ Common7\ide\remote Debugger Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0 \ Common7\ide\remote Debugger Debugger\x64\msvsmon.exe**

2. Partagez le dossier **Remote Debugger** sur l’ordinateur Visual Studio.

3. Sur l’ordinateur distant, exécutez **msvsmon.exe**. Suivez les [instructions d’installation](#bkmk_setup).

> [!TIP] 
> Pour l’installation de ligne de commande et la référence de ligne de commande, consultez la page d’aide de **msvsmon.exe** en tapant ``msvsmon.exe /?`` la ligne de commande sur l’ordinateur sur lequel Visual Studio est installé (ou accédez à **aide/utilisation** dans le débogueur distant).

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge  
 L’ordinateur distant doit exécuter l’un des systèmes d’exploitation suivants :  
  
- Windows 10  
  
- Windows 8 ou 8.1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 ou Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configurations matérielles prises en charge  
  
- Processeur 1,6 GHz minimum  
  
- 1 Go de RAM (1,5 Go s’il s’agit d’une machine virtuelle)  
  
- 1 Go d'espace disque disponible  
  
- Disque dur 5400 tr/min  
  
- Carte vidéo DirectX 9 s’exécutant avec une résolution d’affichage de 1024 x 768 ou supérieure  
  
## <a name="network-configuration"></a>Configuration réseau  
 L’ordinateur distant et l’ordinateur Visual Studio doivent être connectés sur un réseau, un groupe de travail, un groupe résidentiel ou directement connectés à l’aide d’un câble Ethernet. Le débogage sur Internet n’est pas pris en charge.  
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurer le débogueur distant  
 Vous devez disposer des autorisations d’administration sur l’ordinateur distant  
  
1. Recherchez l’application du débogueur distant. (Ouvrez le menu Démarrer et recherchez **débogueur distant**.)
  
    Si vous exécutez le débogueur distant sur un serveur distant, vous pouvez cliquer avec le bouton droit sur l’application du débogueur distant et choisir **exécuter en tant qu’administrateur** (ou vous pouvez exécuter le débogueur distant en tant que service). Si vous ne l’exécutez pas sur un serveur distant, il vous suffit de le démarrer normalement.
  
2. Lorsque vous démarrez les outils de contrôle à distance pour la première fois (ou avant de le configurer), la boîte de dialogue **configuration du débogage distant** s’affiche.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Si l’API de service Windows n’est pas installée (ce qui se produit uniquement sur Windows Server 2008 R2), choisissez le bouton **installer** .  
  
4. Sélectionnez les types de réseau sur lesquels vous voulez utiliser les outils de contrôle à distance. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément, selon les besoins.  
  
5. Choisissez **configurer le débogage distant** pour configurer le pare-feu et démarrer l’outil.  
  
6. Une fois la configuration terminée, la fenêtre du débogueur distant s’affiche.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Le débogueur distant attend maintenant une connexion. Notez le nom du serveur et le numéro de port qui s’affichent, car vous en aurez besoin plus tard pour la configuration dans Visual Studio.  
  
   Lorsque vous avez terminé le débogage et que vous devez arrêter le débogueur distant, cliquez sur **fichier/quitter** dans la fenêtre. Vous pouvez le redémarrer à partir du menu **Démarrer** ou à partir de la ligne de commande :  
  
   Le ** \<Visual Studio installation directory> débogueur \Common7\IDE\Remote \\<x86, x64 ou Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurer le débogueur distant  
 Vous pouvez modifier certains aspects de la configuration du débogueur distant après l’avoir démarré pour la première fois.
  
- Pour permettre à d’autres utilisateurs de se connecter au débogueur distant, choisissez **Outils/autorisations**. Vous devez disposer de privilèges d'administrateur pour accorder ou refuser des autorisations.

  > [!IMPORTANT]
  > Vous pouvez exécuter le débogueur distant sous un compte d’utilisateur différent du compte d’utilisateur que vous utilisez sur l’ordinateur Visual Studio, mais vous devez ajouter le compte d’utilisateur différent aux autorisations du débogueur distant. 

   Vous pouvez également démarrer le débogueur distant à partir de la ligne de commande avec le paramètre ** \<username> /allow** : **msvsmon \<username@computer> /allow **.
  
- Pour modifier le mode d’authentification ou le numéro de port, ou pour spécifier une valeur de délai d’attente pour les outils de contrôle à distance : choisissez **Outils/Options**.  
  
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
  
    Vous devez peut-être ajouter le droit utilisateur **Ouvrir une session en tant que service** pour ce compte. (Recherchez **Stratégie de sécurité locale** (secpol.msc) dans la page ou la fenêtre **Démarrer** (ou tapez **secpol.msc** à l’invite de commande). Quand la fenêtre s’affiche, double-cliquez sur **Attribution des droits utilisateur**, puis recherchez **Ouvrir une session en tant que service** dans le volet droit. Double-cliquez dessus. Ajoutez le compte d’utilisateur à la fenêtre **Propriétés** et cliquez sur **OK**.) Cliquez sur **suivant**.  
  
5. Sélectionnez le type de réseau avec lesquel vous voulez que les outils de contrôle à distance communiquent. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément. Cliquez sur **Suivant**.  
  
6. Si le service peut être démarré, le message suivant s’affiche : **L’Assistant Configuration Visual Studio Remote Debugger est terminé**. Si le service ne peut pas être démarré, le message suivant s’affiche : **Échec de l’Assistant Configuration Débogueur distant Visual Studio**. La page fournit également des conseils à suivre pour faire démarrer le service.  
  
7. Cliquez sur **Terminer**.  
  
   À ce stade, le débogueur distant s’exécute en tant que service. Vous pouvez le vérifier en accédant à **Panneau de configuration / Services** et en recherchant **Débogueur distant Visual Studio 2015**.  
  
   Vous pouvez arrêter et démarrer le service du débogueur distant à partir de **Panneau de configuration / Services**.  

## <a name="remote-debug-an-aspnet-application"></a>Déboguer à distance une application ASP.NET  
 Le déploiement d’une application ASP.NET sur un ordinateur distant qui exécute IIS implique différentes étapes, selon le système d’exploitation et la version d’IIS. Pour les ordinateurs distants qui exécutent Windows Server 2008 ou Windows Server 2012 sur lesquels IIS 7,5 ou une version ultérieure est installé, veuillez consulter [ASP.net de débogage distant sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Si vous déboguez une application ASP.NET Core, consultez [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html). Différentes étapes sont requises pour publier un ASP.NET Core sur IIS. Une fois que vous avez correctement publié une application ASP.NET Core, vous pouvez la déboguer à distance comme d' [autres applications ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), à ceci près que le processus à attacher est dnx.exe au lieu de w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Débogage distant d’un projet Visual C++  
 Dans la procédure suivante, le nom et le chemin d’accès du projet sont C:\remotetemp\MyMfc, et le nom de l’ordinateur distant est **MJO-DL**.  
  
1. Créez une application MFC nommée **mymfc**.  
  
2. Définissez un point d’arrêt facilement accessible quelque part dans l’application, par exemple dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.  
  
3. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**. Ouvrez l’onglet **Débogage**.  
  
4. Définissez **Débogueur à lancer** sur **Débogueur Windows distant**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Appliquez les modifications suivantes aux propriétés :  
  
   |Paramètre|Valeur|
   |-|-|  
   |Commande distante|C:\remotetemp\mymfc.exe|  
   |Répertoire de travail|C:\remotetemp|  
   |Nom du serveur distant|MJO-DL :*numéro_port*|  
   |Connexion|À distance avec authentification Windows|  
   |Type de débogueur|Natif uniquement|  
   |Répertoire de déploiement|C:\remotetemp.|  
   |Fichiers supplémentaires à déployer|C:\data\mymfcdata.txt.|  
  
    Si vous déployez des fichiers supplémentaires (facultatif), le dossier doit exister sur les deux ordinateurs.  
  
6. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution et choisissez **Configuration Manager**.  
  
7. Pour la configuration **Debug**, cochez la case **Déployer**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Démarrez le débogage (**Déboguer/démarrer le débogage**, ou **F5**).  
  
9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.  
  
10. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à la machine distante.  
  
     Les informations d’identification requises sont spécifiques à la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez choisir un certificat de sécurité ou entrer votre nom de domaine et votre mot de passe. Sur un ordinateur qui n’est pas un domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong> , ainsi que le mot de passe correct.  
  
11. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.  
  
    > [!TIP]
    > Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **mymfc**, puis choisissez **Déployer**.  
  
    Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans le **Explorateur de solutions**, cliquez sur **Ajouter/nouveau dossier**.) Ajoutez ensuite les fichiers au dossier (dans le **Explorateur de solutions**, cliquez sur **Ajouter/élément existant**, puis sélectionnez les fichiers.). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Débogage distant d’un projet Visual C# ou Visual Basic  
 Le débogueur ne peut pas déployer d’applications de bureau Visual C# ou Visual Basic sur un ordinateur distant, mais vous pouvez toujours les déboguer à distance comme suit. La procédure suivante suppose que vous souhaitez la déboguer sur un ordinateur nommé **MJO-DL**, comme indiqué dans l’illustration précédente.
  
1. Créez un projet WPF nommé **MyWpf**.  
  
2. Définissez un point d’arrêt facilement accessible quelque part dans le code.  
  
    Par exemple, vous pouvez définir un point d’arrêt dans un gestionnaire de boutons. Pour ce faire, Ouvrez MainWindow. xaml, ajoutez un contrôle Button à partir de la boîte à outils, puis double-cliquez sur le bouton pour ouvrir son gestionnaire.
  
3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Propriétés**.  
  
4. Dans la page **Propriétés**, choisissez l’onglet **Déboguer**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Assurez-vous que la zone de texte **Répertoire de travail** est vide.  
  
6. Choisissez **utiliser l’ordinateur distant**, puis tapez **MJO-DL : 4020** dans la zone de texte. (4020 est le numéro de port indiqué dans la fenêtre du débogueur distant).  
  
7. Vérifiez que l’option **Permettre le débogage du code natif** n’est pas sélectionnée.  
  
8. Créez le projet.  
  
9. Créez un dossier sur l’ordinateur distant qui est le même que celui du dossier de **débogage** sur votre ordinateur Visual Studio : ** \<source path> \MyWPF\MyWPF\bin\Debug**.  
  
10. Copiez le fichier exécutable que vous venez de créer à partir de votre ordinateur Visual Studio dans le dossier nouvellement créé sur l’ordinateur distant.
  
    > [!CAUTION]
    > N’apportez pas de modifications au code ou à la régénération (ou vous devez répéter cette étape). Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

    Vous pouvez copier le projet manuellement, utiliser xcopy, Robocopy, PowerShell ou d’autres options.
  
11. Assurez-vous que le débogueur distant est en cours d’exécution sur l’ordinateur cible. (Si ce n’est pas le cas, recherchez le **débogueur distant** dans le menu **Démarrer** . ) La fenêtre du débogueur distant ressemble à ce qui suit.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Dans Visual Studio, démarrez le débogage (**Déboguer/démarrer le débogage**, ou **F5**).  
  
13. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à la machine distante.  
  
     Les informations d’identification requises varient en fonction de la configuration de sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez entrer votre nom de domaine et votre mot de passe. Sur un ordinateur qui n’est pas un domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong> , ainsi que le mot de passe correct.

     La fenêtre principale de l’application WPF doit être ouverte sur l’ordinateur distant.
  
14. Si nécessaire, prenez des mesures pour atteindre le point d’arrêt. Il doit être actif. Sinon, cela signifie que les symboles de l’application n’ont pas été chargés. Réessayez et, si cela ne fonctionne pas, récupérez des informations sur le chargement des symboles et comment les résoudre pour les résoudre lors de la [Présentation des fichiers de symboles et des paramètres de symbole de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.
  
    Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans le **Explorateur de solutions**, cliquez sur **Ajouter/nouveau dossier**.) Ajoutez ensuite les fichiers au dossier (dans le **Explorateur de solutions**, cliquez sur **Ajouter/élément existant**, puis sélectionnez les fichiers.). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants  
 Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux.  Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  
  
 À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Pour plus d’informations, consultez l’aide sur le débogage distant (appuyez sur **F1** dans la fenêtre du débogueur distant ou cliquez sur **aide/utilisation**). D’autres informations sont disponibles dans [Modification du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Débogage à distance sur le Windows Store et les applications Azure  
 Pour plus d’informations sur le débogage à distance avec les applications du Windows Store, consultez [Déboguer et tester des applications du Windows Store sur un appareil distant à partir de Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Pour plus d’informations sur le débogage sur Azure, consultez une des rubriques suivantes :  
  
- [Débogage d’un service cloud ou d’une machine virtuelle dans Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Débogage du serveur principal .NET dans Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Présentation du débogage à distance sur les sites Web Azure ([partie 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [partie 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [partie 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)   
 [Débogage distant ASP.NET sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
