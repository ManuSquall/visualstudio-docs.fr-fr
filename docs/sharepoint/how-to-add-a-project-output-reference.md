---
title: 'Procédure : Ajouter une référence de sortie de projet | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967251"
---
# <a name="how-to-add-a-project-output-reference"></a>Procédure : Ajouter une référence de sortie de projet
  Pour déployer des assemblys de projet non-SharePoint (ou fichiers .xap dans des projets Silverlight) sur SharePoint, ajoutez-les comme une référence de sortie de projet.

 Ce processus crée une dépendance de build de solution entre les deux projets. Projets associés aux références de sortie de projet sont générés avant le projet SharePoint est généré et déployé.

### <a name="to-add-a-project-output-reference"></a>Pour ajouter une référence de sortie de projet

1. Charger une solution qui contient au moins un projet SharePoint et un projet autre que SharePoint.

2. Dans **l’Explorateur de solutions**, choisissez un élément dans le nœud de projet SharePoint.

3. Dans le **propriétés** fenêtre, choisissez le **références de sortie de projet** propriété, puis choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Ellipse de NET Mobile concepteur")) bouton en regard de celle-ci.

4. Dans le **références de sortie de projet** boîte de dialogue, sélectionnez le **ajouter** bouton.

5. Dans le volet Propriétés, cliquez sur la flèche à côté du **Type de déploiement** propriété, puis choisissez une valeur appropriée pour l’élément non-SharePoint que vous référencez, tel que **ElementFile**.

6. Cliquez sur la flèche à côté **nom_projet**, choisissez le nom de l’élément de projet non-SharePoint, puis le **OK** bouton.

## <a name="see-also"></a>Voir aussi
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Guide pratique pour Marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
