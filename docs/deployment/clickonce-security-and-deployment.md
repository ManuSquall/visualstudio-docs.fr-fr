---
title: Sécurité et déploiement ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88cb136ca4da6f4ca324726edbdaefbd3a27711c
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806945"
---
# <a name="clickonce-security-and-deployment"></a>Sécurité et déploiement ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est une technologie de déploiement qui vous permet de créer des applications Windows à mise à jour automatique qui peuvent être installées et exécutées avec une intervention minimale de l’utilisateur. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit une prise en charge complète de la publication et de la mise à jour des applications déployées avec la technologie ClickOnce C#si vous avez développé vos projets avec Visual Basic et Visual. Pour plus d’informations sur le C++ déploiement d’applications visuelles, consultez [déploiement ClickOnce pour les applications visuelles C++ ](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).

 le déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] passe par trois problèmes majeurs dans le déploiement :

- **Difficultés dans la mise à jour des applications.** Avec Microsoft Windows Installer déploiement, chaque fois qu’une application est mise à jour, l’utilisateur peut installer une mise à jour, un fichier MSP et l’appliquer au produit installé. avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement, vous pouvez fournir des mises à jour automatiquement. Seules les parties de l’application qui ont changé sont téléchargées, puis l’application complète et mise à jour est réinstallée à partir d’un nouveau dossier côte à côte.

- **Impact sur l’ordinateur de l’utilisateur.** Avec le déploiement Windows Installer, les applications s’appuient souvent sur des composants partagés, avec la possibilité de conflits de Versioning. avec le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], chaque application est autonome et ne peut pas interférer avec d’autres applications.

- **Autorisations de sécurité.** Windows Installer déploiement requiert des autorisations d’administration et n’autorise que l’installation utilisateur limitée. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement permet aux utilisateurs non-administrateurs d’installer et d’accorder uniquement les autorisations de sécurité d’accès du code nécessaires pour l’application.

  Par le passé, ces problèmes ont parfois amené les développeurs à décider de créer des applications Web plutôt que des applications Windows, en sacrifiant une interface utilisateur riche pour faciliter l’installation. En utilisant des applications déployées à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez bénéficier du meilleur des deux technologies.

