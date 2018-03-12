---
title: "Création d’Applications ClickOnce à partir de la ligne de commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 39a64737c3e34b7e0c4d89824b22f169d60d4fd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Génération d'applications ClickOnce à partir de la ligne de commande
Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vous pouvez générer des projets à partir de la ligne de commande, même s’ils sont créés dans l’environnement de développement intégré (IDE). En fait, vous pouvez régénérer un projet créé avec [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sur un autre ordinateur qui a uniquement les [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installé. Cela vous permet de reproduire une génération à l’aide d’un processus automatisé, par exemple, dans une build centrale lab ou à l’aide de techniques de script avancées dépasse le cadre de la génération du projet lui-même.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Utilisation de MSBuild pour reproduire des déploiements d’applications ClickOnce  
 Lorsque vous appelez/target : Publish de msbuild sur la ligne de commande, il indique le système MSBuild pour générer le projet et de créer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application dans le dossier de publication. Cela revient à sélectionner la **publier** dans l’IDE.  
  
 Cette commande exécute msbuild.exe, qui se trouve sur le chemin d’accès dans l’environnement d’invite de commandes de Visual Studio.  
  
 Une « cible » est un indicateur à MSBuild sur la façon de traiter la commande. Les principales cibles sont la cible « build » et la cible « publier ». La cible build est équivalente à la sélection de la Build command (ou en appuyant sur F5) dans l’IDE. Si vous souhaitez uniquement générer votre projet, vous pouvez effectuer cette en tapant `msbuild`. Cette commande fonctionne parce que la cible de génération est la cible par défaut pour tous les projets générés par [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Cela signifie que vous n’avez pas explicitement besoin spécifier la cible de génération. Par conséquent, en tapant `msbuild` est la même opération en tapant `msbuild /target:build`.  
  
 Le `/target:publish` commande indique à MSBuild d’appeler la cible de publication. La cible build dépend de la cible de publication. Cela signifie que l’opération de publication est un sur-ensemble de l’opération de génération. Par exemple, si vous avez une modification d’un de vos fichiers sources Visual Basic ou c#, l’assembly correspondant est automatiquement régénéré par l’opération de publication.  
  
 Pour plus d’informations sur la génération d’un intégral [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement à l’aide de l’outil de ligne de commande Mage.exe pour créer votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de manifeste, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Création et la création d’une Application ClickOnce de base à l’aide de MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Pour créer et publier un projet ClickOnce  
  
1.  Cliquez sur **nouveau projet** à partir de la **fichier** menu. La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez **Application Windows** et nommez-le `CmdLineDemo`.  
  
3.  À partir de la **générer** menu, cliquez sur le **publier** commande.  
  
     Cette étape permet de s’assurer que le projet est correctement configuré pour produire un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement d’application.  
  
     L'Assistant Publication apparaît.  
  
4.  Dans l’Assistant Publication, cliquez sur **Terminer**.  
  
     Visual Studio génère et affiche la page Web par défaut, appelée Publish.htm.  
  
5.  Enregistrer votre projet et notez l’emplacement du dossier dans lequel il est stocké.  
  
 La procédure ci-dessus crée un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projet qui a été publiée pour la première fois. Maintenant, vous pouvez reproduire la génération en dehors de l’IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Pour reproduire la génération à partir de la ligne de commande  
  
1.  Quittez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  À partir des fenêtres **Démarrer** menu, cliquez sur **tous les programmes**, puis **Microsoft Visual Studio**, puis **Visual Studio Tools**, puis **Invite de commandes visual Studio**. Cela doit ouvrir une invite de commandes dans le dossier racine de l’utilisateur actuel.  
  
3.  Dans le **invite de commandes Visual Studio**, modifiez le répertoire actuel à l’emplacement du projet que vous venez de créer ci-dessus. Par exemple, tapez `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Pour supprimer les fichiers existants produits dans « pour créer et publier un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projet, « type `rmdir /s publish`.  
  
     Cette étape est facultative, mais il garantit que les nouveaux fichiers ont été générés par la version de ligne de commande.  
  
5.  Tapez `msbuild /target:publish`.  
  
 Les étapes ci-dessus produiront un complet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement d’application dans un sous-dossier de votre projet nommé P**blier**. CmdLineDemo.application est le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Le dossier CmdLineDemo_1.0.0.0 contient les fichiers CmdLineDemo.exe et CmdLineDemo.exe.manifest, le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Setup.exe est le programme d’amorçage, qui par défaut est configuré pour installer le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Le dossier DotNetFX contient les redistribuables pour le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Il s’agit de l’ensemble des fichiers que vous avez besoin pour déployer votre application via le Web ou UNC ou d’un CD/DVD.  
  
## <a name="publishing-properties"></a>Propriétés de publication  
 Lorsque vous publiez l’application dans les procédures ci-dessus, les propriétés suivantes sont insérées dans votre fichier projet par l’Assistant Publication. Ces propriétés influencent directement la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est produite.  
  
 Dans CmdLineDemo.vbproj / CmdLineDemo.csproj :  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Vous pouvez remplacer une de ces propriétés au niveau de la ligne de commande sans modifier le fichier projet. Par exemple, ce qui suit va générer le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement d’application sans le programme d’amorçage :  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Propriétés de publication sont contrôlées dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la **publier**, **sécurité**, et **signature** pages de propriétés de la **Concepteur de projets** . Vous trouverez ci-dessous une description des propriétés de publication, avec une indication de la façon dont chacun est définie dans les différentes pages de propriétés du Concepteur d’applications :  
  
-   `AssemblyOriginatorKeyFile`Détermine le fichier de clé utilisé pour signer votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes d’application. Cette même clé peut également être utilisée pour attribuer un nom fort à vos assemblys. Cette propriété est définie sur le **signature** page de la **Concepteur de projet**.  
  
 Les propriétés suivantes sont définies sur le **sécurité** page :  
  
-   **Activer les paramètres de sécurité ClickOnce** détermine si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes ont été générés. Lorsqu’un projet est créé, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la génération du manifeste est désactivée par défaut. L’Assistant active automatiquement cet indicateur sur lorsque vous publiez pour la première fois.  
  
-   **TargetZone** détermine le niveau de confiance à émettre dans votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Les valeurs possibles sont « Internet », « LocalIntranet » et « Custom ». Internet et LocalIntranet entraînent une autorisation par défaut définie dans votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. LocalIntranet est la valeur par défaut, et il signifie une confiance totale. Custom Spécifie que seules les autorisations spécifiées explicitement dans le fichier App.manifest de base doivent être émis dans le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Le fichier App.manifest est un fichier de manifeste partiel qui contient les définitions de plus d’informations d’approbation. Il s’agit d’un fichier masqué, ajouté automatiquement à votre projet lorsque vous configurez les autorisations sur le **sécurité** page.  
  
 Les propriétés suivantes sont définies sur le **publier** page :  
  
-   `PublishUrl`est l’emplacement où l’application sera publiée à dans l’IDE. Il est inséré dans le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application si ni le `InstallUrl` ou `UpdateUrl` propriété est spécifiée.  
  
-   `ApplicationVersion`Spécifie la version de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Il s’agit d’un numéro de version de quatre chiffres. Si le dernier chiffre est un « * », puis le `ApplicationRevision` est remplacé par la valeur insérée dans le manifeste au moment de la génération.  
  
-   `ApplicationRevision`Spécifie la révision. Il s’agit d’un entier qui incrémente chaque fois que vous publiez dans l’IDE. Notez qu’il n’est pas automatiquement incrémenté pour les builds exécutées sur la ligne de commande.  
  
-   `Install`Détermine si l’application est une application installée ou une application d’exécution à partir du Web.  
  
-   `InstallUrl`(non affichée) est l’emplacement où les utilisateurs installent l’application à partir de. Si spécifié, cette valeur est intégrée dans le programme d’amorçage setup.exe si le `IsWebBootstrapper` propriété est activée. Il est également inséré dans la manifeste d’application si le `UpdateUrl` n’est pas spécifié.  
  
-   `SupportUrl`(non affichée) est l’emplacement lié dans le **Ajout/Suppression de programmes** boîte de dialogue pour une application installée.  
  
 Les propriétés suivantes sont définies le **mises à jour de l’Application** boîte de dialogue, accédé à partir de la **publier** page.  
  
-   `UpdateEnabled`Indique si l’application doit vérifier les mises à jour.  
  
-   `UpdateMode`Spécifie les mises à jour de premier plan ou de mises à jour en arrière-plan.  
  
-   `UpdateInterval`Spécifie la fréquence à laquelle l’application doit vérifier les mises à jour.  
  
-   `UpdateIntervalUnits`Spécifie si le `UpdateInterval` valeur est exprimée en heures, jours ou semaines.  
  
-   `UpdateUrl`(non affichée) est l’emplacement à partir duquel l’application recevra les mises à jour. Si spécifié, cette valeur est insérée dans le manifeste d’application.  
  
-   Les propriétés suivantes sont définies le **Options de publication** boîte de dialogue, accédé à partir de la **publier** page.  
  
-   `PublisherName`Spécifie le nom du serveur de publication affiché dans l’invite qui s’affiché lors de l’installation ou l’exécution de l’application. Dans le cas d’une application installée, il est également utilisé pour spécifier le nom du dossier sur le **Démarrer** menu.  
  
-   `ProductName`Spécifie le nom du produit indiqué dans l’invite qui s’affiché lors de l’installation ou l’exécution de l’application. Dans le cas d’une application installée, il est également utilisé pour spécifier le nom du raccourci sur le **Démarrer** menu.  
  
-   Les propriétés suivantes sont définies le **conditions préalables** boîte de dialogue, accédé à partir de la **publier** page.  
  
-   `BootstrapperEnabled`Détermine s’il faut générer le programme d’amorçage setup.exe.  
  
-   `IsWebBootstrapper`Détermine si le programme d’amorçage setup.exe fonctionne sur le Web ou le mode basée sur disque.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL et UpdateURL  
 Le tableau suivant montre les quatre options d’URL pour le déploiement ClickOnce.  
  
|Option d’URL|Description|  
|----------------|-----------------|  
|`PublishURL`|Obligatoire si vous publiez votre application ClickOnce à un site Web.|  
|`InstallURL`|Facultatif. Définissez cette option si le site de l’installation est différent de celle du `PublishURL`. Par exemple, vous pouvez définir le `PublishURL` à un chemin d’accès FTP et d’un jeu le `InstallURL` vers une URL Web.|  
|`SupportURL`|Facultatif. Définissez cette option si le site de prise en charge est différent de celui du `PublishURL`. Par exemple, vous pouvez définir le `SupportURL` au site Web de votre société client prise en charge.|  
|`UpdateURL`|Facultatif. Définissez cette option si l’emplacement de mise à jour est différent de celui du `InstallURL`. Par exemple, vous pouvez définir le `PublishURL` à un chemin d’accès FTP et d’un jeu le `UpdateURL` vers une URL Web.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)