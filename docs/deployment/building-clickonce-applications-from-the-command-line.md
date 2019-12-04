---
title: Génération d’applications ClickOnce à partir de la ligne de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797201"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Générer des applications ClickOnce à partir de la ligne de commande
Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vous pouvez générer des projets à partir de la ligne de commande, même s’ils sont créés dans l’environnement de développement intégré (IDE). En fait, vous pouvez reconstruire un projet créé avec [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sur un autre ordinateur sur lequel seul le .NET Framework est installé. Cela vous permet de reproduire une génération à l’aide d’un processus automatisé, par exemple dans un laboratoire de génération central ou à l’aide de techniques de script avancées au-delà de la portée de la génération du projet lui-même.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Utiliser MSBuild pour reproduire des déploiements d’applications ClickOnce
 Quand vous appelez MSBuild/target : publish sur la ligne de commande, il indique au système MSBuild de générer le projet et de créer une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application dans le dossier Publish. Cela équivaut à sélectionner la commande **publier** dans l’IDE.

 Cette commande exécute *MSBuild. exe*, qui se trouve sur le chemin d’accès dans l’environnement d’invite de commandes de Visual Studio.

 Une « cible » est un indicateur de MSBuild sur la manière de traiter la commande. Les cibles principales sont la cible « Build » et la cible « Publish ». La cible Build équivaut à sélectionner la commande de génération (ou à appuyer sur F5) dans l’IDE. Si vous souhaitez uniquement générer votre projet, vous pouvez y parvenir en tapant `msbuild`. Cette commande fonctionne, car la cible de génération est la cible par défaut pour tous les projets générés par [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Cela signifie que vous n’avez pas besoin de spécifier explicitement la cible de génération. Par conséquent, la saisie d' `msbuild` est la même opération que la saisie d' `msbuild /target:build`.

 La commande `/target:publish` indique à MSBuild d’appeler la cible de publication. La cible de publication dépend de la cible de génération. Cela signifie que l’opération de publication est un sur-ensemble de l’opération de génération. Par exemple, si vous avez apporté une modification à l’un de vos C# Visual Basic ou fichiers sources, l’assembly correspondant est automatiquement régénéré par l’opération de publication.

 Pour plus d’informations sur la génération d’un déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complet à l’aide de l’outil en ligne de commande Mage. exe pour créer votre manifeste de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Créer et générer une application ClickOnce de base avec MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Pour créer et publier un projet ClickOnce

1. Ouvrez Visual Studio et créez un projet.

    Choisissez le modèle de projet **application de bureau Windows** et nommez le projet `CmdLineDemo`.

1. Dans le menu **générer** , cliquez sur la commande **publier** .

    Cette étape permet de s’assurer que le projet est correctement configuré pour produire un déploiement d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

    L'Assistant Publication s'affiche.

1. Dans l’Assistant publication, cliquez sur **Terminer**.

    Visual Studio génère et affiche la page Web par défaut, appelée *Publish. htm*.

1. Enregistrez votre projet et prenez note de l’emplacement du dossier dans lequel il est stocké.

   Les étapes ci-dessus créent un projet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui a été publié pour la première fois. Vous pouvez maintenant reproduire la génération en dehors de l’IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Pour reproduire la génération à partir de la ligne de commande

1. Quittez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Dans le menu **Démarrer** de Windows, cliquez sur **tous les programmes**, **Microsoft Visual Studio**, **Visual Studio Tools**, puis sur **invite de commandes de Visual Studio**. Cela doit ouvrir une invite de commandes dans le dossier racine de l’utilisateur actuel.

3. Dans l' **invite de commandes de Visual Studio**, remplacez le répertoire actif par l’emplacement du projet que vous venez de générer. Par exemple, tapez `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Pour supprimer les fichiers existants générés dans « pour créer et publier un projet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] », tapez `rmdir /s publish`.

    Cette étape est facultative, mais elle garantit que les nouveaux fichiers ont tous été générés par la génération de la ligne de commande.

5. Tapez `msbuild /target:publish`.

   Les étapes ci-dessus produiront un déploiement complet de l’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dans un sous-dossier de votre projet nommé **Publish**. *CmdLineDemo. application* est le manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Le dossier *CmdLineDemo_1.0.0.0* contient les fichiers *CmdLineDemo. exe* et *CmdLineDemo. exe. manifest*, le manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. *Setup. exe* est le programme d’amorçage, qui est configuré par défaut pour installer le .NET Framework. Le dossier DotNetFX contient les fichiers redistribuables du .NET Framework. Il s’agit de l’ensemble complet des fichiers dont vous avez besoin pour déployer votre application sur le Web ou via un UNC ou un CD/DVD.
   
> [!NOTE]
> Le système MSBuild utilise l’option **PublishDir** pour spécifier l’emplacement de sortie, par exemple `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Propriétés de publication
 Lorsque vous publiez l’application dans les procédures ci-dessus, les propriétés suivantes sont insérées dans votre fichier projet par l’Assistant Publication. Ces propriétés influencent directement le mode de production de l’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

 Dans *CmdLineDemo.vbproj* / *CmdLineDemo.csproj* :

```xml
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

 Vous pouvez remplacer ces propriétés au niveau de la ligne de commande sans modifier le fichier projet lui-même. Par exemple, le code suivant génère le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement de l’application sans le programme d’amorçage :

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Les propriétés de publication sont contrôlées dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir des pages de propriétés **publier**, **sécurité**et **signature** du **Concepteur de projets**. Vous trouverez ci-dessous une description des propriétés de publication, ainsi qu’une indication de la façon dont chacune est définie dans les différentes pages de propriétés du concepteur d’application :

- `AssemblyOriginatorKeyFile` détermine le fichier de clé utilisé pour signer vos manifestes d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Cette même clé peut également être utilisée pour assigner un nom fort à vos assemblys. Cette propriété est définie sur la page **signature** du **Concepteur de projets**.

  Les propriétés suivantes sont définies dans la page **sécurité** :

- **Activer les paramètres de sécurité ClickOnce** détermine si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes sont générés. Quand un projet est initialement créé, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] génération de manifeste est désactivée par défaut. L’assistant active automatiquement cet indicateur lorsque vous publiez pour la première fois.

- **TargetZone** détermine le niveau de confiance à émettre dans votre manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Les valeurs possibles sont « Internet », « LocalIntranet » et « Custom ». Internet et LocalIntranet entraînent l’émission d’un jeu d’autorisations par défaut dans votre manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. LocalIntranet est la valeur par défaut, ce qui signifie une confiance totale. Personnalisé spécifie que seules les autorisations explicitement spécifiées dans le fichier *app. manifest* de base doivent être émises dans le manifeste de l’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Le fichier *app. manifest* est un fichier manifeste partiel qui contient uniquement les définitions d’informations d’approbation. Il s’agit d’un fichier masqué, automatiquement ajouté à votre projet lorsque vous configurez des autorisations sur la page **sécurité** .

  Les propriétés suivantes sont définies sur la page **publier** :

- `PublishUrl` est l’emplacement où l’application sera publiée dans l’IDE. Elle est insérée dans le manifeste de l’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si aucune propriété `InstallUrl` ou `UpdateUrl` n’est spécifiée.

- `ApplicationVersion` spécifie la version de l’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il s’agit d’un numéro de version à quatre chiffres. Si le dernier chiffre est un « * », le `ApplicationRevision` remplace la valeur insérée dans le manifeste au moment de la génération.

- `ApplicationRevision` spécifie la révision. Il s’agit d’un entier qui s’incrémente chaque fois que vous publiez dans l’IDE. Notez qu’il n’est pas incrémenté automatiquement pour les builds effectuées au niveau de la ligne de commande.

- `Install` détermine si l’application est une application installée ou une application exécutée à partir du Web.

- `InstallUrl` (non affiché) est l’emplacement à partir duquel les utilisateurs installent l’application. S’il est spécifié, cette valeur est gravée dans le programme *d’amorçage Setup. exe* si la propriété `IsWebBootstrapper` est activée. Il est également inséré dans le manifeste de l’application si le `UpdateUrl` n’est pas spécifié.

- `SupportUrl` (non affiché) est l’emplacement lié dans la boîte de dialogue **Ajout/suppression de programmes** pour une application installée.

  Les propriétés suivantes sont définies dans la boîte de dialogue **mises à jour des applications** , accessible à partir de la page **publier** .

- `UpdateEnabled` indique si l’application doit vérifier la présence de mises à jour.

- `UpdateMode` spécifie des mises à jour de premier plan ou des mises à jour en arrière-plan.

- `UpdateInterval` spécifie la fréquence à laquelle l’application doit rechercher les mises à jour.

- `UpdateIntervalUnits` spécifie si la valeur de `UpdateInterval` est exprimée en unités d’heures, de jours ou de semaines.

- `UpdateUrl` (non affiché) est l’emplacement à partir duquel l’application recevra les mises à jour. S’il est spécifié, cette valeur est insérée dans le manifeste de l’application.

  Les propriétés suivantes sont définies dans la boîte de dialogue **options de publication** , accessible à partir de la page **publier** .

- `PublisherName` spécifie le nom de l’éditeur affiché dans l’invite affichée lors de l’installation ou de l’exécution de l’application. Dans le cas d’une application installée, elle est également utilisée pour spécifier le nom du dossier dans le menu **Démarrer** .

- `ProductName` spécifie le nom du produit affiché dans l’invite affichée lors de l’installation ou de l’exécution de l’application. Dans le cas d’une application installée, elle est également utilisée pour spécifier le nom du raccourci dans le menu **Démarrer** .

  Les propriétés suivantes sont définies dans la boîte de dialogue **composants requis** , accessible à partir de la page **publier** .

- `BootstrapperEnabled` détermine s’il faut générer le programme *d’amorçage Setup. exe* .

- `IsWebBootstrapper` détermine si le programme *d’amorçage Setup. exe* fonctionne sur le Web ou en mode sur disque.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL et UpdateURL
 Le tableau suivant présente les quatre options d’URL pour le déploiement ClickOnce.

|Option URL|Description|
|----------------|-----------------|
|`PublishURL`|Obligatoire si vous publiez votre application ClickOnce sur un site Web.|
|`InstallURL`|Option facultative. Définissez cette option d’URL si le site d’installation est différent du `PublishURL`. Par exemple, vous pouvez définir la `PublishURL` sur un chemin d’accès FTP et définir la `InstallURL` sur une URL Web.|
|`SupportURL`|Option facultative. Définissez cette option d’URL si le site de support est différent du `PublishURL`. Par exemple, vous pouvez définir le `SupportURL` sur le site Web du support technique de votre entreprise.|
|`UpdateURL`|Option facultative. Définissez cette option d’URL si l’emplacement de mise à jour est différent de l' `InstallURL`. Par exemple, vous pouvez définir la `PublishURL` sur un chemin d’accès FTP et définir la `UpdateURL` sur une URL Web.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
