---
title: "Génération et débogage de Solutions SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: c74c65d091f170b19357058b1d8ae407b2125e77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Génération et débogage de solutions SharePoint
  En général, la génération et débogage de solutions SharePoint sont le même que pour les autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Les rubriques de cette section expliquent les différences qui existent.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Sortie du projet pour les Solutions SharePoint  
 Génération de solutions SharePoint crée des assemblys et un fichier de package (.wsp) de solution. Le tableau suivant présente les emplacements de ces fichiers lors d’une génération.  
  
|Générer l’élément|Dossier de sortie|  
|----------------|-------------------|  
|Assembly, la base de données de programme (PDB) et fichiers .wsp.|*Nom du projet*\bin\debug ou *nom_projet*\bin\release|  
|Fichiers élément de projet SharePoint.|*Nom du projet*\pkg\debug ou *nom_projet*\pkg\release|  
|Générer des fichiers intermédiaires.|*Nom du projet*\obj\debug ou *nom_projet*\obj\release|  
|Empaqueter des fichiers intermédiaires.|*Nom du projet*\pkgobj\debug ou *nom_projet*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>Génération de Solutions SharePoint  
 Pour générer des solutions SharePoint, l’ordinateur de développement doit avoir la version correcte de SharePoint server est installé. Sinon, la génération de solutions SharePoint est identique à la création des autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Comment : générer des Solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>Débogage et test de Solutions SharePoint  
 Avant le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie le package .wsp sur le serveur SharePoint, Active les fonctionnalités de relatives aux applications Web et de Site et dans certains cas, démarre le projet. Dans d’autres cas, vous devrez peut-être ouvrir le projet manuellement. Pour plus d’informations, consultez [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) et [débogage de Solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>Débogage et vérification des Solutions SharePoint à l’aide des fonctionnalités ALM  
 Les fonctionnalités de Visual Studio ALM tels que les tests unitaires et IntelliTrace vous permettent plus précisément les problèmes dans vos solutions SharePoint. Profilage vous permet de rechercher et identifier des zones de problème de performances dans vos solutions SharePoint. Pour plus d’informations, consultez [vérification et débogage du SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) et [profilage des performances des Applications SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sécurité pendant le processus de génération  
 Pour empaqueter ou déployer des solutions SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] doit avoir l’autorisation de copier des fichiers sur le serveur SharePoint. Vous devez exécuter [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comme un processus élevé et d’utilisateur de votre compte doit être un administrateur de Collections de Site sur le serveur SharePoint. En outre, vous devez spécifier si votre projet est une solution bac à sable ou une solution de batterie de serveurs. Pour plus d’informations, consultez [les différences entre bac à sable et les Solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Utilisation de la commande Nettoyer  
 Lorsqu’une solution SharePoint est installée sur un serveur SharePoint pour le débogage, la **Clean** commande ne désinstalle pas la solution. Au lieu de cela, vous devez désactiver les fonctionnalités via la configuration de SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  