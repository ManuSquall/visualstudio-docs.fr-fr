---
title: "ClickOnce Security and Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "Windows applications, ClickOnce deployment"
  - "deploying applications [ClickOnce]"
  - "ClickOnce deployment"
  - "publishing, ClickOnce"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Security and Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est une technologie de déploiement qui vous permet de créer des applications Windows de mise à jour automatique qui peuvent être installées et exécutées avec une intervention minimale de l'utilisateur. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] assure la prise en charge complète de la publication et de la mise à jour des applications déployées avec la technologie ClickOnce si vous avez développé vos projets avec Visual Basic et Visual C\#.  Pour plus d'informations sur le déploiement d'applications Visual C\+\+, consultez [Déploiement de ClickOnce pour les applications Visual C\+\+](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 Le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vient à bout de trois problèmes majeurs au niveau du déploiement :  
  
-   **Difficultés liées à la mise à jour des applications.** Avec le déploiement de Microsoft Windows Installer, à chaque fois qu'une application est mise à jour, l'utilisateur peut installer une mise à jour, un fichier msp et l'appliquer au produit installé ; avec le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez fournir des mises à jour automatiquement.  Seules les parties de l'application qui ont changé sont téléchargées, puis, l'application complète, mise à jour est réinstallée à partir d'un nouveau dossier côte à côte.  
  
-   **Impact sur l'ordinateur de l'utilisateur.** Avec un déploiement Windows Installer, les applications dépendent souvent des composants partagés, d'où l'existence d'un risque potentiel de conflit de versions. Dans le cas d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], chaque application est autonome et ne peut pas interférer avec d'autres applications.  
  
-   **Autorisations de sécurité.** Un déploiement Windows Installer exige des autorisations administratives et n'autorise qu'une installation limitée de l'utilisateur ; le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] autorise des utilisateurs dépourvus de privilèges administratifs à effectuer l'installation et n'octroie que ces autorisations de sécurité d'accès du code nécessaires à l'application.  
  
 Par le passé, ces problèmes amenaient parfois les développeurs à décider de créer des applications Web au lieu d'applications Windows, privilégiant ainsi la simplicité d'utilisation plutôt que la richesse de l'interface utilisateur.  Avec les applications déployées à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez bénéficier du meilleur des deux technologies.  
  
## Définition d'une application ClickOnce  
 Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] correspond à toute application Windows Presentation Foundation \(.xbap\), Windows Forms \(.exe\), application console \(.exe\) ou solution Office \(.dll\) publiée à l'aide de la technologie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Vous pouvez publier une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de trois façons différentes : à partir d'une page Web, d'un partage de fichiers réseau ou d'un média tel qu'un CD\-ROM.  Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut être installée sur l'ordinateur d'un utilisateur final et exécutée localement même si l'ordinateur est hors connexion ou elle peut être exécutée uniquement en mode en ligne sans installer aucun élément de façon permanente sur l'ordinateur de l'utilisateur final.  Pour plus d'informations, consultez [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peuvent être se mettre à jour automatiquement ; elles peuvent vérifier l'existence de versions plus récentes dès qu'elles sont disponibles et remplacer automatiquement tous les fichiers mis à jour.  Le développeur peut définir le comportement de mise à jour et un administrateur réseau peut contrôler les stratégies de mise à jour, en marquant, par exemple, une mise à jour comme étant obligatoire.  Les mises à jour peuvent également être annulées et la version antérieure restaurée par l'utilisateur final ou par un administrateur.  Pour plus d'informations, consultez [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Dans la mesure où les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont isolées, l'installation ou l'exécution d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut pas arrêter des applications existantes.  Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont autonomes ; chaque application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est installée sur et exécutée à partir d'un cache par utilisateur, par application sécurisé.  Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont exécutées dans les zones de sécurité Internet ou intranet.  Le cas échéant, l'application peut demander des autorisations de sécurité élevées.  Pour plus d'informations, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Fonctionnement de ClickOnce  
 La sécurité [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] principale est basée sur des certificats, des stratégies de sécurité d'accès du code et l'invite d'approbation ClickOnce.  
  
