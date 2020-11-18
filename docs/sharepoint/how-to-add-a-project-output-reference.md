---
title: 'Comment : ajouter une référence de sortie de projet | Microsoft Docs'
description: Apprenez à ajouter une référence de sortie de projet afin de pouvoir déployer des assemblys de projet non-SharePoint (ou des fichiers. xap dans des projets Silverlight) sur SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 03980eea9d16cde2b6f079e0b33973958fed7a7f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849868"
---
# <a name="how-to-add-a-project-output-reference"></a>Comment : ajouter une référence de sortie de projet
  Pour déployer des assemblys de projet non-SharePoint (ou des fichiers. xap dans des projets Silverlight) vers SharePoint, ajoutez-les en tant que référence de sortie de projet.

 Ce processus crée une dépendance de génération de solution entre les deux projets. Les projets associés aux références de sortie de projet sont générés avant la génération et le déploiement du projet SharePoint.

### <a name="to-add-a-project-output-reference"></a>Pour ajouter une référence de sortie de projet

1. Chargez une solution qui contient au moins un projet SharePoint et un projet non SharePoint.

2. Dans **Explorateur de solutions**, choisissez un élément dans le nœud de projet SharePoint.

3. Dans la fenêtre **Propriétés** , choisissez la propriété **références de sortie du projet** , puis choisissez le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) en regard de celle-ci.

4. Dans la boîte de dialogue **références de sortie du projet** , cliquez sur le bouton **Ajouter** .

5. Dans le volet Propriétés, cliquez sur la flèche en regard de la propriété **type de déploiement** , puis choisissez une valeur appropriée pour l’élément non SharePoint que vous référencez, par exemple **ElementFile**.

6. Choisissez la flèche en regard de **nom du projet**, choisissez le nom de l’élément de projet non-SharePoint, puis choisissez le bouton **OK** .

## <a name="see-also"></a>Voir aussi
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
