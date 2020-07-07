---
title: Génération et débogage de solutions SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016366"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Générer et déboguer des solutions SharePoint
  En général, la génération et le débogage de solutions SharePoint sont les mêmes que pour la génération et le débogage d’autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Les rubriques de cette section expliquent les différences qui existent.

## <a name="project-output-for-sharepoint-solutions"></a>Sortie de projet pour les solutions SharePoint
 La création de solutions SharePoint crée des assemblys et un fichier de package de solution (*. wsp*). Le tableau suivant indique les emplacements de ces fichiers pendant une génération.

|Élément de build|Dossier de sortie|
|----------------|-------------------|
|Les fichiers d’assembly, de base de données de programme (*. pdb*) et *. wsp* .|* \<ProjectName> \bin\Debug* ou * \<ProjectName> \bin\release*|
|Fichiers d’éléments de projet SharePoint.|* \<ProjectName> \pkg\debug* ou * \<ProjectName> \pkg\release*|
|Générez des fichiers intermédiaires.|* \<ProjectName> \obj\debug* ou * \<ProjectName> \obj\release*|
|Fichiers intermédiaires du package.|* \<ProjectName> \pkgobj\debug* ou * \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Créer des solutions SharePoint
 Pour générer des solutions SharePoint, la version appropriée de SharePoint Server doit être installée sur l’ordinateur de développement. Dans le cas contraire, la génération de solutions SharePoint est identique à la génération d’autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour plus d’informations, consultez [Comment : générer des solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Déboguer et tester des solutions SharePoint
 Avant le débogage, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie le package *. wsp* sur le serveur SharePoint, active les fonctionnalités du site et de l’étendue du Web et, dans certains cas, démarre le projet. Dans d’autres cas, vous devrez peut-être ouvrir le projet manuellement. Pour plus d’informations, consultez [dépanner des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) et [Déboguer des solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Déboguer et vérifier des solutions SharePoint à l’aide des fonctionnalités de Azure DevOps Services
 Azure DevOps Services des fonctionnalités telles que les tests unitaires et IntelliTrace vous permettent d’identifier plus précisément les problèmes dans vos solutions SharePoint. Le profilage vous permet de localiser et d’identifier les zones à problème de performances dans vos solutions SharePoint. Pour plus d’informations, consultez [vérification et débogage du code SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) et [profilage des performances des applications SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sécurité pendant le processus de génération
 Pour empaqueter ou déployer des solutions SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] doit avoir l’autorisation de copier des fichiers sur le serveur SharePoint. Vous devez exécuter [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant que processus avec élévation de privilèges et votre compte d’utilisateur doit être un administrateur de collections de sites sur le serveur SharePoint. En outre, vous devez spécifier si votre projet est une solution bac à sable (sandbox) ou une solution de batterie de serveurs. Pour plus d’informations, consultez [différences entre les solutions sandbox et les solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Utilisation de la commande Clean
 Quand une solution SharePoint est installée sur un serveur SharePoint pour le débogage, la commande **nettoyer** ne désinstalle pas la solution. Au lieu de cela, vous devez désactiver les fonctionnalités par le biais de la configuration SharePoint.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Parcourir les connexions SharePoint à l’aide de Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
