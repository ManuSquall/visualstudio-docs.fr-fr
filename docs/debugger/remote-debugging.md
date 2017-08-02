---
title: "D&#233;bogage distant | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.remote.overview"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "JScript"
  - "VB"
helpviewer_keywords: 
  - "débogage distant, programme d’installation"
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 76
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage distant
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déboguer une application Visual Studio qui a été déployée sur un autre ordinateur.  Pour ce faire, utilisez le débogueur distant Visual Studio.  
  
 Ces informations s’appliquent aux applications de bureau Windows et aux applications ASP.NET.  Pour plus d’informations sur le débogage distant des applications du Windows Store et des applications Azure, consultez [Débogage distant sur des applications Azure et du Windows Store](#bkmk_winstoreAzure).  
  
## Télécharger et installer les outils de contrôle à distance  
 Vous pouvez télécharger les outils de contrôle à distance pour le débogage à la page [Outils de contrôle à distance pour Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48155). Vous pouvez choisir les versions x86, x64 et ARM des outils. Une fois que vous avez terminé de télécharger le fichier exécutable, suivez les instructions pour installer l’application sur l’ordinateur distant.  
  
 Vous pouvez télécharger la version Update 1 des outils de contrôle à distance à la page [Outils de contrôle à distance pour Visual Studio 2015 Update 1](https://www.microsoft.com/en-us/download/details.aspx?id=49986&44F86079-8679-400C-BFF2-9CA5F2BCBDFC=1).  
  
> [!IMPORTANT]
>  Nous vous recommandons d’installer la version des outils de contrôle à distance qui correspond à la version de votre installation de Visual Studio. Les versions incompatibles ne sont pas prises en charge. En outre, vous devez installer les outils de contrôle à distance qui ont la même architecture que celle de l’application que vous souhaitez déboguer. En d’autres termes, si vous voulez déboguer une application 64 bits, vous devez installer la version 64 bits des outils de contrôle à distance.  
  
 Si l’ordinateur distant est déjà configuré avec Visual Studio 2015 édition Community, Professional ou Enterprise, le débogueur distant \(**msvsmon.exe**\) est déjà installé et vous pouvez le démarrer à partir de son répertoire :  
  
 **\<répertoire\_installation\_Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\(x64, x86, Appx\)\\msvsmon.exe**  
  
 Toutefois, l’**Assistant Configuration Remote Debugger** \(**rdbgwiz.exe**\) est installé uniquement quand vous téléchargez et installez les outils, et vous devrez peut\-être l’utiliser plus tard pour la configuration, en particulier si vous voulez que le débogueur distant s’exécute en tant que service. Pour plus d’informations, consultez [Configurer le débogueur distant en tant que service](#bkmk_configureService) ci\-dessous.  
  
## Systèmes d’exploitation pris en charge  
 L’ordinateur distant doit exécuter l’un des systèmes d’exploitation suivants :  
  
-   Windows 10  
  
-   Windows 8 ou 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 ou Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## Configurations matérielles prises en charge  
  
-   Processeur 1,6 GHz minimum  
  
-   1 Go de RAM \(1,5 Go s’il s’agit d’une machine virtuelle\)  
  
-   1 Go d’espace disque disponible  
  
-   Disque dur 5400 tr\/min  
  
-   Carte vidéo DirectX 9 s’exécutant avec une résolution d’affichage de 1024 x 768 ou supérieure  
  
## Configuration réseau  
 L’ordinateur distant et l’ordinateur Visual Studio doivent être connectés sur un réseau, un groupe de travail, un groupe résidentiel ou directement connectés à l’aide d’un câble Ethernet. Le débogage sur Internet n’est pas pris en charge.  
  
## Configurer le débogueur distant  
 Vous devez disposer des autorisations d’administration sur l’ordinateur distant  
  
1.  Recherchez l’application du débogueur distant. Vous pouvez rechercher **Débogueur distant** dans le menu **Démarrer** .  
  
2.  Quand vous démarrez les outils de contrôle à distance pour la première fois \(ou avant de les avoir configurés\), la boîte de dialogue **Configuration du débogage distant** s’affiche.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3.  Si l’API du service Windows n’est pas installée \(ce qui se produit uniquement sur Windows Server 2008 R2\), choisissez le bouton **Installer**.  
  
4.  Sélectionnez les types de réseau sur lesquels vous voulez utiliser les outils de contrôle à distance. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément, selon les besoins.  
  
5.  Sélectionnez **Configurer le débogage distant** pour configurer le pare\-feu et démarrer l’outil.  
  
6.  Une fois la configuration terminée, la fenêtre du débogueur distant s’affiche.  
  
     ![RemoteDebuggerWindow](~/debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
 Vous pouvez arrêter le débogueur distant en cliquant sur **Fichier \/ Quitter** dans la fenêtre. Vous pouvez le redémarrer à partir du menu **Démarrer** ou de la ligne de commande :  
  
 **\<répertoire\_installation\_Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\<x86, x64 ou Appx\\msvsmon.exe**.  
  
## Configurer le débogueur distant  
 Vous pouvez modifier certains aspects de la configuration du débogueur distant après l’avoir démarré pour la première fois.  
  
-   Pour que d’autres utilisateurs puissent se connecter au débogueur distant, choisissez **Outils \/ Autorisations**. Vous devez disposer de privilèges d’administrateur pour accorder ou refuser des autorisations.  
  
-   Pour modifier le mode Authentification ou le numéro de port, ou spécifier une valeur de délai d’attente pour les outils de contrôle à distance : sélectionnez Outils \/ Options.  
  
     Pour obtenir la liste des numéros de port utilisés par défaut, consultez [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md).  
  
> [!WARNING]
>  Vous pouvez choisir d’exécuter les outils de contrôle à distance en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n’existe aucune sécurité du réseau lorsque vous lancez l’exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n’est pas exposé à des failles de sécurité liées à des programmes malveillants ou du trafic dangereux.  
  
##  <a name="bkmk_configureService"></a> Configurer le débogueur distant en tant que service  
 Pour déboguer dans ASP.NET et d’autres environnements de serveur, vous devez exécuter le débogueur distant en tant que service.  
  
1.  Recherchez l’**Assistant Configuration Remote Debugger** \(rdbgwiz.exe\). \(C’est une application distincte du débogueur distant\). Il est disponible uniquement quand vous installez les outils de contrôle à distance. Il n’est pas installé avec Visual Studio.  
  
2.  Démarrez l’Assistant Configuration. Quand la première page s’affiche, cliquez sur **Suivant**.  
  
3.  Cochez la case **Exécuter le débogueur distant Visual Studio 2015 en tant que service**.  
  
4.  Ajoutez le nom du compte d’utilisateur et le mot de passe.  
  
     Vous devez peut\-être ajouter le droit utilisateur **Ouvrir une session en tant que service** pour ce compte. \(Recherchez **Stratégie de sécurité locale** \(secpol.msc\) dans la page ou la fenêtre **Démarrer** \(ou tapez **secpol.msc** à l’invite de commande\). Quand la fenêtre s’affiche, double\-cliquez sur **Attribution des droits utilisateur**, puis recherchez **Ouvrir une session en tant que service** dans le volet droit. Double\-cliquez dessus. Ajoutez le compte d’utilisateur dans la fenêtre **Propriétés** et cliquez sur **OK**.\) Cliquez sur **Suivant**.  
  
5.  Sélectionnez le type de réseau avec lesquel vous voulez que les outils de contrôle à distance communiquent. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément. Cliquez sur **Suivant**.  
  
6.  Si le service peut être démarré, le message suivant s’affiche : **L’Assistant Configuration Visual Studio Remote Debugger est terminé**. Si le service ne peut pas être démarré, le message suivant s’affiche : **Échec de l’Assistant Configuration Débogueur distant Visual Studio**. La page fournit également des conseils à suivre pour faire démarrer le service.  
  
7.  Cliquez sur **Terminer**.  
  
 À ce stade, le débogueur distant s’exécute en tant que service. Vous pouvez le vérifier en accédant à **Panneau de configuration \/ Services** et en recherchant **Débogueur distant Visual Studio 2015**.  
  
 Vous pouvez arrêter et démarrer le service du débogueur distant à partir de **Panneau de configuration \/ Services**.  
  
## Exécution du débogueur distant avec différents comptes d’utilisateur  
 Vous pouvez exécuter le débogueur distant sous un compte d’utilisateur différent de celui que vous utilisez sur l’ordinateur Visual Studio, mais vous devez ajouter l’autre compte d’utilisateur aux autorisations du débogueur distant.  
  
-   Vous pouvez démarrer le débogueur distant à partir de la ligne de commande avec le paramètre  **\/allow \<nom\_utilisateur\>** : **msvsmon \/allow \<nom\_utilisateur@ordinateur\>**.  
  
-   Vous pouvez ajouter l’utilisateur aux autorisations du débogueur distant \(dans la fenêtre du débogueur distant, **Outils \/ Autorisations**\).  
  
## Débogage distant d’un projet Visual C\+\+  
 Dans la procédure suivante, le nom ou chemin du projet est C:\\remotetemp\\MyMfc, et le nom de l’ordinateur distant est **remote1**.  
  
1.  Créez une application MFC nommée **mymfc.**  
  
2.  Définissez un point d’arrêt facilement accessible quelque part dans l’application, par exemple, dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.  
  
3.  Dans Visual Studio, dans le menu **Projet**, sélectionnez **Propriétés**. Ouvrez l’onglet **Débogage**.  
  
4.  Définissez **Débogueur à lancer** sur **Débogueur Windows distant**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Appliquez les modifications suivantes aux propriétés :  
  
    |||  
    |-|-|  
    |**Paramètre**|**Valeur**|  
    |Commande distante|C:\\remotetemp\\mymfc.exe|  
    |Répertoire de travail|C:\\remotetemp|  
    |Nom de serveur distant|remote1|  
    |Connexion|À distance avec authentification Windows|  
    |Type de débogueur|Natif uniquement|  
    |Répertoire de déploiement|C:\\remotetemp.|  
    |Fichiers supplémentaires à déployer|C:\\data\\mymfcdata.txt.|  
  
6.  Dans la barre d’outils, ouvrez le menu déroulant **Configuration de la solution**, puis choisissez **Gestionnaire de configurations**.  
  
7.  Pour la configuration **Debug**, cochez la case **Déployer**.  
  
     ![RemoteDebugCplusDeploy](~/debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Démarrez le débogage \(**Déboguer \/ Démarrer le débogage** ou appuyez sur **F5**.  
  
9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.  
  
10. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.  
  
    > [!TIP]
    >  Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **mymfc**, puis choisissez **Déployer**.  
  
 Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires \(dans l’**Explorateur de solutions**, cliquez sur **Ajouter \/ Nouveau dossier**.\) Ensuite, ajoutez les fichiers au dossier \(dans l’**Explorateur de solutions**, cliquez sur **Ajouter \/ Élément existant**, puis sélectionnez les fichiers.\). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.  
  
## Débogage distant d’un projet Visual C\# ou Visual Basic  
 Le débogueur ne peut pas déployer d’applications de bureau Visual C\# ou Visual Basic sur un ordinateur distant, mais vous pouvez toujours les déboguer à distance comme suit. La procédure suivante suppose que vous voulez les déboguer sur un ordinateur nommé **remote1**.  
  
1.  Créez un projet WPF nommé **MyWpf**.  
  
2.  Définissez un point d’arrêt facilement accessible quelque part dans le code. Par exemple, vous pouvez définir un point d’arrêt dans un gestionnaire de boutons.  
  
3.  Dans le menu **Projet**, choisissez **Propriétés**.  
  
4.  Dans la page **Propriétés**, choisissez l’onglet **Déboguer**.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Assurez\-vous que la zone de texte **Répertoire de travail** est vide.  
  
6.  Choisissez **Utiliser l’ordinateur distant** et tapez **remote1** dans la zone de texte.  
  
7.  Assurez\-vous que **Activer le débogage de code natif** n’est pas sélectionné.  
  
8.  Générez le projet.  
  
9. Créez un dossier sur l’ordinateur distant ayant le même chemin que le dossier **Debug** sur votre ordinateur Visual Studio : **\<chemin\_source\>\\MyWPF\\MyWPF\\bin\\Debug**.  
  
10. Copiez le fichier exécutable que vous venez de créer à partir de votre ordinateur Visual Studio dans le dossier nouvellement créé sur l’ordinateur distant.  
  
    > [!CAUTION]
    >  Ne modifiez pas le code et n’effectuez pas de régénération avant cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.  
  
11. Dans Visual Studio, démarrez le débogage \(**Déboguer \/ Démarrer le débogage** ou appuyez sur **F5**\).  
  
12. Vérifiez le point d’arrêt. Il doit être actif. Sinon, cela signifie que les symboles de l’application n’ont pas été chargés. Pour plus d’informations sur le chargement des symboles et comment résoudre les problèmes associés, consultez [Présentation des fichiers de symboles et des paramètres de symbole de Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).  
  
13. La fenêtre principale de l’application WPF doit être ouverte sur l’ordinateur distant. Effectuez l’action qui permet d’atteindre le point d’arrêt.  
  
14. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.  
  
 Si vous avez des fichiers autres que des fichiers de code qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires \(dans l’**Explorateur de solutions**, cliquez sur **Ajouter \/ Nouveau dossier**.\) Ensuite, ajoutez les fichiers au dossier \(dans l’**Explorateur de solutions**, cliquez sur **Ajouter \/ Élément existant**, puis sélectionnez les fichiers.\). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.  
  
## Déboguer à distance une application ASP.NET  
 Le déploiement d’une application ASP.NET sur un ordinateur distant qui exécute IIS implique différentes étapes, selon le système d’exploitation et la version d’IIS. Pour les ordinateurs distants exécutant les systèmes d’exploitation Windows 8 ou version ultérieure, ou Windows Server 2012 sur lesquels est installé IIS 8 \(ou version ultérieure\), consultez [Publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Pour les ordinateurs distants exécutant Windows 7 ou Windows Server 2008 sur lesquels IIS 7.5 est installé, consultez [Débogage distant ASP.NET sur un ordinateur distant IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
## Configurer le débogage avec des symboles distants  
 Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux. Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  
  
 À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Pour plus d’informations, consultez l’aide du débogage distant \(appuyez sur **F1** dans la fenêtre du débogueur distant, ou cliquez sur **Aide \/ Utilisation**\). D’autres informations sont disponibles dans [Modifications du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Débogage distant sur des applications Azure et du Windows Store  
 Pour plus d’informations sur le débogage distant d’applications du Windows Store, consultez [Déboguer et tester des applications du Windows Store sur un ordinateur distant à partir de Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Pour plus d’informations sur le débogage sur Azure, consultez une des rubriques suivantes :  
  
-   [Débogage d’un service cloud ou d’une machine virtuelle dans Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Débogage du serveur principal .NET dans Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Présentation du débogage distant sur Sites Web Azure \([Partie 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Partie 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Partie 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)\).  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurer le Pare\-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)   
 [Débogage distant ASP.NET sur un ordinateur distant IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)