---
title: Activer le débogage pour les applications ASP.NET | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: b87a8415bf2df2b8848b4fb619964d981e31ffcf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035248"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Déboguer des applications ASP.NET ou ASP.NET Core dans Visual Studio

Vous pouvez déboguer des applications ASP.NET et ASP.NET Core dans Visual Studio. Le processus diffère entre ASP.NET et ASP.NET Core, et si vous l’exécutez sur IIS Express ou d’un serveur IIS local. 

>[!NOTE]
>Les étapes et les paramètres suivants s’appliquent uniquement au débogage des applications sur un serveur local. Débogage des applications sur un serveur IIS à distance serveur utilise **attacher au processus**et ignore ces paramètres. Pour plus d’informations et pour obtenir des instructions pour les applications ASP.NET débogage à distance sur IIS, consultez [déboguer à distance ASP.NET sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou [ASP.NET Core de déboguer à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Le serveur intégré d’IIS Express est inclus avec Visual Studio. IIS Express est le serveur de débogage par défaut pour les projets ASP.NET et ASP.NET Core et est préconfiguré. Il est le moyen le plus simple pour déboguer et idéal pour le débogage et le test initial. 

Vous pouvez également déboguer une application ASP.NET ou ASP.NET Core sur un serveur IIS local (version 8.0 ou version ultérieure) qui est configurée pour exécuter l’application. Pour déboguer sur un serveur IIS local, vous devez remplir les conditions suivantes : 

<a name="iis"></a>
- Sélectionnez **IIS prend en charge des temps de développement** lors de l’installation de Visual Studio. (Si nécessaire, réexécutez le programme d’installation Visual Studio, sélectionnez **modifier**, puis ajoutez ce composant.)
- Exécuter Visual Studio en tant qu’administrateur. 
- Installer et configurer correctement IIS avec les versions appropriées de ASP.NET ou ASP.NET Core. Pour plus d’informations et pour obtenir des instructions, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou [héberger ASP.NET Core sur Windows avec IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Assurez-vous que l’application s’exécute sur IIS sans erreurs.

## <a name="debug-aspnet-apps"></a>Déboguer des applications ASP.NET 

IIS Express est la valeur par défaut et est préconfiguré. Si vous déboguez sur le serveur IIS Local, assurez-vous que vous avez respecté les [requise pour le débogage des IIS local](#iis). 

1. Sélectionnez le projet ASP.NET dans Visual Studio **l’Explorateur de solutions** et cliquez sur le **propriétés** icône, appuyez sur **Alt**+**entrée**, ou avec le bouton droit et choisissez **propriétés**.
   
1. Sélectionnez le **Web** onglet.
   
1. Dans le **propriétés** volet, sous **serveurs**, 
   - Pour IIS Express, sélectionnez **IIS Express** dans la liste déroulante.
   - Pour IIS local,
     1. Sélectionnez **IIS Local** dans la liste déroulante.
     1. À côté du **URL du projet** champ, sélectionnez **créer un répertoire virtuel**, si vous n’avez pas encore configuré l’application dans IIS.
   
1. Sous **débogueurs**, sélectionnez **ASP.NET**.
   
   ![Paramètres du débogueur ASP.NET](media/dbg-aspnet-enable-debugging2.png "paramètres du débogueur ASP.NET")
   
1. Utilisez **fichier** > **enregistrer les éléments sélectionnés** ou **Ctrl**+**S** enregistrer les modifications. 
   
1. Pour déboguer l’application, dans votre projet, définir des points d’arrêt sur du code. Dans la barre d’outils Visual Studio, assurez-vous que la configuration est définie sur **déboguer**, et le navigateur que vous souhaitez apparaît dans **IIS Express (\<nom du navigateur >)** ou **(serveurIISLocal\< Nom du navigateur >)** dans le champ de l’émulateur. 
   
1. Pour démarrer le débogage, sélectionnez **IIS Express (\<nom du navigateur >)** ou **IIS Local (\<nom du navigateur >)** dans la barre d’outils, sélectionnez **démarrer le débogage**à partir de la **déboguer** menu, ou appuyez sur **F5**. Le débogueur s’arrête sur les points d’arrêt. Si le débogueur ne peut pas atteindre les points d’arrêt, consultez [résolution des problèmes de débogage](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Déboguer des applications ASP.NET Core 

IIS Express est la valeur par défaut et est préconfiguré. Si vous déboguez sur le serveur IIS Local, assurez-vous que vous avez respecté les [requise pour le débogage des IIS local](#iis). 

1. Sélectionnez le projet ASP.NET Core dans Visual Studio **l’Explorateur de solutions** et cliquez sur le **propriétés** icône, appuyez sur **Alt**+**entrée**, ou avec le bouton droit et choisissez **propriétés**.

1. Sélectionnez l’onglet **Débogage**.
   
1. Dans le **propriétés** volet, en regard **profil**, 
   - Pour IIS Express, sélectionnez **IIS Express** dans la liste déroulante.
   - Pour IIS local, sélectionnez le nom de l’application dans la liste déroulante, ou sélectionnez **New**, créez un nouveau nom de profil, puis sélectionnez **OK**.
   
1. Regard **lancer**, sélectionnez **IIS Express** ou **IIS** dans la liste déroulante. 
   
1. Assurez-vous que **lancer le navigateur** est sélectionné.
   
1. Sous **variables d’environnement**, assurez-vous que l’option **ASPNETCORE_ENVIRONMENT** est établie avec une valeur de **développement**. Dans le cas contraire, sélectionnez **ajouter** et ajoutez-le.
   
   ![Paramètres du débogueur ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "paramètres du débogueur ASP.NET Core")
   
1. Utilisez **fichier** > **enregistrer les éléments sélectionnés** ou **Ctrl**+**S** enregistrer les modifications. 
   
1. Pour déboguer l’application, dans votre projet, définir des points d’arrêt sur du code. Dans la barre d’outils Visual Studio, assurez-vous que la configuration est définie sur **déboguer**et la valeur **IIS Express**, ou le nouveau nom de profil IIS, apparaît dans le champ de l’émulateur. 
   
1. Pour démarrer le débogage, sélectionnez **IIS Express** ou  **\<nom du profil IIS >** dans la barre d’outils, sélectionnez **démarrer le débogage** à partir de la **déboguer** menu, ou appuyez sur **F5**. Le débogueur s’arrête sur les points d’arrêt. Si le débogueur ne peut pas atteindre les points d’arrêt, consultez [résolution des problèmes de débogage](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Résoudre les problèmes de débogage

Si le débogage local d’IIS ne peuvent pas progresser au point d’arrêt, suivez ces étapes pour résoudre les problèmes. 

1. Démarrez l’application web à partir d’IIS et assurez-vous qu’il fonctionne correctement. Laissez l’application web en cours d’exécution.
   
2. À partir de Visual Studio, sélectionnez **Déboguer > Attacher au processus** ou appuyez sur **Ctrl**+**Alt**+**P**, et se connecter au processus ASP.NET ou ASP.NET Core (généralement **w3wp.exe** ou **dotnet.exe**). Pour plus d’informations, consultez [attacher au processus](attach-to-running-processes-with-the-visual-studio-debugger.md) et [comment rechercher le nom du processus ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Si vous pouvez vous connecter et atteint le point d’arrêt à l’aide de **attacher au processus**, mais ne pas à l’aide **déboguer** > **démarrer le débogage** ou **F5**, un paramètre est probablement incorrect dans les propriétés du projet. Si vous utilisez un fichier HOSTS, assurez-vous qu’il est également configuré correctement.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurer le débogage dans le fichier web.config  

Les projets ASP.NET ont *web.config* par défaut, les fichiers qui contiennent les informations de configuration et de lancement application, y compris les paramètres de débogage. Le *web.config* fichiers doivent être correctement configurés pour le débogage. Le **propriétés** paramètres de mise à jour des sections précédentes le *web.config* fichiers, mais vous pouvez également les configurer manuellement. 

> [!NOTE]
> Les projets ASP.NET Core n’ont pas initialement *web.config* fichiers, mais utilisez *appsettings.json* et *launchSettings.json* fichiers pour la configuration de l’application et de lancement plus d’informations. Déploiement de l’application crée un *web.config* ou les fichiers dans le projet, mais ils ne contiennent généralement les informations de débogage.

> [!TIP]
> Votre processus de déploiement peut mettre à jour le *web.config* paramètres, par conséquent, avant d’essayer de déboguer, vérifiez que le *web.config* est configuré pour le débogage.
  
**Pour configurer manuellement un *web.config* fichier pour le débogage :**

1. Dans Visual Studio, ouvrez le projet ASP.NET *web.config* fichier.  
  
2. *Web.config* est un fichier XML, par conséquent, contient des sections imbriquées marquées par des balises. Recherchez la section `configuration/system.web/compilation`. (Si le `compilation` élément n’existe pas, créez-le.)
  
3. Assurez-vous que le `debug` d’attribut dans le `compilation` élément est défini sur `true`. (Si le `compilation` élément ne contient pas un `debug` d’attribut, ajoutez-le et affectez-lui la valeur `true`.) 
  
   Si vous utilisez IIS local au lieu du serveur d’IIS Express par défaut, assurez-vous que le `targetFramework` attribut la valeur dans la `compilation` élément correspond à l’infrastructure sur le serveur IIS.
  
   Le `compilation` élément de la *web.config* fichier doit se présenter comme dans l’exemple suivant :

   > [!NOTE]
   > Cet exemple est un partiel *web.config* fichier. Il existe généralement autres sections XML dans le `configuration` et `system.web` éléments et le `compilation` élément peut également contenir des autres éléments et attributs.
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] détecte automatiquement les modifications apportées aux fichiers *web.config* et applique les nouveaux paramètres de configuration. Vous n’êtes pas obligé de redémarrer l’ordinateur ou le serveur IIS pour que les modifications entrent en vigueur.  
  
Un site Web peut contenir plusieurs répertoires et sous-répertoires virtuels, avec *web.config* fichiers dans chacun d’eux. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications héritent des paramètres de configuration de *web.config* fichiers à des niveaux supérieurs dans le chemin d’URL. La liste hiérarchique *web.config* les paramètres de fichier s’appliquent à tous les [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications inférieurs dans la hiérarchie. Définition d’une configuration différente dans un *web.config* fichier inférieur dans la hiérarchie substitue aux paramètres dans le fichier plus élevé.  
  
Par exemple, si vous spécifiez `debug="true"` dans <em>www.microsoft.com/aaa/web.config</em>, n’importe quelle application dans le *aaa* dossier ou dans n’importe quel sous-dossier de *aaa* hérite de ce paramètre, sauf si une de ces applications remplace le paramètre avec sa propre *web.config* fichier.  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>Publier en mode débogage à l’aide du système de fichiers

Il existe différentes façons de publier des applications dans IIS. Ces étapes vous montrent comment créer et déployer un profil de publication à l’aide du système de fichiers de débogage. Pour ce faire, vous devez exécuter Visual Studio en tant qu’administrateur. 

> [!IMPORTANT]
> Si vous modifiez votre code ou la reconstruction, vous devez répéter ces étapes pour publier à nouveau. 

1. Dans Visual Studio, cliquez sur le projet et choisissez **publier**.

3. Choisissez **IIS, FTP, etc.** et cliquez sur **publier**.

    ![Publier sur IIS](media/dbg-aspnet-local-iis.png "publier sur IIS")

4. Dans le **CustomProfile** boîte de dialogue, pour **méthode de publication**, choisissez **système de fichiers**.

5. Pour **emplacement cible**, sélectionnez **Parcourir** (**...** ).
   
   - Pour ASP.NET, sélectionnez **IIS Local**, sélectionnez le site Web que vous avez créé pour l’application, puis **Open**.
     
     ![Publier dans ASP.NET sur IIS](media/dbg-aspnet-local-iis1.png "publier ASP.NET sur IIS")
     
   - Pour ASP.NET Core, sélectionnez **système de fichiers**, sélectionnez le dossier que vous configurez pour l’application, puis sélectionnez **Open**.

1. Sélectionnez **Suivant**. 

1. Sous **Configuration**, sélectionnez **déboguer** dans la liste déroulante.

1. Sélectionnez **Enregistrer**.

1. Dans le **publier** boîte de dialogue, assurez-vous que **CustomProfile** (ou le nom du profil que vous venez de créer) s’affiche, et **LastUsedBuildConfiguration** est défini sur  **Déboguer**. 

1. Sélectionnez **Publier**.

    ![Publier sur IIS](media/dbg-aspnet-local-iis-select-site.png "publier sur IIS")

> [!IMPORTANT]
> Mode débogage réduit considérablement les performances de votre application. Pour de meilleures performances, définissez `debug="false"` dans le *web.config* et spécifiez une version Release lorsque vous déployez une application de production ou mesurer les performances.  

## <a name="see-also"></a>Voir aussi  
[Débogage ASP.NET : configuration requise](aspnet-debugging-system-requirements.md)   
[Guide pratique pour exécuter le processus Worker sous un compte d’utilisateur](how-to-run-the-worker-process-under-a-user-account.md)   
[Guide pratique pour rechercher le nom du processus ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Déboguer des applications web déployées](debugging-deployed-web-applications.md)   
[Procédure pas à pas : Débogage d’un formulaire web](walkthrough-debugging-a-web-form.md)   
[Guide pratique pour déboguer des exceptions ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Déboguer des applications web : Erreurs et dépannage](debugging-web-applications-errors-and-troubleshooting.md)
