---
title: Débogage à distance ASP.NET sur un ordinateur IIS 7,5 distant | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839730"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Débogage distant ASP.NET sur un ordinateur IIS distant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez déployer une application Web ASP.NET sur un ordinateur Windows Server avec IIS et la configurer pour le débogage distant. Ce guide explique comment installer et configurer une application Visual Studio 2015 MVC 4.5.2, la déployer sur IIS et attacher le débogueur distant à partir de Visual Studio.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 10
* Windows Server 2008 R2 et IIS 7,5

La plupart des informations contenues dans cet article s’appliquent également au débogage à distance d’une application ASP.NET Core, sauf que le déploiement d’applications ASP.NET Core est différent et nécessite des étapes supplémentaires. Pour déployer une application ASP.NET Core sur IIS, vous devez suivre toutes les sections de [cet article](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Conditions préalables : installer le débogueur distant sur l’ordinateur Windows Server

Pour obtenir des instructions sur le téléchargement du débogueur distant sur l’ordinateur Windows Server, consultez [débogage distant](../debugger/remote-debugging.md).

Pour effectuer un débogage distant d’applications ASP.NET, vous pouvez exécuter l’application du débogueur distant en tant qu’administrateur ou démarrer le débogueur distant en tant que service. Pour plus d’informations l’exécution du débogueur distant en tant que service, consultez [Remote Debugging](../debugger/remote-debugging.md).

Une fois installé, assurez-vous que le débogueur distant est en cours d’exécution sur l’ordinateur cible. (Si ce n’est pas le cas, recherchez le **débogueur distant** dans le menu **Démarrer** . ) La fenêtre du débogueur distant ressemble à ce qui suit. (4020 est le numéro de port par défaut)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Créer l’application sur l’ordinateur Visual Studio  
  
1. Créez une application ASP.NET MVC. (**Fichier / Nouveau / Projet**, puis sélectionnez **Visual C# / Web / Application web ASP.NET** . Dans la section des modèles **ASP.NET 4.5.2** , sélectionnez **MVC**. Assurez-vous que l’option **hôte dans le Cloud** n’est pas sélectionnée dans la section Azure. Nommez le projet **MyMVC**.)
1. Ouvrez le fichier HomeController.cs et définissez un point d’arrêt dans la méthode `About()` .
1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet et sélectionnez **Publier**.
1. Pour **Sélectionner une cible de publication**, sélectionnez **Personnalisée** et nommez le profil **MyMVC**. Cliquez sur **Suivant**.
1. Sous l’onglet **Connexion** , définissez le champ **Méthode de publication** sur **Système de fichiers** et le champ **Emplacement cible** sur un répertoire local. Cliquez sur **Suivant**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Définissez la configuration en **Debug**. Cliquez sur **Publier**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    L’application doit être publiée dans le répertoire local.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Déployer l’application ASP.NET sur l’ordinateur distant Windows Server

 Cette section suppose que IIS est déjà activé sur l’ordinateur Windows Server. Sur Windows Server 2012 R2, consultez [configuration IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) pour activer IIS. (Vous pouvez ignorer les autres sections de cet article, sauf si vous essayez de déployer une application ASP.NET Core. Pour ASP.NET Core, suivez les étapes de l’article pour déployer l’application à la place des étapes décrites ici.
1. Installer ASP.NET utilisez les composants Web Platform pour installer ASP.NET 4,5 (à partir du nœud du serveur dans Windows Server 2012 R2, choisissez **obtenir de nouveaux composants de la plateforme Web** , puis recherchez ASP.net)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Sur Windows Server 2008 R2, installez ASP.NET 4 à la place à l’aide de la commande suivante :   **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-IR**
1. Copiez le répertoire de projet ASP.NET de l’ordinateur Visual Studio dans un répertoire local (que nous appelons **C:\Publish**) sur l’ordinateur Windows Server. Vous pouvez copier le projet manuellement, utiliser xcopy, Web Deploy, Robocopy, PowerShell ou d’autres options.

    > [!CAUTION]
    > Si vous devez apporter des modifications au code ou à la régénération, vous devez republier et répéter cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.
1. Assurez-vous que le fichier web.config indique la version correcte du .NET Framework.  Par exemple, la version de .NET Framework installée par défaut sur Windows Server 2008 R2 est 4.0.30319, mais nous avons créé une version de ASP.NET 4.5.2. Si une application ASP.NET 4,0 est en cours d’exécution sur l’ordinateur Windows Server, vous devez modifier la version :
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.
1. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.
1. Définissez le champ **alias** sur **MyMVC** et le champ pool d’applications sur **ASP.NET v 4.0** (ASP.net 4,5 n’est pas une option pour le pool d’applications). Définissez le **Chemin d’accès physique** sur **C:\Publish** (où vous avez copié le répertoire de projet ASP.NET).

    >[!NOTE] 
    > Pour les applications ASP.NET Core, définissez le champ pool d’applications sur **aucun code managé**.
1. Pour tester le déploiement, cliquez avec le bouton droit sur **site Web par défaut** , puis sélectionnez **Parcourir**.
    Si vous avez correctement déployé l’application, vous verrez la page Web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution **MyMVC** .
1. Dans Visual Studio, cliquez sur **Déboguer/attacher au processus** (**CTRL + ALT + P**).
1. Définissez le champ Qualificateur sur ** \<remote computer name> : 4020**.
1. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez aucun processus, essayez d’utiliser l’adresse IP à la place du nom de l’ordinateur distant (le port est obligatoire). Utilisez `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.
1. Cochez  **Afficher les processus de tous les utilisateurs**.
1. Recherchez **w3wp.exe** et cliquez sur **Attacher**.

     Pour trouver rapidement le nom du processus, tapez la première lettre du processus.
     
    >[!NOTE]
    > Pour une application ASP.NET Core, choisissez le processus dnx.exe au lieu de w3wp.exe. (Ce nom de processus peut changer dans une version à venir.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http:// \<remote computer name> **.
    
    La page web ASP.NET doit s’afficher.
1. Dans la page Web ASP.NET, cliquez sur le lien vers la page **à propos** de.

    Le point d’arrêt doit être atteint dans Visual Studio.
