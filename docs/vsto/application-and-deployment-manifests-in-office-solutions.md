---
title: "Manifestes d’application et déploiement dans les Solutions Office | Documents Microsoft"
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
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe801405795b3ca0fcb28f024a69d0a9c9c22d8b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifestes d'application et de déploiement dans les solutions Office
  Un manifeste d'application est un fichier XML qui fournit les informations utilisées par une solution Office pour localiser ses assemblys et les mettre à jour. Un manifeste d'application peut être utilisé avec un manifeste de déploiement, qui est un fichier XML stocké sur le serveur fournissant les informations nécessaires à la localisation de la version la plus récente du manifeste d'application et des assemblys.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Structure de manifeste pour les solutions Office  
 Pour les solutions Microsoft Office créées à l'aide des Outils de développement Office dans Visual Studio, tous les manifestes sont basés sur le schéma ClickOnce standard. Quand vous déployez vos solutions Office, les manifestes d’application pour les projets au niveau du document et les projets de complément VSTO se trouvent dans le cache ClickOnce. Les manifestes de déploiement ne sont pas copiés sur l'ordinateur client.  
  
 Pour plus d’informations sur le contenu des manifestes d’application et de déploiement des projets Office, consultez [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md) et [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Création de manifestes d'application et de déploiement  
 Les manifestes d'application sont créés automatiquement dans le cadre du processus de génération. Chaque fois que vous générez un projet au niveau du document, l'emplacement du manifeste de déploiement est incorporé dans le document comme une propriété de document personnalisée. Pour les compléments VSTO, l’emplacement du manifeste de déploiement est stocké dans le Registre.  
  
 Pour plus d’informations sur la **Assistant Publication**, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Pour plus d’informations sur les manifestes fonctionnent avec les solutions Office, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des personnalisations au niveau du Document](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’Application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Manifeste de déploiement ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  