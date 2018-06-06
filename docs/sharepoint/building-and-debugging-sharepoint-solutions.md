---
title: Génération et débogage de Solutions SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d0bc3185b0684f96bf31cc127cd852448afe772
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765068"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Générer et déboguer des solutions SharePoint
  En général, la génération et débogage de solutions SharePoint sont le même que pour les autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Les rubriques de cette section expliquent les différences qui existent.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Sortie du projet pour les solutions SharePoint
 Génération de solutions SharePoint crée des assemblys et un package de solution (*.wsp*) fichier. Le tableau suivant présente les emplacements de ces fichiers lors d’une génération.  
  
|Générer l’élément|Dossier de sortie|  
|----------------|-------------------|  
|Assembly, la base de données de programme (*.pdb*), et *.wsp* fichiers.|*{ProjectName} \bin\debug* ou *{ProjectName} \bin\release*|  
|Fichiers élément de projet SharePoint.|*{ProjectName} \pkg\debug* ou *{ProjectName} \pkg\release*|  
|Générer des fichiers intermédiaires.|*{ProjectName} \obj\debug* ou *{ProjectName} \obj\release*|  
|Empaqueter des fichiers intermédiaires.|*{ProjectName} \pkgobj\debug* ou *{ProjectName} \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Créer des solutions SharePoint
 Pour générer des solutions SharePoint, l’ordinateur de développement doit avoir la version correcte de SharePoint server est installé. Sinon, la génération de solutions SharePoint est identique à la création des autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Comment : générer des Solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Déboguer et tester des solutions SharePoint
 Avant le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copies le *.wsp* package sur le serveur SharePoint, Active les fonctionnalités de relatives aux applications Web et de Site et dans certains cas, démarre le projet. Dans d’autres cas, vous devrez peut-être ouvrir le projet manuellement. Pour plus d’informations, consultez [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) et [débogage de Solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Déboguer et vérifier des solutions SharePoint à l’aide des fonctionnalités ALM
 Les fonctionnalités de Visual Studio ALM tels que les tests unitaires et IntelliTrace vous permettent plus précisément les problèmes dans vos solutions SharePoint. Profilage vous permet de rechercher et identifier des zones de problème de performances dans vos solutions SharePoint. Pour plus d’informations, consultez [vérification et débogage du SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) et [profilage des performances des Applications SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sécurité pendant le processus de génération
 Pour empaqueter ou déployer des solutions SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] doit avoir l’autorisation de copier des fichiers sur le serveur SharePoint. Vous devez exécuter [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comme un processus élevé et d’utilisateur de votre compte doit être un administrateur de Collections de Site sur le serveur SharePoint. En outre, vous devez spécifier si votre projet est une solution bac à sable ou une solution de batterie de serveurs. Pour plus d’informations, consultez [les différences entre bac à sable et les Solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>À l’aide de la commande Clean  
 Lorsqu’une solution SharePoint est installée sur un serveur SharePoint pour le débogage, la **Clean** commande ne désinstalle pas la solution. Au lieu de cela, vous devez désactiver les fonctionnalités via la configuration de SharePoint.  
  
## <a name="see-also"></a>Voir aussi
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 