### Certificats  
 Les certificats Authenticode sont utilisés pour vérifier l'authenticité de l'éditeur de l'application.  En utilisant Authenticode pour le déploiement des applications, ClickOnce permet d'éviter qu'un programme préjudiciable se présente comme un programme légitime provenant d'une source établie et digne de confiance.  Éventuellement, les certificats peuvent également être utilisés pour signer les manifestes de déploiement et d'application afin de prouver que les fichiers n'ont pas été falsifiés.  Pour plus d'informations, consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md).  Les certificats peuvent également être utilisés pour configurer des ordinateurs clients de sorte qu'ils aient une liste d'éditeurs approuvés.  Si une application provient d'un éditeur approuvé, elle peut être installée sans intervention de l'utilisateur.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md).  
  
### Sécurité d'accès du code  
 La sécurité d'accès du code permet de limiter l'accès du code aux ressources protégées.  Dans la plupart des cas, vous pouvez choisir les zones Internet ou intranet local pour limiter les autorisations.  Utilisez la page **Sécurité** dans le **Concepteur de projets** afin de demander la zone appropriée pour l'application.  Vous pouvez également déboguer les applications avec des autorisations restreintes pour émuler l'expérience de l'utilisateur.  Pour plus d'informations, consultez [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### Invite d'approbation ClickOnce  
 Si l'application demande plus d'autorisations que la zone n'en autorise, l'utilisateur final peut être invité à prendre une décision d'approbation.  L'utilisateur final peut décider si l'exécution des applications ClickOnce telles que les applications Windows Forms, les applications Windows Presentation Foundation, les applications console, les applications du navigateur XAML et les solutions Office, est approuvée.  Pour plus d'informations, consultez [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Fonctionnement d'un déploiement ClickOnce  
 L'architecture de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de base repose sur deux fichiers manifeste XML : un manifeste d'application et un manifeste de déploiement.  Les fichiers sont utilisés pour décrire l'emplacement à partir duquel les applications ClickOnce sont installées, la manière dont elles sont mises à jour et le moment où elles le sont.  
  
### Publication d'applications ClickOnce  
 Le manifeste de l'application décrit l'application elle\-même.  Cela comprend les assemblys, les dépendances et les fichiers qui composent l'application, les autorisations requises et l'emplacement dans lequel les mises à jour seront disponibles.  Le développeur d'applications crée le manifeste d'application à l'aide de l'Assistant Publication dans Visual Studio ou de l'Outil Manifest Generation and Editing \(Mage.exe\) dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Pour plus d'informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
 Le manifeste de déploiement décrit comment l'application est déployée.  Cela inclut l'emplacement du manifeste de l'application, et la version de l'application que les clients doivent exécuter.  
  
### Déploiement d'applications ClickOnce  
 Après sa création, le manifeste de déploiement est copié vers l'emplacement de déploiement.  Il peut s'agir d'un serveur Web, d'un partage de fichiers réseau ou de médias tels qu'un CD\-ROM.  Le manifeste d'application et tous les fichiers de l'application sont également copiés vers un emplacement de déploiement spécifié dans le manifeste de déploiement.  Il peut s'agir du même emplacement que celui du déploiement ou d'un autre.  Lors de l'utilisation de l'**Assistant Publication** dans Visual Studio, les opérations de copie sont exécutées automatiquement.  
  
### Installation des applications ClickOnce  
 Après le déploiement de l'application dans l'emplacement de déploiement, les utilisateurs finaux peuvent télécharger et installer l'application en cliquant sur une icône représentant le fichier manifeste de déploiement sur une page Web ou dans un dossier.  Dans la plupart des cas, l'utilisateur final voit s'afficher une simple boîte de dialogue demandant à l'utilisateur de confirmer l'installation, après quoi l'installation continue et l'application est lancée sans autre intervention.  Lorsque l'application requiert des autorisations élevées ou n'est pas signée par un certificat approuvé, la boîte de dialogue demande également à l'utilisateur d'accorder des autorisations pour que l'installation puisse continuer.  Bien que les installations ClickOnce soient effectuées par utilisateur, l'élévation d'autorisations peut être requise si des composants requis nécessitent des privilèges d'administrateur.  Pour plus d'informations sur les autorisations élevées, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Les certificats peuvent être approuvés au niveau de l'ordinateur ou de l'entreprise, afin que les applications ClickOnce signées avec un certificat approuvé puissent s'installer silencieusement.  Pour plus d'informations sur l'utilisation des certificats approuvés, consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md).  
  
 L'application peut être ajoutée au menu **Démarrer** de l'utilisateur et au groupe **Ajout\/Suppression de programmes** du **Panneau de configuration**.  Contrairement aux autres technologies de déploiement, aucun ajout n'est effectué dans le dossier **Program Files** ou le Registre et l'installation ne requiert aucun droit d'administration.  
  
> [!NOTE]
>  Il est également possible d'empêcher l'ajout de l'application au menu **Démarrer** et au groupe **Ajout\/Suppression de programmes**. Elle se comporte, dans ce cas, comme une application Web.  Pour plus d'informations, consultez [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### Mise à jour des applications ClickOnce  
 Lorsque les développeurs d'applications créent une version mise à jour de l'application, ils génèrent un manifeste d'application et copient les fichiers dans un emplacement de déploiement \(en général, un dossier frère du dossier de déploiement d'application d'origine\).  L'administrateur met à jour le manifeste de déploiement pour qu'il pointe vers l'emplacement de la nouvelle version de l'application.  
  
> [!NOTE]
>  L'**Assistant Publication** dans Visual Studio peut être utilisé pour exécuter ces étapes.  
  
 En plus de l'emplacement de déploiement, le manifeste de déploiement contient un emplacement de mise à jour \(une page Web ou un partage de fichiers réseau\) où l'application vérifie les versions mises à jour.  Les propriétés [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**Publish** sont utilisées pour spécifier la date et la fréquence auxquelles l'application doit vérifier les mises à jour.  Le comportement de mise à jour peut être spécifié dans le manifeste de déploiement ou il peut être présenté sous la forme d'un choix d'options utilisateur dans l'interface utilisateur de l'application au moyen des API [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En outre, les propriétés **Publish** peuvent être employées pour configurer la mise à jour obligatoire ou restaurer une version antérieure.  Pour plus d'informations, consultez [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### Programmes d'installation tiers  
 Vous pouvez personnaliser votre programme d'installation ClickOnce pour installer des composants tiers avec votre application.  Vous devez disposer du package redistribuable \(fichier .exe ou .msi\) et décrire le package avec un manifeste de produit indépendant de la langue ainsi qu'un manifeste du package spécifique à la langue.  Pour plus d'informations, consultez [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md).  
  
## Outils ClickOnce  
 Le tableau suivant contient les outils que vous pouvez utiliser pour générer, modifier, signer et signer à nouveau les manifestes de déploiement et d'application.  
  
|Outil|Description|  
|-----------|-----------------|  
|[Page Sécurité, Concepteur de projets](../ide/reference/security-page-project-designer.md)|Signe les manifestes d'application et de déploiement|  
|[Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)|Génère et modifie les manifestes de déploiement et d'application pour les applications Visual Basic et Visual C\#.|  
|[Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Génère les manifestes de déploiement et d'application pour les applications Visual Basic, Visual C\# et Visual C\+\+.<br /><br /> Signe et signe à nouveau les manifestes d'application et de déploiement<br /><br /> Peut être exécuté à partir de scripts de commandes par lot et de l'invite de commandes.|  
|[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|Génère et modifie les manifestes d'application et de déploiement<br /><br /> Signe et signe à nouveau les manifestes d'application et de déploiement|  
|[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)|Génère le manifeste d'application.<br /><br /> Peut être exécuté à partir de MSBuild.  Pour plus d'informations, consultez [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)|Génère le manifeste de déploiement.<br /><br /> Peut être exécuté à partir de MSBuild.  Pour plus d'informations, consultez [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[SignFile Task](../msbuild/signfile-task.md)|Signe les manifestes d'application et de déploiement<br /><br /> Peut être exécuté à partir de MSBuild.  Pour plus d'informations, consultez [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Développez votre propre application pour générer les manifestes de déploiement et d'application.|  
  
 Le tableau suivant indique la version du .NET Framework obligatoire pour prendre en charge les applications ClickOnce dans ces navigateurs.  
  
|Lecteur|Version du .NET Framework|  
|-------------|-------------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## Voir aussi  
 [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Deploying COM Components with ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Building ClickOnce Applications from the Command Line](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debugging ClickOnce Applications That Use System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)