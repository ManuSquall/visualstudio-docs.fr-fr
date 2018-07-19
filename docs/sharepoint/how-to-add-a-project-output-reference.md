---
title: 'Comment : ajouter une référence de sortie de projet | Microsoft Docs'
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
ms.openlocfilehash: 47b6a3d164bbe1ddcda6d131275427fb1f815198
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755475"
---
# <a name="how-to-add-a-project-output-reference"></a>Comment : ajouter une référence de sortie de projet
  Pour déployer des assemblys de projet non-SharePoint (ou fichiers .xap dans des projets Silverlight) sur SharePoint, ajoutez-les comme une référence de sortie de projet.  
  
 Ce processus crée une dépendance de build de solution entre les deux projets. Projets associés aux références de sortie de projet sont générés avant le projet SharePoint est généré et déployé.  
  
### <a name="to-add-a-project-output-reference"></a>Pour ajouter une référence de sortie de projet
  
1.  Charger une solution qui contient au moins un projet SharePoint et un projet autre que SharePoint.  
  
2.  Dans **l’Explorateur de solutions**, choisissez un élément dans le nœud de projet SharePoint.  
  
3.  Dans le **propriétés** fenêtre, choisissez le **références de sortie de projet** propriété, puis choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Ellipse de NET Mobile concepteur")) bouton en regard de celle-ci.  
  
4.  Dans le **références de sortie de projet** boîte de dialogue, sélectionnez le **ajouter** bouton.  
  
5.  Dans le volet Propriétés, cliquez sur la flèche à côté du **Type de déploiement** propriété, puis choisissez une valeur appropriée pour l’élément non-SharePoint que vous référencez, tel que **ElementFile**.  
  
6.  Cliquez sur la flèche à côté **nom_projet**, choisissez le nom de l’élément de projet non-SharePoint, puis le **OK** bouton.  
  
## <a name="see-also"></a>Voir aussi
 [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
