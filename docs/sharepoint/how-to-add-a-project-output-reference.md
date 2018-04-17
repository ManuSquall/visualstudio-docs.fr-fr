---
title: 'Comment : ajouter une référence de sortie de projet | Documents Microsoft'
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
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8be3cd7576dcd42391c2f1bda1bd2d997ea958ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Comment : ajouter une référence de sortie de projet
  Pour déployer des assemblys de projet autre que SharePoint (ou fichiers .xap dans les projets Silverlight) sur SharePoint, ajoutez-les sous la forme d’une référence de sortie de projet.  
  
 Ce processus crée une dépendance de build de solution entre les deux projets. Les projets associés aux références de sortie de projet sont générés avant la génération et le déploiement du projet SharePoint.  
  
### <a name="to-add-a-project-output-reference"></a>Pour ajouter une référence de sortie de projet  
  
1.  Charger une solution qui contient au moins un projet SharePoint et un projet autre que SharePoint.  
  
2.  Dans **l’Explorateur de solutions**, sélectionnez un élément dans le nœud de projet SharePoint.  
  
3.  Dans le **propriétés** fenêtre, choisissez le **références de sortie de projet** propriété, puis choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Points de suspension NET Mobile concepteur")) bouton en regard de celui-ci.  
  
4.  Dans le **références de sortie de projet** boîte de dialogue, choisissez le **ajouter** bouton.  
  
5.  Dans le volet Propriétés, cliquez sur la flèche à côté du **Type de déploiement** propriété, puis choisissez une valeur appropriée pour l’élément non-SharePoint référençant, tel que **ElementFile**.  
  
6.  Cliquez sur la flèche à côté **nom du projet**, choisissez le nom de l’élément de projet non-SharePoint, puis choisissez le **OK** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [En fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  