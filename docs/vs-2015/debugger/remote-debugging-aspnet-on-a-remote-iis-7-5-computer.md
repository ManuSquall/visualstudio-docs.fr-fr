---
title: Débogage distant ASP.NET sur un ordinateur distant IIS 7.5 ordinateur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d249571830ac608bef12c4a47d0243de1859a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764068"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Débogage distant ASP.NET sur un ordinateur distant IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez déployer une application Web ASP.NET sur un ordinateur Windows Server avec IIS et le configurer pour le débogage distant. Ce guide explique comment paramétrer et configurer une application Visual Studio 2015 MVC 4.5.2, déployez-le sur IIS et attacher le débogueur distant à partir de Visual Studio.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 10
* Windows Server 2008 R2 et IIS 7.5

La plupart des informations dans cet article s’applique également au débogage à distance une application ASP.NET Core, à ceci près que le déploiement d’applications ASP.NET core est différent et nécessite des étapes supplémentaires. Pour déployer une application ASP.NET Core sur IIS, vous devez effectuer toutes les sections de [cet article](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Conditions préalables : installer le débogueur distant sur l’ordinateur Windows Server

Pour obtenir des instructions sur la façon de télécharger le débogueur distant sur l’ordinateur Windows Server, consultez [le débogage à distance](../debugger/remote-debugging.md).

Pour effectuer un débogage distant des applications ASP.NET, vous pouvez exécuter l’application débogueur distant en tant qu’administrateur ou démarrer le débogueur distant en tant que service. Pour plus d’informations l’exécution du débogueur distant en tant que service, consultez [Remote Debugging](../debugger/remote-debugging.md).

Une fois qu’il est installé, assurez-vous que le débogueur distant est en cours d’exécution sur l’ordinateur cible. (Si elle n’est pas le cas, recherchez **débogueur distant** dans le **Démarrer** menu. ) De la fenêtre du débogueur distant se présente comme suit. (4020 est le numéro de port par défaut)

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

## <a name="BKMK_deploy_asp_net"></a> Déployer l’application ASP.NET sur l’ordinateur distant de Windows Server

 Cette section suppose que l’ordinateur Windows Server IIS est déjà activé. Sur Windows Server 2012 R2, consultez [Configuration IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) pour activer IIS. (Vous pouvez ignorer autres sections de cet article, sauf si vous essayez de déployer une application ASP.NET Core. Pour ASP.NET Core, suivez les étapes de l’article pour déployer l’application au lieu de la procédure décrite ici.)
1. Installer ASP.NET utiliser les composants de plate-forme Web pour installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Sur Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande : **\v4.0.30319\aspnet_regiis.exe C:\Windows\Microsoft.NET\Framework (64) - ir**
1. Copiez le répertoire de projet ASP.NET de l’ordinateur Visual Studio dans un répertoire local (que nous appelons **C:\Publish**) sur l’ordinateur Windows Server. Vous pouvez copier le projet manuellement, utilisez Xcopy, Web Deploy, Robocopy, Powershell ou autres options.

    > [!CAUTION]
    >  Si vous avez besoin apporter des modifications au code ou de la reconstruction, vous devez republier et répétez cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.
1. Assurez-vous que le fichier web.config indique la version correcte du .NET Framework.  Par exemple, la version de .NET Framework installée par défaut sur Windows Server 2008 R2 est 4.0.30319, mais nous avons créé un ASP.NET 4.5.2 version. Si une application ASP.NET 4.0 s’exécute sur l’ordinateur Windows Server, vous devez modifier la version :
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.
1. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.
1. Définir le **Alias** champ **MyMVC** et le champ pool d’applications à **ASP.NET v4.0** (ASP.NET 4.5 n’est pas une option pour le pool d’applications). Définissez le **Chemin d’accès physique** sur **C:\Publish** (où vous avez copié le répertoire de projet ASP.NET).

    >[!NOTE] 
    > Pour les applications ASP.NET Core, la valeur du champ de pool d’applications **aucun Code managé**.
1. Tester le déploiement en double-cliquant sur **Site Web par défaut** et sélectionnez **Parcourir**.
    Si vous avez déployé avec succès l’application, vous verrez la page web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution **MyMVC** .
1. Dans Visual Studio, cliquez sur **déboguer / attacher au processus** (**Ctrl + Alt + P**).
1. Définissez le champ qualificateur sur  **\<nom_ordinateur_distant > : 4020**.
1. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Utilisez `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.
1. Cochez  **Afficher les processus de tous les utilisateurs**.
1. Recherchez **w3wp.exe** et cliquez sur **Attacher**.

     Pour trouver rapidement le nom du processus, tapez la première lettre du processus.
     
    >[!NOTE]
    > Pour une application ASP.NET Core, choisissez le processus de dnx.exe au lieu de w3wp.exe. (Ce nom de processus peut changer dans une prochaine version.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant >**.
    
    La page web ASP.NET doit s’afficher.
1. Dans la page web ASP.NET, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.



