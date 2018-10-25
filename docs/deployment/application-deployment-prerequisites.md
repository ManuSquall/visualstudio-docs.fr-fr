---
title: Conditions préalables au déploiement de application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 421092218cdeb889fe195917e46b123c73e7e1f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851801"
---
# <a name="application-deployment-prerequisites"></a>Conditions préalables au déploiement de application

Pour que votre application pour installer et exécuter avec succès, d’abord installer tous les composants dont votre application dépend sur l’ordinateur cible. Par exemple, la plupart des applications créées à l’aide [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ont une dépendance sur le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Dans ce cas, la version correcte du common language runtime doit être présente sur l’ordinateur de destination avant que l’application est installée.  

 Vous pouvez sélectionner ces conditions préalables dans le **Prerequisites Dialog Box** et installer le .NET Framework et n’importe quel autre package redistribuable dans le cadre de votre installation. Cette pratique est appelée *amorçage*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un programme exécutable Windows nommé *Setup.exe*, également appelé un *programme d’amorçage*. Le programme d'amorçage effectue l'installation des composants requis avant que votre application ne s'exécute. Pour plus d’informations sur la sélection de ces conditions préalables, consultez [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).  

 Chaque composant requis est un package de programme d'amorçage. Un package de programme d’amorçage est un groupe de répertoires et fichiers qui contient les fichiers manifestes qui décrivent comment les composants requis sont installés. Si vos composants requis d’application ne sont pas répertoriés dans le **boîte de dialogue prérequis**, vous pouvez créer des packages de programme d’amorçage personnalisé et les ajouter à Visual Studio. Vous pouvez ensuite sélectionner les conditions préalables dans le **Prerequisites Dialog Box**. Pour plus d’informations, consultez [créer des packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  

 Par défaut, l'amorçage est activé pour le déploiement ClickOnce. Le programme d'amorçage généré pour le déploiement ClickOnce est signé. Vous pouvez désactiver l’amorçage d’un composant, mais uniquement si vous êtes sûr que la version correcte du composant est déjà installée sur tous les ordinateurs cibles.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Amorçage et le déploiement ClickOnce  
 Avant d’installer une application sur un ordinateur client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] examine le client pour vous assurer qu’il a des exigences spécifiées dans le manifeste d’application. Citons notamment les conditions suivantes :  

- La version minimale requise du Common Language Runtime, spécifiée en tant que dépendance d'assembly dans le manifeste de l'application.  

- La version minimale du système d'exploitation Windows requis par l'application, spécifiée dans le manifeste de l'application via l'élément `<osVersionInfo>` (Consultez [ \<dépendance > élément](../deployment/dependency-element-clickonce-application.md).)  

- La version minimale de tous les assemblys qui doivent être préinstallés dans le global assembly cache (GAC), tel que spécifié par les déclarations de dépendance d’assembly dans le manifeste d’assembly.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut détecter les composants requis manquants, et vous pouvez installer les conditions préalables à l’aide d’un programme d’amorçage. Pour plus d’informations, consultez [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Pour modifier les valeurs dans les manifestes générés par des outils tels que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et *MageUI.exe*, vous devez modifier le manifeste d’application dans un éditeur de texte et signer à nouveau les manifestes d’application et de déploiement. Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Si vous utilisez Visual Studio et ClickOnce pour déployer votre application, les packages de programme d'amorçage sélectionnés par défaut dépendent de la version du .NET Framework de la solution. Toutefois, si vous modifiez la version cible du .NET Framework, vous devez mettre à jour les options dans le **Prerequisites Dialog Box** manuellement.  

|.NET Framework cible|Packages de programme d'amorçage sélectionnés|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  

 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement, le *Publish.htm* page générée par le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Assistant Publication pointe vers un lien qui installe uniquement l’application ou à un lien qui installe l’application et l’amorçage composants.  

 Si vous générez le programme d’amorçage à l’aide de l’Assistant Publication de ClickOnce ou de la Page Publier dans Visual Studio, le *Setup.exe* est automatiquement connecté. Toutefois, si vous souhaitez utiliser le certificat de votre client pour signer le programme d'amorçage, vous pouvez signer le fichier plus tard.  

## <a name="bootstrapping-and-msbuild"></a>Amorçage et MSBuild  
 Si vous n’utilisez pas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mais plutôt de compiler vos applications sur la ligne de commande, vous pouvez créer le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application d’amorçage à l’aide d’une tâche Microsoft Build Engine (MSBuild). Pour plus d’informations, consultez [GenerateBootstrapper, tâche](../msbuild/generatebootstrapper-task.md).  

 À la place de l'amorçage, vous pouvez prédéployer les composants à l'aide d'un système électronique de distribution de logiciels, par exemple Microsoft Systems Management Server (SMS).  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Arguments de ligne de commande du programme d’amorçage (Setup.exe)  
 Le *Setup.exe* généré par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et les tâches MSBuild prend en charge l’ensemble suivant d’arguments de ligne de commande. Tous les autres arguments sont transmis au programme d’installation de l’application.  

 Si vous modifiez les options du programme d’amorçage, vous devez modifier le programme d’amorçage non signé et puis reconnectez-vous ultérieurement le fichier de programme d’amorçage.  


| Argument de ligne de commande | Description |
| - | - |
| **- ?, -h, - aide** | Affiche une boîte de dialogue d'aide. |
| **-url, - componentsurl** | Affiche l'URL stockée et l'URL des composants pour cette installation. |
| **-url =** `location` | Définit l’URL où *Setup.exe* recherchera le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. |
| **-componentsurl =** `location` | Définit l’URL où *Setup.exe* recherchera les dépendances, telles que le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite =** `true`**&#124;** `false` | Lorsque `true`, télécharge les dépendances à partir de l’emplacement par défaut sur le site du fournisseur. Ce paramètre remplace le **- componentsurl** paramètre. Lorsque `false`, télécharge les dépendances à partir de l’URL spécifiée par **- componentsurl**. |

## <a name="operating-system-support"></a>Système d'exploitation pris en charge  
 Le programme d’amorçage de Visual Studio n’est pas pris en charge sur Server Core de Windows Server 2008 ou Windows Server 2008 R2 Server Core, car elles fournissent un environnement serveur à faible maintenance avec des fonctionnalités limitées. Par exemple, l’option d’installation Server Core prend uniquement en charge le profil .NET Framework 3.5 Server Core, qui ne peut pas exécuter les fonctionnalités de Visual Studio qui dépendent du .NET Framework.  

## <a name="see-also"></a>Voir aussi  
 [Choisissez une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)