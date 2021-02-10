---
title: 'Procédure : définir des commandes de déploiement SharePoint | Microsoft Docs'
description: Découvrez comment personnaliser le processus de déploiement en définissant les commandes de pré-déploiement et de publication de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965848"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procédure : définir des commandes de déploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de pré-déploiement et de prédéploiement. Ces commandes s’exécutent avant et après d’autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement

1. Dans la barre de menus,  choisissez  >  **\<*ProjectName*> Propriétés** du projet.

2. Choisissez l’onglet **SharePoint** .

3. Dans la zone de texte **ligne de commande de prédéploiement** , entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire avant la fin du déploiement, entrez **dir**.

### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de publication

1. Dans la barre de menus,  choisissez  >  **\<*ProjectName*> Propriétés** du projet.

2. Choisissez l’onglet **SharePoint** .

3. Dans la zone de texte **ligne de commande de publication du déploiement** , entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable MSBuild pour copier l’assembly à partir du répertoire de build, entrez **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
