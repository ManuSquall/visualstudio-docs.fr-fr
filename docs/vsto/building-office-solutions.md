---
title: "G&#233;n&#233;ration de solutions Office"
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
  - "déboguer (développement Office dans Visual Studio)"
  - "déboguer des applications Office dans Visual Studio"
  - "solutions (développement Office dans Visual Studio), déboguer"
  - "applications Office (développement Office dans Visual Studio), déboguer"
  - "développement d’applications (développement Office dans Visual Studio), générer"
  - "applications Office (développement Office dans Visual Studio), générer"
  - "projets (développement Office dans Visual Studio), déboguer"
  - "solutions Office (développement Office dans Visual Studio), générer"
  - "solutions (développement Office dans Visual Studio), générer"
  - "projets Office (développement Office dans Visual Studio), déboguer"
  - "projets (développement Office dans Visual Studio), générer"
  - "builds (développement Office dans Visual Studio)"
  - "projets Office (développement Office dans Visual Studio), déboguer"
  - "développement d’applications (développement Office dans Visual Studio), déboguer"
  - "solutions Office (développement Office dans Visual Studio), déboguer"
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# G&#233;n&#233;ration de solutions Office
  En général, la génération et le débogage de projets Office sont identiques à la génération et au débogage d’autres types de projets dans Visual Studio, tels que les Windows Forms. Les rubriques de cette section expliquent les différences qui existent. Pour obtenir des informations générales sur la génération d’applications, consultez [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md).  
  
## Sortie de projet pour les projets Office  
 L’emplacement de sortie pour les projets Office est *nom\_projet*\\bin\\release ou *nom\_projet*\\bin\\debug. Vous ne pouvez pas générer un projet dans un répertoire de déploiement.  
  
### Projets au niveau du document  
 Quand vous générez un projet au niveau du document, les éléments suivants sont inclus dans la sortie du projet :  
  
-   Une copie du document de projet.  
  
-   L’assembly de projet et tous les assemblys référencés dont la propriété **Copie locale** a la valeur **true**.  
  
-   Le manifeste de l’application doté de l’extension de nom de fichier .manifest. Pour plus d'informations, consultez [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Le manifeste de déploiement doté de l’extension de nom de fichier .vsto. Pour plus d'informations, consultez [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un fichier de base de données du programme \(PDB\).  
  
> [!NOTE]  
>  Si vous générez une solution au niveau du document à un emplacement distant et non pas sur l’ordinateur local, ajoutez le chemin complet de la liste des emplacements approuvés dans le Centre de gestion de la confidentialité de l’application. Pour plus d’informations, consultez la section intitulée Octroi de niveaux de confiance à des documents dans [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).  
  
### Projets de niveau application  
 Quand vous générez un projet de complément VSTO, les éléments suivants sont inclus dans la sortie du projet :  
  
-   L’assembly de projet et tous les assemblys référencés dont la propriété **Copie locale** a la valeur **true**.  
  
-   Le manifeste de l’application doté de l’extension de nom de fichier .manifest. Pour plus d'informations, consultez [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Le manifeste de déploiement doté de l’extension de nom de fichier .vsto. Pour plus d'informations, consultez [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un fichier de base de données du programme \(PDB\) pour l’assembly du projet.  
  
 Le processus de génération pour les projets de complément VSTO crée également un jeu d’entrées du Registre sur l’ordinateur de développement, qui sont requises pour charger le complément VSTO. Pour plus d'informations, consultez [Entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Si vous générez un projet de complément VSTO Outlook qui contient des zones de formulaire, le processus de génération ajoute les informations supplémentaires suivantes dans le Registre :  
  
-   une clé pour chaque classe de message associée à une ou plusieurs zones de formulaire,  
  
-   une entrée pour chaque zone de formulaire et une valeur associée représentant le nom du complément VSTO Outlook.  
  
 Outlook a besoin de ces informations pour charger les zones de formulaire.  
  
## Assemblys référencés  
 Vous pouvez référencer des assemblys \(y compris des projets de bibliothèque de classes\) à partir de votre projet de génération de solutions Office. Chaque assembly référencé possède une propriété appelée **Copie locale**. Cette propriété indique si l’assembly doit être copié dans le répertoire de sortie. Elle a la valeur **true** par défaut. Chaque assembly référencé dont la propriété **Copie locale** a la valeur **true** est copié dans le répertoire de sortie.  
  
## Sécurité pendant le processus de génération  
 Visual Studio configure automatiquement les paramètres de sécurité sur l’ordinateur de développement afin d’accorder un niveau de confiance à la solution pendant le processus de génération. Cela permet d’exécuter la solution pendant que vous la déboguez.  
  
 Les projets Office utilisent des certificats pour vérifier l’éditeur. Visual Studio crée automatiquement un certificat temporaire pour identifier les solutions Office et configure l’ordinateur de développement pour approuver ce certificat.  
  
 Pour plus d'informations, consultez [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).  
  
### Projets en réseau  
 Si l’assembly ou le document se trouve sur un partage réseau, la mise à jour de la stratégie de sécurité locale \(niveau utilisateur\) ne suffit pas pour permettre à la solution de s’exécuter. Un administrateur doit accorder une confiance totale au niveau de l’ordinateur aux assemblys et documents situés sur un partage réseau avant que la solution ne s’exécute. Pour plus d’informations sur la façon de définir la stratégie de sécurité, consultez [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).  
  
 Pour les projets au niveau du document, vous devez également ajouter l’emplacement complet du document dans la liste des dossiers approuvés d’Office. Pour plus d'informations, consultez [Octroi de niveaux de confiance à des documents](../vsto/granting-trust-to-documents.md).  
  
## Modification de la plateforme cible  
 Par défaut, la plateforme cible pour les projets Office est **Any CPU**. En règle générale, vous ne devez pas modifier ce paramètre. Les solutions Office générées avec le paramètre de plateforme cible **Any CPU** s’exécutent dans les versions 32 bits et 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Vous devez spécifier la plateforme cible x64 seulement si vous créez une solution destinée à s’exécuter uniquement dans les versions 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], et que votre solution appelle des API 64 bits natives. Pour plus d’informations sur la modification du paramètre de plateforme cible, consultez [NIB : Comment : optimiser une application pour un type d’UC spécifique](http://msdn.microsoft.com/fr-fr/294a75d2-4279-4b72-8298-2bea05be907a).  
  
 Si vous spécifiez la plateforme cible x64, la solution ne s’exécutera pas dans les versions 32 bits de Windows et Office. La plateforme cible x64 exige que la solution s’exécute dans un processus 64 bits.  
  
## Utilisation de la commande Nettoyer  
 Pour supprimer les fichiers projet générés de l’ordinateur de développement, vous pouvez utiliser la commande **Nettoyer** du menu **Générer** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. La commande **Nettoyer** supprime tous les fichiers de l’emplacement de sortie de la génération. Pour les projets de niveau application, la commande **Nettoyer** supprime également les entrées de Registre créées par le processus de génération.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Débogage de projets Office](../vsto/debugging-office-projects.md)|Présente des problèmes liés au débogage de projets Office.|  
|[Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Montre comment créer une personnalisation de base au niveau du document pour Excel.|  
|[Comment : réactiver un complément VSTO qui a été désactivé](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Décrit comment réactiver un complément VSTO qui a été désactivé de manière forcée ou en douceur.|  
|[Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)|Fournit des liens vers des informations concernant la création de solutions Office et le rôle des assemblys dans ces solutions.|  
  
  