---
title: Génération et débogage de Solutions SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e91c1433fde85a9ec828a6a018bee986fdc7aa5c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623760"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Générer et déboguer des solutions SharePoint
  En règle générale, la génération et débogage de solutions SharePoint sont le même que pour les autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Les rubriques de cette section expliquent les différences qui existent.

## <a name="project-output-for-sharepoint-solutions"></a>Sortie du projet pour les solutions SharePoint
 Génération de solutions SharePoint crée des assemblys et un package de solution (*.wsp*) fichier. Le tableau suivant présente les emplacements de ces fichiers pendant une génération.

|Générer l’élément|Dossier de sortie|
|----------------|-------------------|
|Assembly, de la base de données de programme (*.pdb*), et *.wsp* fichiers.|*\<NomProjet > \bin\debug* ou  *\<nom_projet > \bin\release*|
|Fichiers élément de projet SharePoint.|*\<Nom du projet > \pkg\debug* ou  *\<nom_projet > \pkg\release*|
|Générer des fichiers intermédiaires.|*\<Nom du projet > \obj\debug* ou  *\<nom_projet > \obj\release*|
|Empaqueter des fichiers intermédiaires.|*\<Nom du projet > \pkgobj\debug* ou  *\<nom_projet > \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Créer des solutions SharePoint
 Pour créer des solutions SharePoint, l’ordinateur de développement doit avoir la version appropriée de SharePoint server est installé. Sinon, la génération de solutions SharePoint est identique à la génération d’autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d'informations, voir [Procédure : Créer des solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Déboguer et tester des solutions SharePoint
 Avant le débogage, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copies le *.wsp* package sur le serveur SharePoint, Active les fonctionnalités relatives aux applications Web et au Site et dans certains cas, démarre le projet. Dans d’autres cas, vous devrez peut-être ouvrir le projet manuellement. Pour plus d’informations, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md) et [solutions SharePoint déboguer](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Déboguer et vérifier des solutions SharePoint à l’aide des fonctionnalités des Services de DevOps Azure
 Les fonctionnalités DevOps Services Azure tels que les tests unitaires et d’IntelliTrace vous permettent plus précisément les problèmes dans vos solutions SharePoint. Le profilage vous permet de localiser et identifier les zones de problèmes de performances dans vos solutions SharePoint. Pour plus d’informations, consultez [vérification et débogage du SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) et [profilage des performances des Applications SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sécurité pendant le processus de génération
 Pour empaqueter ou déployer des solutions SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] doit avoir l’autorisation de copier des fichiers sur le serveur SharePoint. Vous devez exécuter [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comme un processus avec élévation de privilèges et d’utilisateur de votre compte doit être un administrateur de Collections de sites sur le serveur SharePoint. En outre, vous devez spécifier si votre projet est une solution bac à sable ou une solution de batterie de serveurs. Pour plus d’informations, consultez [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>À l’aide de la commande Clean
 Lorsqu’une solution SharePoint est installée sur un serveur SharePoint pour le débogage, le **Clean** commande ne désinstalle pas la solution. Au lieu de cela, vous devez désactiver les fonctionnalités via la configuration de SharePoint.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Parcourir les connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
