---
title: 'Procédure : Définir des commandes de déploiement SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7664dfcfe11d7ab7dc6ab03045533bbd9e69fb9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812908"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procédure : Définir des commandes de déploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de prédéploiement et de post-déploiement. Ces commandes s’exécutent avant et après les autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement

1. Dans la barre de menus, choisissez **projet** > **\<*nom_projet*> Propriétés**.

2. Choisissez le **SharePoint** onglet.

3. Dans le **ligne de commande de prédéploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire avant la fin de déploiement, entrez **dir**.

### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de post-déploiement

1. Dans la barre de menus, choisissez **projet** > **\<*nom_projet*> Propriétés**.

2. Choisissez le **SharePoint** onglet.

3. Dans le **ligne de commande de post-déploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.

     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable MSBuild pour copier l’assembly à partir du répertoire de build, entrez **copier $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
