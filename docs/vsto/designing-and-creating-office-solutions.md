---
title: "Conception et cr&#233;ation de solutions Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement Office dans Visual Studio, créer des solutions"
  - "types de projets Office dans Visual Studio"
  - "solutions Office (développement Office dans Visual Studio), créer"
  - "solutions (développement Office dans Visual Studio), créer"
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: 103
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 99
---
# Conception et cr&#233;ation de solutions Office
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer différents types de solutions Office.  Cette section de la documentation décrit les modèles de projet et apporte des conseils sur la création de projets Office.  Pour plus d'informations sur l'implémentation de code et de personnalisations d'interface utilisateur après la création de votre projet, consultez [Développement de solutions Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Création de projets Office  
 Avant de commencer, vous devez déterminer vos besoins et choisir le type de solution qui convient le mieux.  Par exemple, si votre solution Office doit s'exécuter chaque fois que l'application est utilisée, un complément VSTO correspond mieux à vos critères.  Si le code est étroitement intégré à un document unique, créez une personnalisation au niveau du document.  Ces types de projets sont disponibles sous forme de modèles de projet Visual Studio.  Pour plus d'informations sur les modèles de projet Office inclus dans Visual Studio, consultez [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  Pour plus d'informations sur la création de projets Office, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Certaines fonctionnalités et certains éléments des projets Office diffèrent des autres types de projets dans Visual Studio.  Par exemple, quand vous créez un projet au niveau du document, le document ou le classeur de votre projet peut être ouvert et modifié depuis Visual Studio.  Pour plus d'informations, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Choix d'une version du .NET Framework  
 Après avoir sélectionné le type de projet qui répond le mieux à vos besoins, vous pouvez choisir la version du .NET Framework utiliser dans votre processus de développement.  Vous pouvez cibler les versions du .NET Framework suivantes dans les projets Office :  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 La version du .NET Framework que vous choisissez pour votre projet doit être installée sur les ordinateurs des utilisateurs finaux pour que votre solution puisse fonctionner.  Par exemple, si votre projet cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] doit être installé sur les ordinateurs des utilisateurs finaux.  Dans cet exemple, votre solution ne fonctionnera pas si seul le .NET Framework 3.5 est installé sur les ordinateurs des utilisateurs finaux.  
  
 Si vous migrez un projet de complément VSTO qui cible le .NET Framework 3.5, Visual Studio remplace la version cible du .NET Framework de votre projet par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieur en fonction de la version d'Office installée.  
  
 Toutefois, après le changement de la version cible du .NET Framework par Visual Studio, vous devrez peut\-être modifier une partie du code de votre projet s'il utilise certaines fonctionnalités.  Pour plus d'informations sur le changement de la version cible du .NET Framework, consultez [Comment : cibler une version du .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  Pour plus d'informations sur les modifications que vous devez éventuellement apporter dans votre projet, consultez [Migration de solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si Visual Studio modifie la version cible du .NET Framework pour votre projet et que vous utilisez ClickOnce pour déployer votre solution, assurez\-vous que vous sélectionnez également la version correspondante du .NET Framework dans la boîte de dialogue **Configuration requise**.  Cette sélection ne change pas automatiquement quand vous modifiez la version cible du .NET Framework pour votre projet.  Pour plus d'informations, consultez [Comment : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](http://msdn.microsoft.com/fr-fr/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Vous ne pouvez pas cibler le .NET Framework 3.5 ou version antérieure dans les projets Office créés à l'aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  Les projets Office créés à l'aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nécessitent les fonctionnalités introduites dans le [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].  
  
### Quand les assemblys PIA Office sont\-ils nécessaires sur les ordinateurs des utilisateurs finaux ?  
 Par défaut, les assemblys PIA \(Primary Interop Assembly\) Office n'ont pas besoin d'être installés sur les ordinateurs des utilisateurs finaux si la propriété **Incorporer les types d'interopérabilité** de chaque référence d'assembly PIA Office dans le projet a la valeur **True**, qui est la valeur par défaut.  Dans ce scénario, les informations relatives aux types PIA utilisés par votre solution sont incorporées dans l'assembly de solution au moment de la génération du projet.  Au moment de l'exécution, les informations de type incorporées sont utilisées au lieu des assemblys PIA pour exécuter un appel dans le modèle objet COM de l'application Office.  Pour plus d'informations sur la manière dont les types d'assemblys PIA sont incorporés dans votre solution, consultez [Type Equivalence and Embedded Interop Types](http://msdn.microsoft.com/library/78892eba-2a58-4165-b4b1-0250ee2f41dc).  
  
 Si la propriété **Incorporer les types d'interopérabilité** de chaque référence d'assembly PIA dans le projet a la valeur **False**, des assemblys PIA Office doivent être installés et inscrits dans le Global Assembly Cache sur chaque ordinateur d'utilisateur final qui exécute la solution.  Dans la plupart des cas, les assemblys PIA sont installés par défaut avec Office, mais vous pouvez également inclure le composant redistribuable de l'assembly PIA comme composant requis pour votre solution.  Pour plus d'informations, consultez [Composants requis pour les solutions Office en vue du déploiement](http://msdn.microsoft.com/fr-fr/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### Présentation du profil client  
 Le .NET Framework Client Profile est un sous\-ensemble du .NET Framework complet.  Vous pouvez cibler le .NET Framework Client Profile si vous devez utiliser uniquement les fonctionnalités client du .NET Framework et souhaitez fournir le déploiement le plus rapide possible pour votre solution Office.  Pour plus d'informations, consultez [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
 Quand vous créez un projet Office qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], le [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] est ciblé par défaut. Si vous souhaitez développer pour la version complète du [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], vous devez définir cette option après la création du projet.  Pour plus d'informations, consultez [Comment : cibler une version du .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Création de solutions pour l'édition 64 bits de Microsoft Office  
 Microsoft Office est disponibles dans les éditions 64 bits et 32 bits.  Pour créer des solutions Office qui peuvent s'exécuter dans les deux éditions, le paramètre de plateforme cible de votre projet doit avoir la valeur **Any CPU**.  Il s'agit de la valeur par défaut pour les projets Office. Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
 Il existe des versions 64 bits et 32 bits distinctes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui sont utilisées par les éditions 64 bits et 32 bits de Microsoft Office.  Pour plus d'informations, consultez [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Assemblys dans les solutions Office  
 Quand vous créez un projet Office à l'aide des Outils de développement Office dans Visual Studio, le code que vous écrivez est en fin de compte compilé dans un assembly.  L'assembly est généralement déployé vers un serveur partagé ou un répertoire sur l'ordinateur client.  
  
 Les assemblys dans les solutions Office sont chargés par une application Office.  Une fois l'assembly chargé, le code dans l'assembly peut répondre aux événements déclenchés dans l'application, par exemple quand un utilisateur clique sur un élément de menu.  Le code dans l'assembly peut également exécuter un appel dans le modèle objet pour automatiser et étendre l'application, et il peut utiliser toutes les classes du [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Pour plus d'informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md) et [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
 Les solutions Office utilisent des manifestes de déploiement et des manifestes d'application pour identifier l'assembly.  Les manifestes contiennent des informations sur le nom, la version et l'emplacement de l'assembly pour que l'application puisse trouver l'assembly approprié, créer un lien vers celui\-ci et l'exécuter.  Pour plus d'informations, consultez [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Les projets au niveau du document incluent un document en plus d'un assembly.  Le document constitue la partie frontale de l'application et concentre l'ensemble des interactions avec l'utilisateur.  Chaque document ne peut être associé qu'à un seul assembly de projet principal ; cependant, plusieurs documents peuvent pointer vers le même assembly.  
  
 Les assemblys des projets au niveau du document ne sont pas incorporés au document ; ils sont en fait stockés ailleurs et sont identifiés par le manifeste d'application du document.  
  
## Considérations sur la sécurité des assemblys  
 Pour qu'une solution Office s'exécute sur un ordinateur, les assemblys utilisés par la solution doivent être approuvés pour exécution.  Pour plus d'informations sur la sécurité, consultez [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).  
  
 Par défaut, l'assembly de solution et tous les assemblys référencés qui figurent dans le dossier de sortie de votre projet sont approuvés pour exécution sur l'ordinateur de développement quand vous générez le projet.  Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
 Pour des raisons de sécurité, il est préférable de créer les projets sur votre ordinateur local, au lieu d'effectuer le développement dans un emplacement partagé.  Pour plus d'informations, consultez [Développement collaboratif de solutions Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## Assemblys référencés  
 L'assembly peut référencer d'autres assemblys répertoriés dans les références du projet.  Toutefois, un assembly de projet au niveau du document ne peut pas en référencer un autre.  
  
## Voir aussi  
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md)   
 [Exécution de solutions dans différentes versions de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Comment : cibler les applications Office via les assemblys PIA &#40;Primary Interop Assembly&#41;](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Comment : configurer les informations de configuration d'une solution Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Utilisation de fonctionnalités Office dans Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md)   
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  