---
title: Activer le débogage pour les applications ASP.NET | Microsoft Docs
description: Découvrez comment activer le débogage pour les applications ASP.NET et ASP.NET Core dans Visual Studio. Vous pouvez exécuter le processus sur un serveur IIS Express ou sur un serveur IIS local.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 1fd620a0c7f4860421b6f8b1a15c0b708c1ba860
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729258"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Déboguer des applications ASP.NET ou ASP.NET Core dans Visual Studio

Vous pouvez déboguer des applications ASP.NET et ASP.NET Core dans Visual Studio. Le processus diffère entre ASP.NET et ASP.NET Core, et indique si vous l’exécutez sur IIS Express ou sur un serveur IIS local.

>[!NOTE]
>Les étapes et les paramètres suivants s’appliquent uniquement au débogage des applications sur un serveur local. Le débogage d’applications sur un serveur IIS distant utilise l' **attachement au processus** et ignore ces paramètres. Pour plus d’informations et des instructions pour le débogage à distance des applications ASP.NET sur IIS, consultez [débogage distant ASP.net sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou [débogage à distance ASP.net Core sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Le IIS Express Server intégré est inclus dans Visual Studio. IIS Express est le serveur de débogage par défaut pour les projets ASP.NET et ASP.NET Core, et est préconfiguré. C’est le moyen le plus simple de déboguer et idéal pour le débogage et les tests initiaux.

Vous pouvez également déboguer une application ASP.NET ou ASP.NET Core sur un serveur IIS local (version 8,0 ou ultérieure) configuré pour exécuter l’application. Pour déboguer sur un serveur IIS local, vous devez respecter les conditions suivantes :

<a name="iis"></a>
- S’il n’est pas installé, installez la **charge de travail ASP.net et développement Web**. (Réexécutez l’Visual Studio Installer, sélectionnez **modifier**, puis ajoutez cette charge de travail.)

   ::: moniker range="vs-2017"
   Dans Visual Studio 2017, recherchez le composant **prise en charge d’IIS au moment du développement** . Assurez-vous qu’elle est sélectionnée lorsque vous ajoutez la charge de travail.
   ::: moniker-end
