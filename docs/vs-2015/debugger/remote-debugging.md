---
title: Débogage à distance | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61b1bc7f81ca4d6c3f313c543be23b746d56d37e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812892"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez déboguer une application Visual Studio qui a été déployée sur un autre ordinateur.  Pour ce faire, utilisez le débogueur distant Visual Studio.  
  
 Ces informations s’appliquent aux applications de bureau Windows et aux applications ASP.NET.  Pour plus d’informations sur le débogage des applications Windows Store à distance et des applications Azure, consultez [débogage à distance sur les applications Windows Store et Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Obtenir les outils à distance  
Vous pouvez télécharger les outils à distance directement sur l’appareil ou le serveur que vous souhaitez déboguer, ou vous peuvent obtenir les outils à distance à partir de votre ordinateur hôte avec Visual Studio est installé.

### <a name="to-download-and-install-the-remote-tools"></a>Pour télécharger et installer les outils à distance
  
1.  Sur l’appareil ou serveur machine que vous souhaitez déboguer (plutôt que l’ordinateur qui exécute Visual Studio), obtenir la version des outils à distance.

    |Version|Lien|Notes|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, rejoindre le groupe de Visual Studio Dev Essentials gratuit, ou vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Puis ouvrez à nouveau le lien si nécessaire. Toujours télécharger la version correspondant à votre système d’exploitation (x 86, x64 ou ARM version)|
    |Visual Studio 2015 (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, rejoindre le groupe de Visual Studio Dev Essentials gratuit, ou vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Puis ouvrez à nouveau le lien si nécessaire.|
    |Visual Studio 2013|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2013|
    |Visual Studio 2012|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2012|
  
2.  Sur la page de téléchargement, choisissez la version des outils qui correspond à votre système d’exploitation (x 86, x64 ou ARM version) et téléchargez les outils à distance.
  
    > [!IMPORTANT]
    >  Nous vous recommandons de qu'installer la version la plus récente des outils à distance qui correspond à votre version de Visual Studio. Versions incompatibles ne sont pas recommandées.  
    >   
    >  En outre, vous devez installer les outils à distance qui ont la même architecture que le système d’exploitation sur lequel vous souhaitez l’installer. En d’autres termes, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation de 64 bits, vous devez installer la version 64 bits des outils à distance sur l’ordinateur distant.  
  
3.  Une fois que vous avez terminé de télécharger le fichier exécutable, suivez les instructions pour installer l’application sur l’ordinateur distant. Consultez [instructions d’installation](#bkmk_setup)

Si vous tentez de copier le débogueur distant (msvsmon.exe) sur l’ordinateur distant et l’exécuter, n’oubliez pas que le **Assistant Configuration Remote Debugger** (**rdbgwiz.exe**) est installé uniquement lorsque vous téléchargez le outils et vous devrez peut-être utiliser l’Assistant pour la configuration ultérieurement, en particulier si vous souhaitez que le débogueur distant s’exécute en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](#bkmk_configureService) ci-dessous.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Pour exécuter le débogueur distant à partir d’un partage de fichiers

Vous pouvez trouver le débogueur distant (**msvsmon.exe**) sur un ordinateur avec Visual Studio 2015 Community, Professional ou Enterprise déjà installé. Pour de nombreux scénarios, le plus simple à configurer le débogage à distance consiste à exécuter le débogueur distant (msvsmon.exe) à partir d’un partage de fichiers. Pour les restrictions d’utilisation, consultez la page d’aide du débogueur distant (**aide / utilisation** dans le débogueur distant).

1. Rechercher **msvsmon.exe** dans le répertoire correspondant à votre version de Visual Studio. Pour Visual Studio 2015 :

      **Programme Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programme Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Partage le **débogueur distant** dossier sur l’ordinateur Visual Studio.

3. Sur l’ordinateur distant, exécutez **msvsmon.exe**. Suivez le [instructions d’installation](#bkmk_setup).

> [!TIP] 
> Pour l’installation de ligne de commande et référence de ligne de commande, consultez la page d’aide **msvsmon.exe** en tapant ``msvsmon.exe /?`` dans la ligne de commande sur l’ordinateur avec Visual Studio est installé (ou accédez à **aide / utilisation**dans le débogueur distant).

  
## <a name="supported-operating-systems"></a>Supported Operating Systems  
 L’ordinateur distant doit exécuter l’un des systèmes d’exploitation suivants :  
  
-   Windows 10  
  
-   Windows 8 ou 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 ou Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configurations matérielles prises en charge  
  
-   Processeur 1,6 GHz minimum  
  
-   1 Go de RAM (1,5 Go s’il s’agit d’une machine virtuelle)  
  
-   1 Go d’espace disque disponible  
  
-   Disque dur 5400 tr/min  
  
-   Carte vidéo DirectX 9 s’exécutant avec une résolution d’affichage de 1024 x 768 ou supérieure  
  
## <a name="network-configuration"></a>Configuration réseau  
 L’ordinateur distant et l’ordinateur Visual Studio doivent être connectés sur un réseau, un groupe de travail, un groupe résidentiel ou directement connectés à l’aide d’un câble Ethernet. Le débogage sur Internet n’est pas pris en charge.  
  
## <a name="bkmk_setup"></a>Configurer le débogueur distant  
 Vous devez disposer des autorisations d’administration sur l’ordinateur distant  
  
1. Recherchez l’application du débogueur distant. (Ouvrez le menu Démarrer et recherchez **débogueur distant**.)
  
    Si vous exécutez le débogueur distant sur un serveur distant, vous pouvez avec le bouton droit de l’application débogueur distant et choisissez **exécuter en tant qu’administrateur** (ou, vous pouvez exécuter le débogueur distant en tant que service). Si vous n’exécutez pas sur un serveur distant, seulement le démarrer normalement.
  
2. Lorsque vous démarrez les outils à distance pour la première fois (ou avant que vous l’avez configuré), le **Configuration du débogage distant** boîte de dialogue s’affiche.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Si l’API de Service Windows n’est pas installé (ce qui se produit uniquement sur Windows Server 2008 R2), choisissez le **installer** bouton.  
  
4. Sélectionnez les types de réseau sur lesquels vous voulez utiliser les outils de contrôle à distance. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément, selon les besoins.  
  
5. Choisissez **configurer le débogage distant** pour configurer le pare-feu et démarrer l’outil.  
  
6. Une fois la configuration terminée, la fenêtre du débogueur distant s’affiche.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Le débogueur distant est maintenant en attente pour une connexion. Prenez note du nom du serveur et le port numéro qui s’affiche, car vous en aurez besoin ultérieurement pour la configuration dans Visual Studio.  
  
   Lorsque vous avez terminé le débogage et vous devez arrêter le débogueur distant, cliquez sur **fichier / quitter** dans la fenêtre. Vous pouvez le redémarrer à partir de la **Démarrer** menu ou à partir de la ligne de commande :  
  
   **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Remote Debugger\\< x86, x64 ou Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurer le débogueur distant  
 Vous pouvez modifier certains aspects de la configuration du débogueur distant après l’avoir démarré pour la première fois.
  
- Pour activer les autres utilisateurs de se connecter au débogueur distant, choisissez **outils / autorisations**. Vous devez disposer de privilèges d’administrateur pour accorder ou refuser des autorisations.

  > [!IMPORTANT]
  > Vous pouvez exécuter le débogueur distant sous un compte d’utilisateur différent à partir du compte d’utilisateur que vous utilisez sur l’ordinateur Visual Studio, mais vous devez ajouter le compte d’utilisateur différent pour les autorisations du débogueur distant. 

   Vous pouvez également démarrer le débogueur distant à partir de la ligne de commande avec le **/ allow \<nom d’utilisateur >** paramètre : **msvsmon /Allow \< username@computer>**.
  
- Pour modifier le mode d’authentification ou le numéro de port, ou pour spécifier une valeur de délai d’expiration pour les outils à distance : choisissez **Outils / Options**.  
  
   Pour obtenir la liste des numéros de port utilisés par défaut, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  >  Vous pouvez choisir d’exécuter les outils de contrôle à distance en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n’existe aucune sécurité du réseau lorsque vous lancez l’exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n’est pas exposé à des failles de sécurité liées à des programmes malveillants ou du trafic dangereux.

##  <a name="bkmk_configureService"></a> (Facultatif) Configurer le débogueur distant en tant que service
 Pour déboguer dans ASP.NET et d’autres environnements de serveur, vous devez exécuter le débogueur distant en tant qu’administrateur ou, si vous souhaitez qu’il est toujours en cours d’exécution, exécutez le débogueur distant en tant que service.
  
 Si vous souhaitez configurer le débogueur distant en tant que service, procédez comme suit.  
  
1. Recherchez l’ **Assistant Configuration Remote Debugger** (rdbgwiz.exe). (C’est une application distincte du débogueur distant). Il est disponible uniquement quand vous installez les outils de contrôle à distance. Il n’est pas installé avec Visual Studio.  
  
2. Démarrez l’Assistant Configuration. Quand la première page s’affiche, cliquez sur **Suivant**.  
  
3. Cochez la case **Exécuter le débogueur distant Visual Studio 2015 en tant que service** .  
  
4. Ajoutez le nom du compte d’utilisateur et le mot de passe.  
  
    Vous devez peut-être ajouter le droit utilisateur **Ouvrir une session en tant que service** pour ce compte. (Recherchez **Stratégie de sécurité locale** (secpol.msc) dans la page ou la fenêtre **Démarrer** (ou tapez **secpol.msc** à l’invite de commande). Quand la fenêtre s’affiche, double-cliquez sur **Attribution des droits utilisateur**, puis recherchez **Ouvrir une session en tant que service** dans le volet droit. Double-cliquez dessus. Ajouter le compte d’utilisateur pour le **propriétés** fenêtre et cliquez sur **OK**.) Cliquez sur **suivant**.  
  
5. Sélectionnez le type de réseau avec lesquel vous voulez que les outils de contrôle à distance communiquent. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément. Cliquez sur **Suivant**.  
  
6. Si le service peut être démarré, le message suivant s’affiche : **L’Assistant Configuration Visual Studio Remote Debugger est terminé**. Si le service ne peut pas être démarré, le message suivant s’affiche : **Échec de l’Assistant Configuration Débogueur distant Visual Studio**. La page fournit également des conseils à suivre pour faire démarrer le service.  
  
7. Cliquez sur **Terminer**.  
  
   À ce stade, le débogueur distant s’exécute en tant que service. Vous pouvez le vérifier en accédant à **Panneau de configuration / Services** et en recherchant **Débogueur distant Visual Studio 2015**.  
  
   Vous pouvez arrêter et démarrer le service du débogueur distant à partir de **Panneau de configuration / Services**.  

## <a name="remote-debug-an-aspnet-application"></a>Déboguer à distance une application ASP.NET  
 Le déploiement d’une application ASP.NET sur un ordinateur distant qui exécute IIS implique différentes étapes, selon le système d’exploitation et la version d’IIS. Pour les ordinateurs distants exécutant Windows Server 2008 ou Windows Server 2012 et IIS 7.5 ou ultérieure, consultez [Remote Debugging ASP.NET sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Si vous déboguez une application ASP.NET Core, consultez [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html). Différentes étapes nécessaires à la publication d’un cœur d’ASP.NET sur IIS. Une fois que vous publiez une application ASP.NET Core avec succès, vous pouvez accéder à distance déboguer [tout comme les autres applications ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), sauf que le processus que vous devez joindre à est dnx.exe au lieu de w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Débogage distant d’un projet Visual C++  
 Dans la procédure suivante, le nom et le chemin d’accès du projet est C:\remotetemp\MyMfc, et le nom de l’ordinateur distant est **MJO-DL**.  
  
1. Créer une application MFC nommée **mymfc.**  
  
2. Définissez un point d’arrêt quelque part dans l’application qui est facilement accessible, par exemple dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.  
  
3. Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**. Ouvrez le **débogage** onglet.  
  
4. Définir le **débogueur à lancer** à **débogueur Windows distant**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Appliquez les modifications suivantes aux propriétés :  
  
   |Paramètre|Value|
   |-|-|  
   |Commande distante|C:\remotetemp\mymfc.exe|  
   |Répertoire de travail|C:\remotetemp|  
   |Nom de serveur distant|DL-MJO :*numéro_port*|  
   |Connexion|À distance avec authentification Windows|  
   |Type de débogueur|Natif uniquement|  
   |Répertoire de déploiement|C:\remotetemp.|  
   |Fichiers supplémentaires à déployer|C:\data\mymfcdata.txt.|  
  
    Si vous déployez des fichiers supplémentaires (facultatifs), le dossier doit exister sur les deux ordinateurs.  
  
6. Dans l’Explorateur de solutions, cliquez sur la solution et choisissez **Configuration Manager**.  
  
7. Pour le **déboguer** configuration, sélectionnez le **déployer** case à cocher.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Démarrer le débogage (**déboguer / démarrer le débogage**, ou **F5**).  
  
9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.  
  
10. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à l’ordinateur distant.  
  
     Les informations d’identification requises sont spécifiques à la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pourrez choisir un certificat de sécurité ou entrez votre nom de domaine et le mot de passe. Sur un ordinateur n’appartenant pas au domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong>, ainsi que le mot de passe correct.  
  
11. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.  
  
    > [!TIP]
    >  Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans le **l’Explorateur de solutions,** avec le bouton droit le **mymfc** nœud, puis choisissez **déployer**.  
  
    Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans le **l’Explorateur de solutions**, cliquez sur **Ajouter / nouveau dossier**.) Puis ajoutez les fichiers dans le dossier (dans le **l’Explorateur de solutions**, cliquez sur **Ajouter / existant élément**, puis sélectionnez les fichiers.). Sur le **propriétés** pour chaque fichier, définissez **Copy to Output Directory** à **toujours copier**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Débogage distant d’un projet Visual C# ou Visual Basic  
 Le débogueur ne peut pas déployer d’applications de bureau Visual C# ou Visual Basic sur un ordinateur distant, mais vous pouvez toujours les déboguer à distance comme suit. La procédure suivante suppose que vous souhaitez déboguer sur un ordinateur nommé **MJO-DL**, comme illustré dans l’illustration précédente.
  
1. Créez un projet WPF nommé **MyWpf**.  
  
2. Définissez un point d’arrêt facilement accessible quelque part dans le code.  
  
    Par exemple, vous pouvez définir un point d’arrêt dans un gestionnaire de boutons. Pour ce faire, ouvrez MainWindow.xaml et ajouter un contrôle de bouton à partir de la boîte à outils, puis double-cliquez sur le bouton pour ouvrir son gestionnaire.
  
3. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **propriétés**.  
  
4. Sur le **propriétés** page, choisissez le **déboguer** onglet.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Assurez-vous que le **répertoire de travail** zone de texte est vide.  
  
6. Choisissez **utiliser l’ordinateur distant**et le type **MJO-DL:4020** dans la zone de texte. (4020 est le numéro de port indiqué dans la fenêtre du débogueur distant).  
  
7. Assurez-vous que l’option **activer le débogage du code natif** n’est pas sélectionnée.  
  
8. Générez le projet.  
  
9. Créez un dossier sur l’ordinateur distant qui est le même chemin que le **déboguer** dossier sur votre ordinateur Visual Studio :  **\<chemin_source > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copiez le fichier exécutable que vous venez de créer à partir de votre ordinateur Visual Studio dans le dossier nouvellement créé sur l’ordinateur distant.
  
    > [!CAUTION]
    >  Ne pas modifier le code ou la reconstruction (ou vous devez répéter cette étape). Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

    Vous pouvez copier le projet manuellement, utilisez Xcopy, Robocopy, Powershell ou autres options.
  
11. Assurez-vous que le débogueur distant est en cours d’exécution sur l’ordinateur cible. (Si elle n’est pas le cas, recherchez **débogueur distant** dans le **Démarrer** menu. ) De la fenêtre du débogueur distant se présente comme suit.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Dans Visual Studio, démarrez le débogage (**déboguer / démarrer le débogage**, ou **F5**).  
  
13. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à l’ordinateur distant.  
  
     Les informations d’identification requises varient selon la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez entrer votre nom de domaine et le mot de passe. Sur un ordinateur n’appartenant pas au domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong>, ainsi que le mot de passe correct.

     La fenêtre principale de l’application WPF doit être ouverte sur l’ordinateur distant.
  
14. Si nécessaire, prendre des mesures pour atteindre le point d’arrêt. Il doit être actif. Sinon, cela signifie que les symboles de l’application n’ont pas été chargés. Nouvelle tentative et si cela ne fonctionne pas, obtenir des informations sur le chargement de symboles et comment les résoudre à [paramètres des symboles de présentation des fichiers de symboles et de Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.
  
    Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans le **l’Explorateur de solutions**, cliquez sur **Ajouter / nouveau dossier**.) Puis ajoutez les fichiers dans le dossier (dans le **l’Explorateur de solutions**, cliquez sur **Ajouter / existant élément**, puis sélectionnez les fichiers.). Sur le **propriétés** pour chaque fichier, définissez **Copy to Output Directory** à **toujours copier**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants  
 Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux.  Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  
  
 À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Pour plus d’informations, consultez l’aide du débogage distant (appuyez sur **F1** dans la fenêtre du débogueur distant, ou cliquez sur **aide / utilisation**). Vous trouverez plus d’informations sur [modifications symboles distants .NET le chargement dans Visual Studio 2012 et 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Débogage à distance sur les applications Windows Store et Azure  
 Pour plus d’informations sur le débogage distant avec les applications du Windows Store, consultez [déboguer et tester des applications du Windows Store sur un appareil distant à partir de Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Pour plus d’informations sur le débogage sur Azure, consultez une des rubriques suivantes :  
  
-   [Débogage d’un Service Cloud ou une Machine virtuelle dans Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Débogage du serveur principal .NET dans Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Introduction au débogage à distance sur Sites Web Azure ([partie 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [partie 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [partie 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)



