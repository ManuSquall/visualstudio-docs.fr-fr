---
title: Activer le débogage pour les Applications ASP.NET | Documents Microsoft
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 3418e1d2e05d687f8cb73a7857178ae1060d56f8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479388"
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Débogage d’Applications ASP.NET dans Visual Studio

Vous pouvez déboguer des applications ASP.NET à partir de Visual Studio.

## <a name="requirements"></a>Spécifications

Pour suivre les instructions fournies dans cette rubrique, vous devez :

- IIS Express, qui est inclus par défaut dans Visual Studio 2012 et versions ultérieures

    - ou -

- Local IIS web server (version 8.0 ou version ultérieure) est correctement configuré et peut exécuter l’application ASP.NET sans erreurs.

Si le serveur est distant, le débogueur distant doit être en cours d’exécution sur l’ordinateur distant. Pour déboguer sur un serveur IIS distant, consultez [ASP.NET de déboguer à distance sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Configurer les paramètres de débogage

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Activer le débogage ASP.NET dans les propriétés du projet

1. Ouvrez votre projet ASP.NET dans Visual Studio.

2. Cliquez sur le projet dans **l’Explorateur de solutions**, choisissez **propriétés**, puis cliquez sur le **Web** onglet.

    Pour certains types de projet, sélectionnez **Propriétés > déboguer** à la place. Pour un projet Web Forms ASP.NET, cliquez sur le projet et sélectionnez **Pages de propriétés > Options de démarrage**.
  
3.  Sous **Débogueurs**, cochez la case **ASP.NET** .

    ![Paramètres du débogueur](../debugger/media/dbg-aspnet-enable-debugging.png "paramètres du débogueur")

> [!NOTE]
> Si vous créez un nouveau projet ASP.NET (**fichier > Nouveau projet**), les paramètres de débogage sont déjà configurés correctement.

### <a name="enable-debugging-in-the-webconfig-file"></a>Activer le débogage dans le fichier web.config  

Pour déboguer une application web, au fichier web.config de l’application doit être configuré correctement. Un fichier web.config est requis si vous hébergez l’application sur IIS ou IIS Express.

Pour ASP.NET Core, le fichier web.config est créé automatiquement lorsque l’application est déployée (si elle n’est pas déjà présente).

> [!TIP]
> Votre processus de déploiement peut mettre à jour les paramètres web.config. Par conséquent, avant d’essayer de déboguer, vérifiez le paramètre web.config sur le serveur.
  
1.  Dans Visual Studio, ouvrez le fichier web.config du projet.  
  
    > [!NOTE]  
    > Vous ne pouvez pas accéder au fichier web.config à distance à l’aide d’un navigateur Web. Pour des raisons de sécurité, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] configure Microsoft IIS pour empêcher un navigateur accède directement aux fichiers Web.config. Si vous essayez d’accéder à un fichier de configuration à l’aide d’un navigateur, vous obtenez une erreur d’accès HTTP 403 (interdit).  
  
2.  Recherchez l’élément `configuration/system.web/compilation` . Si l’élément de compilation n’existe pas, créez-le.

    Le fichier web.config est un fichier XML qui contient des sections imbriquées marquées par des balises.
  
3.  Si l’élément `compilation` ne contient pas d’attribut `debug` , ajoutez cet attribut à l’élément.  
  
4.  Assurez-vous que l’attribut `debug` est défini sur `true`.  
  
Le fichier web.config doit ressembler à l’exemple suivant :

> [!NOTE]
> Cet exemple est un fichier web.config partielle. Les sections XML supplémentaires sont généralement présentes entre la configuration et les éléments system.web. L’élément de compilation peut également contenir des autres éléments et attributs.
  
#### <a name="example"></a>Exemple  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Si vous utilisez un serveur externe au lieu du serveur d’IIS Express par défaut, vous devez également vous assurer que le `targetFramework` valeur d’attribut correspond à la configuration sur le serveur.

> [!IMPORTANT]
> Pour de meilleures performances, définir une application de production `debug=false` et spécifiez une version Release lorsque vous générez et publiez l’application.

## <a name="configure-project-settings-for-the-server"></a>Configurer les paramètres de projet pour le serveur