- Exécutez Visual Studio en tant qu’administrateur.
- Installez et configurez correctement IIS avec la ou les versions appropriées de ASP.NET et/ou de ASP.NET Core. Pour plus d’informations sur l’utilisation d’IIS avec ASP.NET Core, consultez la page [hôte ASP.net Core sur Windows avec IIS](/aspnet/core/host-and-deploy/iis/index). Pour ASP.NET, consultez [installer les modules IIS et ASP.net](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Assurez-vous que l’application s’exécute sur IIS sans erreurs.

## <a name="debug-aspnet-apps"></a>Déboguer les applications ASP.NET

IIS Express est la valeur par défaut, et est préconfiguré. Si vous effectuez un débogage sur IIS local, assurez-vous que vous remplissez les [conditions requises pour le débogage IIS local](#iis).

1. Sélectionnez le projet ASP.net dans Visual Studio **Explorateur de solutions** puis cliquez sur l’icône **Propriétés** , ou appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Sélectionnez l’onglet **Web** .

1. Dans le volet **Propriétés** , sous **serveurs**,
   - Pour IIS Express, sélectionnez **IIS Express** dans la liste déroulante.
   - Pour les services IIS locaux,
     1. Sélectionnez **IIS local** dans la liste déroulante.
     1. En regard du champ **URL du projet** , sélectionnez créer un **répertoire virtuel**, si vous n’avez pas encore configuré l’application dans IIS.

1. Sous **débogueurs**, sélectionnez **ASP.net**.

   ![Paramètres du débogueur ASP.NET](media/dbg-aspnet-enable-debugging2.png "Paramètres du débogueur ASP.NET")

1. Choisissez **fichier**  >  **enregistrer les éléments sélectionnés** (ou appuyez sur **CTRL** + **S**) pour enregistrer les modifications.

1. Pour déboguer l’application, dans votre projet, définissez des points d’arrêt sur du code. Dans la barre d’outils de Visual Studio, assurez-vous que la configuration est définie sur **Déboguer**, et que le navigateur souhaité s’affiche dans **IIS Express ( \<Browser name> )** ou **IIS local ( \<Browser name> )** dans le champ émulateur.

1. Pour démarrer le débogage, sélectionnez **IIS Express ( \<Browser name> )** ou **IIS local ( \<Browser name> )** dans la barre d’outils, sélectionnez **Démarrer le débogage** dans le menu **Déboguer** ou appuyez sur **F5**. Le débogueur s’arrête au niveau des points d’arrêt. Si le débogueur ne parvient pas à atteindre les points d’arrêt, consultez [résoudre les problèmes de débogage](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Déboguer les applications ASP.NET Core

IIS Express est la valeur par défaut, et est préconfiguré. Si vous effectuez un débogage sur IIS local, assurez-vous que vous remplissez les [conditions requises pour le débogage IIS local](#iis).

1. Sélectionnez le projet ASP.net core dans Visual Studio **Explorateur de solutions** puis cliquez sur l’icône **Propriétés** , ou appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Sélectionnez l’onglet **Débogage**.

1. Dans le volet **Propriétés** , en regard de **Profil**,
   - Pour IIS Express, sélectionnez **IIS Express** dans la liste déroulante.
   - Pour IIS local, sélectionnez le nom de l’application dans la liste déroulante ou sélectionnez **nouveau**, créez un nom de profil, puis sélectionnez **OK**.

1. En regard de **lancement**, sélectionnez **IIS Express** ou **IIS** dans la liste déroulante.

1. Assurez-vous que l’option **lancer le navigateur** est sélectionnée.

1. Sous **variables d’environnement**, assurez-vous que **ASPNETCORE_ENVIRONMENT** est présent avec la valeur **développement**. Si ce n’est pas le cas, sélectionnez **Ajouter** et ajoutez-le.

   ![ASP.NET Core les paramètres du débogueur](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core les paramètres du débogueur")

1. Utilisez **fichier**  >  **enregistrer les éléments sélectionnés** ou **CTRL** + **S** pour enregistrer les modifications.

1. Pour déboguer l’application, dans votre projet, définissez des points d’arrêt sur du code. Dans la barre d’outils de Visual Studio, assurez-vous que la configuration est définie sur **Déboguer**, et que **IIS Express**, ou le nouveau nom de profil IIS, apparaît dans le champ émulateur.

1. Pour démarrer le débogage, sélectionnez **IIS Express** ou **\<IIS profile name>** dans la barre d’outils, sélectionnez **Démarrer le débogage** dans le menu **Déboguer** ou appuyez sur **F5**. Le débogueur s’arrête au niveau des points d’arrêt. Si le débogueur ne parvient pas à atteindre les points d’arrêt, consultez [résoudre les problèmes de débogage](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Résoudre les problèmes de débogage

Si le débogage IIS local ne peut pas progresser jusqu’au point d’arrêt, procédez comme suit pour résoudre le problèmes.

1. Démarrez l’application Web à partir d’IIS et assurez-vous qu’elle s’exécute correctement. Laissez l’application Web en cours d’exécution.

2. Dans Visual Studio, sélectionnez **Déboguer > attacher au processus** ou appuyez sur **CTRL** + **ALT** + **P**, puis connectez-vous au processus ASP.net ou ASP.net Core (généralement **w3wp.exe** ou **dotnet.exe**). Pour plus d’informations, consultez [attacher au processus](attach-to-running-processes-with-the-visual-studio-debugger.md) et [Comment rechercher le nom du processus ASP.net](how-to-find-the-name-of-the-aspnet-process.md).

Si vous pouvez vous connecter et atteindre le point d’arrêt à l’aide de l’option **attacher au processus**, mais pas **en utilisant déboguer**  >  **Démarrer le débogage** ou **F5**, un paramètre est probablement incorrect dans les propriétés du projet. Si vous utilisez un fichier HOSTs, assurez-vous qu’il est également configuré correctement.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurer le débogage dans le fichier web.config

Les projets ASP.NET ont des fichiers *web.config* par défaut, qui contiennent des informations de configuration d’application et de lancement, y compris les paramètres de débogage. Les fichiers de *web.config* doivent être configurés correctement pour le débogage. Les paramètres des **Propriétés** des sections précédentes mettent à jour les fichiers *web.config* , mais vous pouvez également les configurer manuellement.

> [!NOTE]
> Les projets de ASP.NET Core n’ont pas initialement des fichiers *web.config* , mais utilisent *appsettings.js* et *launchSettings.jssur* les fichiers pour la configuration et les informations de lancement de l’application. Le déploiement de l’application crée un fichier *web.config* ou des fichiers dans le projet, mais ils ne contiennent généralement pas d’informations de débogage.

> [!TIP]
> Votre processus de déploiement peut mettre à jour les paramètres de *web.config* . par conséquent, avant d’essayer de déboguer, assurez-vous que le *web.config* est configuré pour le débogage.

**Pour configurer manuellement un fichier de *web.config* pour le débogage :**

1. Dans Visual Studio, ouvrez le fichier *web.config* du projet ASP.net.

2. *Web.config* est un fichier XML, contient des sections imbriquées marquées par des balises. Recherchez la section `configuration/system.web/compilation`. (Si l' `compilation` élément n’existe pas, créez-le.)

3. Assurez-vous que l' `debug` attribut dans l' `compilation` élément a la valeur `true` . (Si l' `compilation` élément ne contient pas d' `debug` attribut, ajoutez-le et affectez-lui la valeur `true` .)

   Si vous utilisez IIS local au lieu du serveur par défaut IIS Express, assurez-vous que la `targetFramework` valeur de l’attribut dans l' `compilation` élément correspond à l’infrastructure sur le serveur IIS.

   L' `compilation` élément du fichier *web.config* doit ressembler à l’exemple suivant :

   > [!NOTE]
   > Cet exemple est un fichier *web.config* partiel. Il y a généralement des sections XML supplémentaires dans les `configuration` `system.web` éléments et, et l' `compilation` élément peut également contenir d’autres attributs et éléments.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] détecte automatiquement les modifications apportées aux fichiers *web.config* et applique les nouveaux paramètres de configuration. Vous n’êtes pas obligé de redémarrer l’ordinateur ou le serveur IIS pour que les modifications prennent effet.

Un site Web peut contenir plusieurs répertoires et sous-répertoires virtuels, avec *web.config* fichiers dans chacun d’eux. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] les applications héritent des paramètres de configuration des fichiers *web.config* à des niveaux supérieurs dans le chemin d’accès de l’URL. Les paramètres de fichier *web.config* hiérarchique s’appliquent à toutes les [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications situées au-dessous dans la hiérarchie. La définition d’une configuration différente dans un fichier de *web.config* plus bas dans la hiérarchie remplace les paramètres dans le fichier supérieur.

Par exemple, si vous spécifiez `debug="true"` dans <em>www.Microsoft.com/AAA/web.config</em>, toute application dans le dossier *AAA* ou dans un sous-dossier de *AAA* hérite de ce paramètre, sauf si l’une de ces applications remplace le paramètre par son propre fichier *web.config* .

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publier en mode débogage à l’aide du système de fichiers

Il existe différentes façons de publier des applications sur IIS. Ces étapes montrent comment créer et déployer un profil de publication de débogage à l’aide du système de fichiers. Pour ce faire, vous devez exécuter Visual Studio en tant qu’administrateur.

> [!IMPORTANT]
> Si vous modifiez votre code ou la régénération, vous devez répéter ces étapes pour republier.

1. Dans Visual Studio, cliquez avec le bouton droit sur le projet et choisissez **publier**.

3. Choisissez **IIS, FTP, etc.** , puis cliquez sur **publier**.

    ![Capture d’écran de la boîte de dialogue choisir une cible de publication dans Visual Studio. Une Web Deploy IIS, FTP, est sélectionnée et le bouton publier est mis en surbrillance.](media/dbg-aspnet-local-iis.png)

4. Dans la boîte de dialogue **CustomProfile** , pour la **méthode de publication**, choisissez **système de fichiers**.

5. Pour **emplacement cible**, sélectionnez **Parcourir** (**...**).

   - Pour ASP.NET, sélectionnez **IIS local**, sélectionnez le site Web que vous avez créé pour l’application, puis sélectionnez **ouvrir**.

     ![Publier sur ASP.NET sur IIS](media/dbg-aspnet-local-iis1.png "Publier des ASP.NET sur IIS")

   - Pour ASP.NET Core, sélectionnez **système de fichiers**, sélectionnez le dossier que vous avez configuré pour l’application, puis sélectionnez **ouvrir**.

1. Sélectionnez **Suivant**.

1. Sous **configuration**, sélectionnez **Déboguer** dans la liste déroulante.

1. Sélectionnez **Enregistrer**.

1. Dans la boîte de dialogue **publier** , vérifiez que **CustomProfile** (ou le nom du profil que vous venez de créer) apparaît et que **LastUsedBuildConfiguration** est défini sur **Debug**.

1. Sélectionnez **Publier**.

    ![Capture d’écran de la boîte de dialogue publier, avec l’application CustomProfile sélectionnée, le bouton publier mis en surbrillance et LastBuildConfiguration défini sur débogage.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Le mode débogage réduit considérablement les performances de votre application. Pour de meilleures performances, définissez `debug="false"` dans le *web.config* et spécifiez une version Release quand vous déployez une application de production ou exécutez des mesures de performances.

## <a name="see-also"></a>Voir aussi
- [Débogage ASP.NET : configuration requise](aspnet-debugging-system-requirements.md)
- [Guide pratique pour exécuter le processus Worker sous un compte d’utilisateur](how-to-run-the-worker-process-under-a-user-account.md)
- [Guide pratique pour rechercher le nom du processus ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Déboguer des applications Web déployées](debugging-deployed-web-applications.md)
- [Procédure pas à pas : débogage d’un formulaire Web](walkthrough-debugging-a-web-form.md)
- [Guide pratique pour déboguer des exceptions ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Déboguer des applications Web : erreurs et dépannage](debugging-web-applications-errors-and-troubleshooting.md)
