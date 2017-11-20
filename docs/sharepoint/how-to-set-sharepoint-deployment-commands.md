---
title: "Comment : définir des commandes de déploiement SharePoint | Documents Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c67972dddedcd05338d793883b2dcba0789d48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Comment : définir des commandes de déploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de prédéploiement et de post-déploiement. Ces commandes s’exécutent avant et après les autres actions de déploiement lorsque vous déboguez des solutions SharePoint à partir de Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Pour ajouter une commande de prédéploiement  
  
1.  Dans la barre de menus, choisissez **Projet**, *Propriétés de***NomProjet**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de prédéploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire avant la fin de déploiement, entrez **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Pour ajouter une commande de post-déploiement  
  
1.  Dans la barre de menus, choisissez **Projet**, *Propriétés de***NomProjet**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **ligne de commande de post-déploiement** texte, entrez les commandes MS-DOS ou MSBuild pour personnaliser cette étape.  
  
     Par exemple, pour répertorier le contenu du répertoire une fois le déploiement terminé, entrez **dir**. Pour utiliser une variable de MSBuild pour copier l’assembly à partir du répertoire de build, entrez **copier $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  