## <a name="what-is-a-clickonce-application"></a>Qu’est-ce qu’une application ClickOnce ?
 Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est un Windows Presentation Foundation ( *. XBAP*), Windows Forms ( *. exe*), une application console ( *. exe*) ou une solution Office ( *. dll*) publiée à l’aide de la technologie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Vous pouvez publier une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de trois façons différentes : à partir d’une page Web, à partir d’un partage de fichiers réseau ou à partir d’un support tel qu’un CD-ROM. Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut être installée sur l’ordinateur d’un utilisateur final et s’exécuter localement, même lorsque l’ordinateur est hors connexion, ou elle peut être exécutée en mode en ligne uniquement sans installer définitivement quoi que ce soit sur l’ordinateur de l’utilisateur final. Pour plus d’informations, consultez [choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peuvent être mises à jour automatiquement ; ils peuvent rechercher les versions plus récentes dès qu’elles sont disponibles et remplacer automatiquement les fichiers mis à jour. Le développeur peut définir le comportement de mise à jour, et un administrateur réseau peut aussi contrôler les stratégies de mise à jour, par exemple en marquant une mise à jour comme étant obligatoire. Les mises à jour peuvent également être restaurées vers une version antérieure par l’utilisateur final ou par un administrateur. Pour plus d’informations, consultez [choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Étant donné que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications sont isolées, l’installation ou l’exécution d’une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut pas interrompre les applications existantes. les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont autonomes ; chaque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est installée et exécutée à partir d’un cache par utilisateur et par application sécurisé. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications s’exécutent dans les zones de sécurité Internet ou intranet. Si nécessaire, l’application peut demander des autorisations de sécurité élevées. Pour plus d’informations, consultez [sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="how-clickonce-security-works"></a>Fonctionnement de la sécurité ClickOnce
 La sécurité de base [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est basée sur les certificats, les stratégies de sécurité d’accès du code et l’invite d’approbation ClickOnce.

### <a name="certificates"></a>Certificats
 Les certificats Authenticode sont utilisés pour vérifier l’authenticité de l’éditeur de l’application. En utilisant Authenticode pour le déploiement d’applications, ClickOnce permet d’éviter qu’un programme dangereux se présente comme un programme légitime provenant d’une source établie et digne de confiance. Vous pouvez également utiliser des certificats pour signer les manifestes d’application et de déploiement afin de prouver que les fichiers n’ont pas été falsifiés. Pour plus d’informations, consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Vous pouvez également utiliser des certificats pour configurer les ordinateurs clients de sorte qu’ils disposent d’une liste d’éditeurs approuvés. Si une application provient d’un éditeur approuvé, elle peut être installée sans intervention de l’utilisateur. Pour plus d’informations, consultez [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).

### <a name="code-access-security"></a>Sécurité d'accès du code
 La sécurité d’accès du code permet de limiter l’accès du code aux ressources protégées. Dans la plupart des cas, vous pouvez choisir les zones Internet ou Intranet local pour limiter les autorisations. Utilisez la page **sécurité** dans **ProjectDesigner** pour demander la zone appropriée pour l’application. Vous pouvez également déboguer des applications avec des autorisations restreintes pour émuler l’expérience de l’utilisateur final. Pour plus d’informations, consultez [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

### <a name="clickonce-trust-prompt"></a>Invite d’approbation ClickOnce
 Si l’application demande plus d’autorisations que la zone ne l’autorise, l’utilisateur final peut être invité à prendre une décision d’approbation. L’utilisateur final peut décider s’il est possible d’exécuter des applications ClickOnce telles que Windows Forms applications, des applications Windows Presentation Foundation, des applications console, des applications de navigateur XAML et des solutions Office. Pour plus d’informations, consultez [Comment : configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="how-clickonce-deployment-works"></a>Fonctionnement du déploiement ClickOnce
 L’architecture de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de base est basée sur deux fichiers manifeste XML : un manifeste d’application et un manifeste de déploiement. Les fichiers sont utilisés pour décrire l’emplacement d’installation des applications ClickOnce, comment elles sont mises à jour et quand elles sont mises à jour.

### <a name="publish-clickonce-applications"></a>Publier des applications ClickOnce
 Le manifeste d’application décrit l’application elle-même. Cela comprend les assemblys, les dépendances et les fichiers qui composent l’application, les autorisations requises et l’emplacement où les mises à jour seront disponibles. Le développeur d’applications crée le manifeste d’application à l’aide de l’Assistant Publication dans Visual Studio ou du Outil Manifest Generation and Editing (*Mage. exe*) dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

 Le manifeste de déploiement décrit la façon dont l’application est déployée. Cela comprend l’emplacement du manifeste d’application et la version de l’application que les clients doivent exécuter.

### <a name="deploy-clickonce-applications"></a>Déployer des applications ClickOnce
 Une fois créé, le manifeste de déploiement est copié à l’emplacement de déploiement. Il peut s’agir d’un serveur web, d’un partage de fichiers réseau ou d’un support comme un CD-ROM. Le manifeste d’application et tous les fichiers d’application sont également copiés vers un emplacement de déploiement spécifié dans le manifeste de déploiement. Il peut s’agir du même emplacement que celui du déploiement ou d’un autre emplacement. Lors de l’utilisation de l' **Assistant Publication** dans Visual Studio, les opérations de copie sont effectuées automatiquement.

### <a name="install-clickonce-applications"></a>Installer des applications ClickOnce
 Une fois déployée sur l’emplacement de déploiement, les utilisateurs finaux peuvent télécharger et installer l’application en cliquant sur une icône représentant le fichier manifeste de déploiement sur une page Web ou dans un dossier. Dans la plupart des cas, l’utilisateur final reçoit une boîte de dialogue simple demandant à l’utilisateur de confirmer l’installation, après quoi l’installation se poursuit et l’application est démarrée sans intervention supplémentaire. Dans les cas où l’application requiert des autorisations élevées ou si l’application n’est pas signée par un certificat approuvé, la boîte de dialogue demande également à l’utilisateur d’accorder l’autorisation pour que l’installation puisse continuer. Bien que les installations ClickOnce soient par utilisateur, l’élévation d’autorisations peut être nécessaire si des conditions préalables requièrent des privilèges d’administrateur. Pour plus d’informations sur les autorisations élevées, consultez [sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).

 Les certificats peuvent être approuvés au niveau de l’ordinateur ou de l’entreprise, de sorte que les applications ClickOnce signées avec un certificat approuvé peuvent s’installer en mode silencieux. Pour plus d’informations sur les certificats approuvés, consultez [vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).

 L’application peut être ajoutée au menu **Démarrer** de l’utilisateur et au groupe **Ajout/suppression de programmes** dans le **panneau de configuration**. Contrairement à d’autres technologies de déploiement, rien n’est ajouté au dossier **Program Files** ou au registre, et aucun droit d’administration n’est requis pour l’installation

> [!NOTE]
> Il est également possible d’empêcher l’application d’être ajoutée au menu **Démarrer** et au groupe **Ajout/suppression de programmes** , en faisant en sorte qu’elle se comporte comme une application Web. Pour plus d’informations, consultez [choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

### <a name="update-clickonce-applications"></a>Mettre à jour les applications ClickOnce
 Lorsque les développeurs d’applications créent une version mise à jour de l’application, ils génèrent un nouveau manifeste d’application et copient les fichiers dans un emplacement de déploiement, généralement un dossier frère dans le dossier de déploiement d’application d’origine. L’administrateur met à jour le manifeste de déploiement pour qu’il pointe vers l’emplacement de la nouvelle version de l’application.

> [!NOTE]
> L' **Assistant Publication** dans Visual Studio peut être utilisé pour effectuer ces étapes.

 En plus de l’emplacement de déploiement, le manifeste de déploiement contient également un emplacement de mise à jour (une page Web ou un partage de fichiers réseau) dans lequel l’application recherche des versions mises à jour. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] propriétés de **publication** sont utilisées pour spécifier quand et à quelle fréquence l’application doit rechercher les mises à jour. Le comportement de mise à jour peut être spécifié dans le manifeste de déploiement, ou il peut être présenté en tant que choix de l’utilisateur dans l’interface utilisateur de l’application au moyen des API [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. En outre, les propriétés **Publish** peuvent être utilisées pour rendre les mises à jour obligatoires ou pour restaurer une version antérieure. Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

### <a name="third-party-installers"></a>Programmes d’installation tiers
 Vous pouvez personnaliser votre programme d’installation ClickOnce pour installer des composants tiers en même temps que votre application. Vous devez disposer du package redistribuable (fichier. exe ou. msi) et décrire le package avec un manifeste de produit indépendant de la langue et un manifeste de package spécifique à une langue. Pour plus d’informations, consultez [création de packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).

## <a name="clickonce-tools"></a>Outils ClickOnce
 Le tableau suivant présente les outils que vous pouvez utiliser pour générer, modifier, signer et signer à nouveau les manifestes d’application et de déploiement.

|Outil|Description|
|----------|-----------------|
|[Page Sécurité, Concepteur de projet](../ide/reference/security-page-project-designer.md)|Signe les manifestes d’application et de déploiement.|
|[Page Publier, Concepteur de projet](../ide/reference/publish-page-project-designer.md)|Génère et modifie les manifestes d’application et de déploiement pour les applications C# Visual Basic et visuelles.|
|[*Mage.exe* (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Génère les manifestes d’application et de déploiement pour les C#applications Visual Basic, C++ visuelles et visuelles.<br /><br /> Signe et signe à nouveau les manifestes d’application et de déploiement.<br /><br /> Peut être exécuté à partir de scripts batch et de l’invite de commandes.|
|[*MageUI.exe* (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Génère et modifie les manifestes d’application et de déploiement.<br /><br /> Signe et signe à nouveau les manifestes d’application et de déploiement.|
|[GenerateApplicationManifest, tâche](../msbuild/generateapplicationmanifest-task.md)|Génère le manifeste de l’application.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md).|
|[Tâche GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Génère le manifeste de déploiement.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md).|
|[SignFile, tâche](../msbuild/signfile-task.md)|Signe les manifestes d’application et de déploiement.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md).|
|[Microsoft. Build. Tasks. Deployment. ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Développez votre propre application pour générer les manifestes d’application et de déploiement.|

 Le tableau suivant indique la version .NET Framework requise pour prendre en charge les applications ClickOnce dans ces navigateurs.

|Visiteur|Version du .NET Framework|
|-------------|----------------------------|
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|
|Firefox|2.0 SP1, 3.5 SP1, 4|

## <a name="see-also"></a>Voir aussi
- [Déploiement ClickOnce sur Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Déployer des composants COM avec ClickOnce](../deployment/deploying-com-components-with-clickonce.md)
- [Générer des applications ClickOnce à partir de la ligne de commande](../deployment/building-clickonce-applications-from-the-command-line.md)
- [Déboguer des applications ClickOnce qui utilisent System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
