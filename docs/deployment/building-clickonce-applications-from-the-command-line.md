---
title: "Building ClickOnce Applications from the Command Line | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, from command line"
  - "publishing"
  - "publishing, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Building ClickOnce Applications from the Command Line
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vous pouvez générer des projets à partir de la ligne de commande même s'ils sont créés dans l'environnement de développement intégré \(IDE\).  En fait, vous pouvez régénérer un projet créé avec [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sur un autre ordinateur sur lequel seul le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] est installé.  Cela vous permet de reproduire une génération à l'aide d'un processus automatisé \(par exemple, dans un laboratoire de génération centralisée ou à l'aide de techniques de script avancées dépassant le projet proprement dit\).  
  
## Utilisation de MSBuild pour reproduire des déploiements d'applications ClickOnce  
 Lorsque vous appelez msbuild \/target:publish à la ligne de commande, il indique au système MSBuild de générer le projet et de créer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dans le dossier de publication.  Cela équivaut à sélectionner la commande **Publier** dans l'IDE.  
  
 Cette commande exécute le fichier msbuild.exe qui se trouve sur le chemin d'accès dans l'environnement d'invite de commandes Visual Studio.  
  
 Une « cible » est un élément indiquant à MSBuild la manière de traiter la commande.  Les principales cibles sont la cible de génération et la cible de publication.  La cible de génération revient à sélectionner la commande Générer \(ou à appuyer sur F5\) dans l'IDE.  Si vous souhaitez uniquement générer votre projet, vous pouvez effectuer cette opération en tapant `msbuild`.  Cette commande fonctionne parce que la cible de génération est la cible par défaut pour tous les projets générés par [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Cela signifie que vous n'avez pas besoin de spécifier explicitement la cible de la génération.  Par conséquent, taper `msbuild` revient à taper `msbuild /target:build`.  
  
 La commande `/target:publish` indique à MSBuild d'appeler la cible de publication.  Celle\-ci dépend de la cible de génération.  Cela signifie que l'opération de publication est un sur\-ensemble de l'opération de génération.  Par exemple, si vous avez apporté une modification à l'un de vos fichiers sources Visual Basic ou C\#, l'assembly correspondant est automatiquement régénéré par l'opération de publication.  
  
 Pour plus d'informations sur la génération d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complet à l'aide de l'outil de ligne de commande Mage.exe afin de créer votre manifeste [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Création et génération d'une application ClickOnce de base à l'aide de MSBuild  
  
#### Pour créer et publier un projet ClickOnce  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sélectionnez **Application Windows** et nommez\-la `CmdLineDemo`.  
  
3.  Dans le menu **Générer**, cliquez sur la commande **Publier**.  
  
     Cette étape permet de vérifier que le projet est correctement configuré pour produire un déploiement d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
     L'Assistant Publication s'affiche.  
  
4.  Dans l'Assistant Publication, cliquez sur **Terminer**.  
  
     Visual Studio génère et affiche la page Web par défaut, appelée Publish.htm.  
  
5.  Enregistrez votre projet et prenez note de l'emplacement du dossier dans lequel il est stocké.  
  
 Les étapes ci\-dessus vous ont permis de créer un projet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui a été publié pour la première fois.  Vous pouvez à présent reproduire la génération en dehors de l'IDE.  
  
#### Pour reproduire la génération à partir de la ligne de commande  
  
1.  Quittez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Dans le menu **Démarrer** de Windows, cliquez sur **Tous les programmes**, sur **Microsoft Visual Studio**, sur **Visual Studio Tools**, puis sur **Invite de commandes de Visual Studio**.  Une invite de commandes s'ouvre dans le dossier racine de l'utilisateur actuel.  
  
3.  Dans **Invite de commandes de Visual Studio**, remplacez le répertoire actif par l'emplacement du projet que vous venez de créer ci\-dessus.  Par exemple, tapez `chdir Mes documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Pour supprimer les fichiers existants produits à la section « Pour créer et publier un projet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] », tapez `rmdir /s publish`.  
  
     Cette étape est facultative, mais elle garantit que les nouveaux fichiers ont tous été produits par génération à partir de la ligne de commande.  
  
5.  Tapez `msbuild /target:publish`.  
  
 Les étapes ci\-dessus produiront un déploiement d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complet dans un sous\-dossier de votre projet nommé **Publish**.  CmdLineDemo.application est le manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Le dossier CmdLineDemo\_1.0.0.0 contient les fichiers CmdLineDemo.exe et CmdLineDemo.exe.manifest \(manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\).  Setup.exe est le programme d'amorçage qui est configuré par défaut pour installer le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Le dossier DotNetFX contient les redistribuables du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Il s'agit de l'intégralité du jeu de fichiers dont vous avez besoin pour déployer votre application sur le Web ou par l'intermédiaire d'un chemin UNC ou d'un CD\/DVD.  
  
## Propriétés de publication  
 Lorsque vous publiez l'application dans le cadre des procédures ci\-dessus, l'Assistant Publication insère les propriétés suivantes dans votre fichier projet.  Ces propriétés influencent directement la manière dont l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est produite.  
  
 Dans CmdLineDemo.vbproj \/ CmdLineDemo.csproj :  
  
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
  
 Vous pouvez substituer chacune de ces propriétés au niveau de la ligne de commande sans modifier le fichier projet proprement dit.  Par exemple, les éléments suivants généreront le déploiement de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sans le programme d'amorçage :  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Les propriétés de publication sont contrôlées dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir des pages de propriétés **Publier**, **Sécurité** et **Signature** du **Concepteur de projets**.  Vous trouverez ci\-dessous une description des propriétés de publication, ainsi qu'une indication de la manière dont chacune peut être définie dans les différentes pages de propriétés du Concepteur d'applications :  
  
-   `AssemblyOriginatorKeyFile` détermine le fichier de clé utilisé pour signer vos manifestes d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cette même clé peut également être utilisée pour assigner un nom fort à vos assemblys.  Cette propriété est définie à la page **Signature** du **Concepteur de projets**.  
  
 Les propriétés suivantes sont définies à la page **Sécurité** :  
  
-   La propriété **Activer les paramètres de sécurité ClickOnce** détermine si les manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont générés.  Lorsqu'un projet est créé, la génération des manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est désactivée par défaut.  L'Assistant active automatiquement cet indicateur lors de votre première publication.  
  
-   La propriété **TargetZone** détermine le niveau de confiance à émettre dans votre manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Les valeurs possibles sont « Internet », « LocalIntranet » et « Custom ».  Internet et LocalIntranet entraînent l'émission d'un jeu d'autorisations par défaut dans votre manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  LocalIntranet est la valeur par défaut et équivaut en fait à une confiance totale.  Custom spécifie que seules les autorisations spécifiées explicitement dans le fichier app.manifest de base doivent être émises dans le manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Le fichier app.manifest est un fichier de manifeste partiel qui contient uniquement les définitions d'informations d'approbation.  Il s'agit d'un fichier masqué, ajouté automatiquement à votre projet lorsque vous configurez des autorisations à la page **Sécurité**.  
  
 Les propriétés suivantes sont définies à la page **Publier** :  
  
-   `PublishUrl` est l'emplacement de publication de l'application dans l'IDE.  Il est inséré dans le manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si les propriétés `InstallUrl` et `UpdateUrl` ne sont pas spécifiées.  
  
-   `ApplicationVersion` spécifie la version de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Il s'agit d'un numéro de version à quatre chiffres.  Si le dernier chiffre est un "\*", la propriété `ApplicationRevision` remplace la valeur insérée dans le manifeste au moment de la génération.  
  
-   `ApplicationRevision` spécifie la révision.  Il s'agit d'un entier incrémenté à chaque publication dans l'IDE.  Notez qu'il n'est pas automatiquement incrémenté pour les générations effectuées au niveau de la ligne de commande.  
  
-   `Install` détermine si l'application est une application installée ou si elle s'exécute à partir du Web.  
  
-   `InstallUrl` \(non affichée\) est l'emplacement à partir duquel les utilisateurs installeront l'application.  Lorsqu'elle est spécifiée, cette valeur est intégrée dans le programme d'amorçage setup.exe si la propriété `IsWebBootstrapper` est activée.  Elle est également insérée dans le manifeste d'application si la propriété `UpdateUrl` n'est pas spécifiée.  
  
-   `SupportUrl` \(non affichée\) est l'emplacement désigné par le lien de la boîte de dialogue **Ajouter ou supprimer des programmes** d'une application installée.  
  
 Les propriétés suivantes sont définies dans la boîte de dialogue **Mises à jour des applications**, accessible à partir de la page **Publier**.  
  
-   `UpdateEnabled` indique si l'application doit rechercher les mises à jour.  
  
-   `UpdateMode` spécifie les mises à jour de premier plan ou les mises à jour d'arrière\-plan.  
  
-   `UpdateInterval` spécifie la fréquence selon laquelle l'application doit rechercher les mises à jour.  
  
-   `UpdateIntervalUnits` indique si la valeur `UpdateInterval` est exprimée en heures, en jours ou en semaines.  
  
-   `UpdateUrl` \(non affichée\) est l'emplacement à partir duquel l'application recevra les mises à jour.  Si elle est spécifiée, cette valeur est insérée dans le manifeste d'application.  
  
-   Les propriétés suivantes sont définies dans la boîte de dialogue **Options de publication**, accessible à partir de la page **Publier**.  
  
-   `PublisherName` spécifie le nom de l'éditeur indiqué dans l'invite qui s'affiche lors de l'installation ou de l'exécution de l'application.  Dans le cas d'une application installée, il est également utilisé pour spécifier le nom du dossier dans le menu **Démarrer**.  
  
-   `ProductName` spécifie le nom du produit indiqué dans l'invite qui s'affiche lors de l'installation ou de l'exécution de l'application.  Dans le cas d'une application installée, il est également utilisé pour spécifier le nom du raccourci dans le menu **Démarrer**.  
  
-   Les propriétés suivantes sont définies dans la boîte de dialogue **Composants requis**, accessible à partir du volet **Publier**.  
  
-   `BootstrapperEnabled` détermine si le programme d'amorçage setup.exe doit être généré.  
  
-   `IsWebBootstrapper` détermine si le programme d'amorçage setup.exe est exécuté à partir du Web ou d'un disque.  
  
## InstallURL, SupportUrl, PublishURL et UpdateURL  
 Le tableau affiche les quatre options d'URL pour le déploiement ClickOnce.  
  
|Option d'URL|Description|  
|------------------|-----------------|  
|`PublishURL`|Obligatoire si vous publiez votre application ClickOnce sur un site Web.|  
|`InstallURL`|Facultatif.  Définissez cette option si le site d'installation est différent de `PublishURL`.  Par exemple, vous pouvez affecter comme valeur à la propriété `PublishURL` un chemin d'accès FTP et à la propriété `InstallURL` une URL Web.|  
|`SupportURL`|Facultatif.  Définissez cette option si le site de prise en charge est différent de `PublishURL`.  Par exemple, vous pouvez affecter à la propriété `SupportURL` la valeur du site Web de support technique de votre société.|  
|`UpdateURL`|Facultatif.  Définissez cette option si l'emplacement de mise à jour est différent de `InstallURL`.  Par exemple, vous pouvez affecter comme valeur à la propriété `PublishURL` un chemin d'accès FTP et à la propriété `UpdateURL` une URL Web.|  
  
## Voir aussi  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)