Pour le débogage sur un serveur web local, définissez les propriétés du projet. Pour le débogage sur un serveur distant, suivez les instructions de plus complètes décrites dans [ASP.NET de débogage à distance sur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) à la place.

1. Dans le **Web** onglet du projet de propriétés, sélectionnez **IIS Express** ou **serveur externe** sous le **Server** paramètres. (Pour certains types de projet, ces paramètres s’affichent sous la **déboguer** onglet à la place.)

    ![Paramètres du serveur](../debugger/media/dbg-aspnet-server-settings.png "paramètres du serveur")

    IIS Express est le serveur par défaut pour ASP.NET et ne requiert généralement pas de configuration spéciale. Il s’agit de la façon la plus simple pour déboguer une application ASP.NET.

    Pour un projet Web Forms ASP.NET, cliquez sur le projet, choisissez **Pages de propriétés > Options de démarrage**, puis sélectionnez **utiliser le serveur Web par défaut** ou **utiliser le serveur personnalisé** () au lieu de **serveur externe**).

    ![Paramètres du serveur pour l’application de Web Forms](../debugger/media/dbg-aspnet-server-settings-webforms.png "paramètres du serveur pour l’application de Web Forms")

2. Si vous choisissez un serveur (personnalisé) externe, entrez l’URL correcte dans le **URL Project** (ou **une URL de Base**) champ.

    Si le serveur externe est local IIS, IIS doit être installé et configuré correctement. Par exemple, la version correcte d’ASP.NET doit être configurée dans IIS. Pour plus d’informations, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Si vous souhaitez tester le déploiement, ainsi que le débogage, consultez [déploiement pour tester](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Si le serveur externe est [distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), attacher au processus à la place, et ces paramètres de projet ne sont pas utilisés pour le débogage.

## <a name="local-iis-web-server-configure-iis"></a>(Serveur web de serveur IIS local) Configurer IIS

Pour IIS Express, vous n’avez pas besoin de configurer le serveur web (ignorer cette section). IIS Express est recommandé pour les tests initiaux.

Si vous utilisez un serveur web IIS local, procédez comme suit.

1. Assurez-vous qu’IIS est installé correctement. Pour plus d’informations, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Assurez-vous que vous installez la version correcte d’ASP.NET sur le serveur. Web Platform Installer (WebPI) permet d’installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET). Pour installer ASP.NET Core, consultez [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Ouvrez le **Internet Information Services (IIS) Manager**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

5. Définir le **Alias** au champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez la **chemin d’accès physique** à  **C:\inetpub\myNewFolder** (créer un nouveau dossier pour l’application).

6. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et définissez le champ pool d’applications à la valeur correcte pour votre application (à utiliser ASP.NET 4 pour ASP.NET 4.5. Utilisez **aucun Code managé** pour ASP.NET Core).

## <a name="local-iis-web-server-deploy-the-app"></a>(Serveur web de serveur IIS local) Déployer l’application

Pour IIS Express, l’application web est déployée automatiquement lorsque vous démarrez le débogage (ignorer cette section).

Si vous utilisez un serveur web IIS local, procédez comme suit. Il existe différentes manières de publier votre application à IIS. Dans ces étapes, nous montrons comment créer et utiliser un profil de publication afin que vous puissiez déployer à l’aide du système de fichiers.

1. Redémarrez Visual Studio en tant qu’administrateur.

    Pour déployer à l’aide de cette méthode, vous avez besoin des privilèges d’administrateur.

2. Dans Visual Studio, cliquez sur le projet et choisissez **publier** (pour Web Forms, utilisez **publier l’application Web**).

3. Choisissez **IIS, FTP, etc.** et cliquez sur **publier**.

    ![Publier sur IIS](../debugger/media/dbg-aspnet-local-iis.png "publier sur IIS")

    Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue Publier, entrez un nom de profil, puis choisissez **OK**.

4. Dans le **méthode de publication** champ, choisissez **système de fichiers**.

5. Pour le **emplacement cible**, cliquez sur le **Parcourir** bouton.

6. (ASP.NET Core) Choisissez **système de fichiers** et sélectionnez le dossier où vous avez créé précédemment pour l’application.

6. (ASP.NET) Choisissez **IIS Local**, puis sélectionnez le site web, vous avez créé précédemment, puis cliquez sur **ouvrir**.

    ![Publier sur IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "publier sur IIS")

    > [!TIP]
    > Si vous voyez un message indiquant que le serveur web n’est pas configuré correctement, assurez-vous que la version correcte d’ASP.NET est installée pour IIS.

7. Cliquez sur **suivant** et choisissez une **déboguer** configuration.

    > [!NOTE]
    > Si vous déployez avec une configuration Release, cela définit `debug=false` dans le fichier du serveur web.config.

8. Cliquez sur **enregistrer** pour enregistrer les paramètres de publication, puis cliquez sur **publier**.

    > [!CAUTION]
    >  Si vous devez apporter des modifications à du code ou la régénération, vous devez republier et répétez cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

## <a name="set-a-breakpoint-and-start-debugging"></a>Définir un point d’arrêt et démarrer le débogage

1. Dans votre projet dans Visual Studio, ensemble un point d’arrêt sur du code qui s’exécutera.

2. Pour démarrer le débogage, appuyez sur **F5** (**Déboguer > Démarrer le débogage**).

3. Effectuez les actions à exécuter le code qui contient le point d’arrêt.

    Les temps de pause débogueur où vous avez défini le point d’arrêt.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(Serveur IIS local) Résolution des problèmes : Ne peut pas atteint le point d’arrêt

1. Démarrer l’application web d’IIS et assurez-vous qu’il fonctionne correctement. Laissez l’application web en cours d’exécution.

2. Dans Visual Studio, sélectionnez **Déboguer > Attacher au processus** et se connecter au processus ASP.NET (généralement **w3wp.exe** ou **dotnet.exe**). Pour plus d’informations, consultez [attacher au processus](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Si vous êtes en mesure de se connecter à l’aide de **attacher au processus** et pouvez atteindre un point d’arrêt, mais ne peut pas démarrer le débogage à l’aide de **F5**, il est probable qu’un paramètre est incorrect dans les propriétés du projet. Si vous utilisez un fichier HOSTS, vérifiez qu’il est correctement configuré.

  
## <a name="robust-programming"></a>Programmation fiable  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] détecte les modifications apportées aux fichiers Web.config et applique les nouveaux paramètres de configuration automatiquement. Vous n’avez pas à redémarrer l’ordinateur ni à redémarrer le serveur IIS pour que les modifications prennent effet.  
  
Un site web peut contenir plusieurs répertoires et sous-répertoires virtuels, et chacun d’eux peut contenir des fichiers web.config. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications héritent des paramètres des fichiers Web.config à des niveaux supérieurs dans le chemin d’accès d’URL. Fichiers de configuration hiérarchiques permettent de modifier les paramètres pour plusieurs [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications en même temps, par exemple, pour toutes les applications en dessous dans la hiérarchie. Toutefois, si `debug` est défini dans un fichier de niveau inférieur dans la hiérarchie, il substitue à la valeur la plus élevée.  
  
Par exemple, vous pouvez spécifier `debug="true"` dans www.microsoft.com/aaa/Web.config, ainsi que les applications dans le dossier aaa ou dans n’importe quel sous-dossier de aaa hérite de ce paramètre. Par conséquent, si votre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application se trouve dans www.microsoft.com/aaa/bbb, il hérite de ce paramètre, tout comme les [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications dans www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd et ainsi de suite. La seule exception concerne le cas où l’une de ces applications remplace le paramètre à l’aide de son propre fichier Web.config de niveau inférieur.  
  
> [!IMPORTANT]
> L’activation du mode de débogage considérablement affecte les performances de votre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application. Pensez à désactiver le mode débogage avant de déployer une application release ou de mesurer les performances.  
  
## <a name="see-also"></a>Voir aussi  
[Débogage ASP.NET : configuration requise](aspnet-debugging-system-requirements.md)   
[Comment : exécuter le processus de travail sous un compte d’utilisateur](how-to-run-the-worker-process-under-a-user-account.md)   
[Comment : rechercher le nom du processus ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Déboguer les applications Web déployées](debugging-deployed-web-applications.md)   
[Procédure pas à pas : Débogage d’un formulaire Web](walkthrough-debugging-a-web-form.md)   
[Comment : déboguer des exceptions ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Déboguer des applications web : erreurs et dépannage](debugging-web-applications-errors-and-troubleshooting.md)
  