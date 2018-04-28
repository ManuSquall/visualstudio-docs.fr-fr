---
title: Création de Solutions Office | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 825e9bae6651848d161898ef9436fa27d9b60d90
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="building-office-solutions"></a>Génération de solutions Office
  En général, la génération et le débogage de projets Office sont identiques à la génération et au débogage d’autres types de projets dans Visual Studio, tels que les Windows Forms. Les rubriques de cette section expliquent les différences qui existent. Pour obtenir des informations générales sur la façon de créer des applications, consultez [compilation et génération dans Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
## <a name="project-output-for-office-projects"></a>Sortie de projet pour les projets Office  
 L’emplacement de sortie pour les projets Office est *nom_projet*\bin\release ou *nom_projet*\bin\debug. Vous ne pouvez pas générer un projet dans un répertoire de déploiement.  
  
### <a name="document-level-projects"></a>Projets au niveau du document  
 Quand vous générez un projet au niveau du document, les éléments suivants sont inclus dans la sortie du projet :  
  
-   Une copie du document de projet.  
  
-   L’assembly de projet et tous les assemblys référencés dont la propriété **Copie locale** a la valeur **true**.  
  
-   Le manifeste de l’application doté de l’extension de nom de fichier .manifest. Pour plus d'informations, consultez [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
-   Le manifeste de déploiement doté de l’extension de nom de fichier .vsto. Pour plus d'informations, consultez [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un fichier de base de données du programme (PDB).  
  
> [!NOTE]  
>  Si vous générez une solution au niveau du document à un emplacement distant et non pas sur l’ordinateur local, ajoutez le chemin complet de la liste des emplacements approuvés dans le Centre de gestion de la confidentialité de l’application. Pour plus d’informations, consultez la section intitulée Octroi de niveaux de confiance à des documents dans [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Projets de niveau application  
 Quand vous générez un projet de complément VSTO, les éléments suivants sont inclus dans la sortie du projet :  
  
-   L’assembly de projet et tous les assemblys référencés dont la propriété **Copie locale** a la valeur **true**.  
  
-   Le manifeste de l’application doté de l’extension de nom de fichier .manifest. Pour plus d'informations, consultez [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
-   Le manifeste de déploiement doté de l’extension de nom de fichier .vsto. Pour plus d'informations, consultez [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un fichier de base de données du programme (PDB) pour l’assembly du projet.  
  
 Le processus de génération pour les projets de complément VSTO crée également un jeu d’entrées du Registre sur l’ordinateur de développement, qui sont requises pour charger le complément VSTO. Pour plus d'informations, consultez [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Si vous générez un projet de complément VSTO Outlook qui contient des zones de formulaire, le processus de génération ajoute les informations supplémentaires suivantes dans le Registre :  
  
-   une clé pour chaque classe de message associée à une ou plusieurs zones de formulaire,  
  
-   une entrée pour chaque zone de formulaire et une valeur associée représentant le nom du complément VSTO Outlook.  
  
 Outlook a besoin de ces informations pour charger les zones de formulaire.  
  
## <a name="referenced-assemblies"></a>Assemblys référencés  
 Vous pouvez référencer des assemblys (y compris des projets de bibliothèque de classes) à partir de votre projet de génération de solutions Office. Chaque assembly référencé possède une propriété appelée **Copie locale**. **Copie locale** indique si l’assembly est copié vers le répertoire de sortie. Elle a la valeur **true**par défaut. Chaque assembly référencé dont la propriété **Copie locale** a la valeur **true** est copié dans le répertoire de sortie.  
  
## <a name="security-during-the-build-process"></a>Sécurité pendant le processus de génération  
 Visual Studio configure automatiquement les paramètres de sécurité sur l’ordinateur de développement afin d’accorder un niveau de confiance à la solution pendant le processus de génération. Cela permet d’exécuter la solution pendant que vous la déboguez.  
  
 Les projets Office utilisent des certificats pour vérifier l’éditeur. Visual Studio crée automatiquement un certificat temporaire pour identifier les solutions Office et configure l’ordinateur de développement pour approuver ce certificat.  
  
 Pour plus d'informations, consultez [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Projets en réseau  
 Si l’assembly ou le document se trouve sur un partage réseau, la mise à jour de la stratégie de sécurité locale (niveau utilisateur) ne suffit pas pour permettre à la solution de s’exécuter. Un administrateur doit accorder une confiance totale au niveau de l’ordinateur aux assemblys et documents situés sur un partage réseau avant que la solution ne s’exécute. Pour plus d’informations sur la façon de définir la stratégie de sécurité, consultez [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
 Pour les projets au niveau du document, vous devez également ajouter l’emplacement complet du document dans la liste des dossiers approuvés d’Office. Pour plus d'informations, consultez [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
## <a name="changing-the-platform-target"></a>Modification de la plateforme cible  
 Par défaut, la plateforme cible pour les projets Office est **Any CPU**. En règle générale, vous ne devez pas modifier ce paramètre. Les solutions Office générées avec le paramètre de plateforme cible **Any CPU** s’exécutent dans les versions 32 bits et 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Vous devez spécifier la plateforme cible x64 seulement si vous créez une solution destinée à s’exécuter uniquement dans les versions 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], et que votre solution appelle des API 64 bits natives. Pour plus d’informations sur la modification du paramètre de la plateforme cible, consultez [Comment : configurer des projets pour des plateformes cibles](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Si vous spécifiez la plateforme cible x64, la solution ne s’exécutera pas dans les versions 32 bits de Windows et Office. La plateforme cible x64 exige que la solution s’exécute dans un processus 64 bits.  
  
## <a name="using-the-clean-command"></a>Utilisation de la commande Nettoyer  
 Pour supprimer les fichiers projet générés de l’ordinateur de développement, vous pouvez utiliser la commande **Nettoyer** du menu **Générer** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. La commande **Nettoyer** supprime tous les fichiers de l’emplacement de sortie de la génération. Pour les projets de niveau application, la commande **Nettoyer** supprime également les entrées de Registre créées par le processus de génération.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Débogage de projets Office](../vsto/debugging-office-projects.md)|Présente des problèmes liés au débogage de projets Office.|  
|[Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Montre comment créer une personnalisation de base au niveau du document pour Excel.|  
|[Guide pratique pour réactiver un complément VSTO qui a été désactivé](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Décrit comment réactiver un complément VSTO qui a été désactivé de manière forcée ou en douceur.|  
|[Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)|Fournit des liens vers des informations concernant la création de solutions Office et le rôle des assemblys dans ces solutions.|  
  
  