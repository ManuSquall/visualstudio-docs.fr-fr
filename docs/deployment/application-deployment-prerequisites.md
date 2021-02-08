---
title: Conditions préalables pour le déploiement d’applications | Microsoft Docs
description: En savoir plus sur les conditions préalables au déploiement pour vos applications, notamment l’utilisation de la boîte de dialogue composants requis et des packages du programme d’amorçage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe8312a4dcaa2efb0b783e89540e5ff9f71f15e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837799"
---
# <a name="application-deployment-prerequisites"></a>Prérequis pour le déploiement d’applications

Pour que votre application soit installée et exécutée correctement, installez d’abord tous les composants dont dépend votre application sur l’ordinateur cible. Par exemple, la plupart des applications créées à l’aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ont une dépendance sur le .NET Framework. Dans ce cas, la version correcte du common language runtime doit être présente sur l’ordinateur de destination avant l’installation de l’application.

 Vous pouvez sélectionner ces composants requis dans la **boîte de dialogue composants requis** et installer le .NET Framework et tout autre redistribuable dans le cadre de votre installation. Cette pratique est connue sous le nom d’*amorçage*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un programme exécutable Windows nommé *Setup.exe*, également appelé *programme d’amorçage*. Le programme d'amorçage effectue l'installation des composants requis avant que votre application ne s'exécute. Pour plus d’informations sur la sélection de ces conditions préalables, consultez [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).

 Chaque composant requis est un package de programme d'amorçage. Un package de programme d’amorçage est un groupe de répertoires et de fichiers contenant les fichiers manifeste qui décrivent comment les composants requis sont installés. Si les prérequis de votre application ne sont pas listés dans la boîte de dialogue **Composants requis**, vous pouvez créer des packages de programme d’amorçage personnalisés, puis les ajouter à Visual Studio. Sélectionnez ensuite les prérequis dans la boîte de dialogue **Composants requis**. Pour plus d’informations, consultez [créer des packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).

 Par défaut, l'amorçage est activé pour le déploiement ClickOnce. Le programme d'amorçage généré pour le déploiement ClickOnce est signé. Vous pouvez désactiver l’amorçage pour un composant, mais uniquement si vous êtes sûr que la version correcte du composant est déjà installée sur tous les ordinateurs cibles.

## <a name="bootstrapping-and-clickonce-deployment"></a>Amorçage et déploiement ClickOnce
 Avant d’installer une application sur un ordinateur client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] examine le client pour s’assurer qu’il possède la configuration requise spécifiée dans le manifeste de l’application. Ces conditions sont les suivantes :

- La version minimale requise du Common Language Runtime, spécifiée en tant que dépendance d'assembly dans le manifeste de l'application.

- La version minimale du système d'exploitation Windows requis par l'application, spécifiée dans le manifeste de l'application via l'élément `<osVersionInfo>` (Consultez l' [ \<dependency> élément](../deployment/dependency-element-clickonce-application.md).)

- Version minimale de tous les assemblys qui doivent être préinstallés dans le Global Assembly Cache (GAC), comme spécifié par les déclarations de dépendance d’assembly dans le manifeste de l’assembly.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut détecter les composants requis manquants et vous pouvez installer les composants requis à l’aide d’un programme d’amorçage. Pour plus d’informations, consultez [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Pour modifier les valeurs dans les manifestes générés par des outils tels que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et *MageUI.exe*, vous devez modifier le manifeste d’application dans un éditeur de texte, puis signer à nouveau les manifestes d’application et de déploiement. Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Si vous utilisez Visual Studio et ClickOnce pour déployer votre application, les packages de programme d'amorçage sélectionnés par défaut dépendent de la version du .NET Framework de la solution. Cependant, si vous changez la version du .NET Framework cible, vous devez mettre à jour manuellement les options de la boîte de dialogue **Composants requis**.

|.NET Framework cible|Packages de programme d'amorçage sélectionnés|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le déploiement, la page *Publish.htm* générée par l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Assistant Publication pointe vers un lien qui installe uniquement l’application ou vers un lien qui installe à la fois l’application et les composants amorcés.

 Si vous générez le programme d’amorçage à l’aide de l’Assistant publication ClickOnce ou de la page publier dans Visual Studio, le *Setup.exe* est signé automatiquement. Toutefois, si vous souhaitez utiliser le certificat de votre client pour signer le programme d'amorçage, vous pouvez signer le fichier plus tard.

## <a name="bootstrapping-and-msbuild"></a>Amorçage et MSBuild
 Si vous n’utilisez pas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , mais que vous compilez plutôt vos applications sur la ligne de commande, vous pouvez créer l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application d’amorçage à l’aide d’une tâche Microsoft Build Engine (MSBuild). Pour plus d’informations, consultez [tâche GenerateBootstrapper,](../msbuild/generatebootstrapper-task.md).

 À la place de l'amorçage, vous pouvez prédéployer les composants à l'aide d'un système électronique de distribution de logiciels, par exemple Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Arguments de ligne de commande du programme d’amorçage (Setup.exe)
 La *Setup.exe* générée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et les tâches MSBuild prend en charge l’ensemble suivant d’arguments de ligne de commande. Tous les autres arguments sont transmis au programme d’installation de l’application.

 Si vous modifiez les options du programme d’amorçage, vous devez modifier le programme d’amorçage non signé, puis signer ultérieurement le fichier du programme d’amorçage.

| Argument de ligne de commande | Description |
| - | - |
| **-?, -h, -help** | Affiche une boîte de dialogue d'aide. |
| **-url, -componentsurl** | Affiche l'URL stockée et l'URL des composants pour cette installation. |
| **-URL =**`location` | Définit l’URL à laquelle *Setup.exe* recherchera l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. |
| **-componentsurl=** `location` | Définit l’URL où *Setup.exe* recherche les dépendances, telles que le .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Lorsque `true` , télécharge les dépendances à partir de l’emplacement préféré sur le site du fournisseur. Ce paramètre remplace le paramètre **-componentsurl** . Lorsque `false` , télécharge les dépendances à partir de l’URL spécifiée par **-componentsurl**. |

## <a name="operating-system-support"></a>Prise en charge du système d’exploitation
 Le programme d’amorçage de Visual Studio n’est pas pris en charge sur Windows Server 2008 Server Core ou Windows Server 2008 R2 Server Core, car ils fournissent un environnement serveur de faible maintenance avec des fonctionnalités limitées. Par exemple, l’option d’installation Server Core ne prend en charge que le profil .NET Framework 3,5 Server Core, qui ne peut pas exécuter les fonctionnalités Visual Studio qui dépendent du .NET Framework complet.

## <a name="see-also"></a>Voir aussi
- [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)