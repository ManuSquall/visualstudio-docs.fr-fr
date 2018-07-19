---
title: 'Comment : ajouter et supprimer des assemblys supplémentaires | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e5ff6fd7c9e78871d180f08c6148c25fbede3583
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756286"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Comment : ajouter et supprimer des assemblys supplémentaires
  Si un package SharePoint dépend des autres assemblys pour des fonctionnalités ou données, vous pouvez ajouter les assemblys à votre package de solution (.wsp). De cette façon, le serveur SharePoint permet de s’assurer que les assemblys personnalisés sont installés avec un package.  
  
 Vous pouvez également ajouter et modifier les contrôles sécurisés et les fichiers de ressources de classe associés aux assemblys.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Ajouter des assemblys supplémentaires, les contrôles sécurisés et les ressources de classe  
 Vous pouvez ajouter des assemblys supplémentaires dans le package de solution SharePoint. Déploiement des assemblys supplémentaires dans une solution bac à sable sur le global assembly cache, mais les éléments de projet SharePoint dans une solution bac à sable sont ajoutés à la base de données de contenu. Vous pouvez également ajouter des contrôles sécurisés et les ressources de classe à ces assemblys supplémentaires. Pour plus d’informations sur les contrôles sécurisés, consultez [Providing Packaging and Deployment Information in éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ou « Création d’une entrée SafeControl » dans [déploiement de composants WebPart dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Pour ajouter un assembly existant  
  
1.  Ouvrez le **Package Designer**. Pour plus d’informations, consultez [Comment : personnaliser un Package de Solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Choisissez le **avancé** onglet.  
  
3.  Choisissez le **ajouter** bouton, puis choisissez **ajouter un Assembly existant** dans la liste.  
  
     Le **ajouter un Assembly existant** boîte de dialogue s’affiche.  
  
4.  Choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")), puis choisissez l’assembly que vous souhaitez ajouter. Nous vous recommandons d’utiliser un chemin d’accès relatif à l’assembly sélectionné à des fins de portabilité.  
  
5.  Pour le **cible de déploiement**, choisissez le **GlobalAssemblyCache** case d’option pour déployer l’assembly dans le global assembly cache, ou choisissez le **WebApplication** option bouton pour déployer l’assembly dans le dossier WebApplication sur le serveur qui exécute SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Ajouter un assembly à partir de la sortie du projet  
  
1.  Ouvrez le **Package Designer**.  
  
     Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Choisissez le **avancé** onglet.  
  
3.  Choisissez le **ajouter** bouton, puis choisissez **ajouter un Assembly à partir de la sortie du projet** dans la liste.  
  
     Le **ajouter un Assembly à partir de la sortie du projet** boîte de dialogue s’affiche.  
  
4.  Dans le **projet Source** liste, puis choisissez le projet source que vous souhaitez ajouter.  
  
5.  Pour le **cible de déploiement**, choisissez le **GlobalAssemblyCache** case d’option pour déployer l’assembly dans le global assembly cache, ou choisissez le **WebApplication** option bouton pour déployer l’assembly dans le dossier WebApplication sur le serveur qui exécute SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Pour ajouter un contrôle sécurisé  
  
1.  Ouvrez le **modifier un Assembly existant** boîte de dialogue. Pour ce faire, ouvrez le Concepteur de packages, choisissez le **avancé** onglet, choisissez un assembly, puis le **modifier**bouton.  
  
2.  Dans le **contrôles sécurisés** volet, choisissez le **cliquez ici pour ajouter un nouvel élément** bouton.  
  
3.  Dans le **nom de l’Assembly** colonne, entrez le nom de l’assembly.  
  
4.  Dans le **Namespace** colonne, entrez le nom de l’espace de noms pour le contrôle sécurisé.  
  
5.  Dans le **nom de Type** colonne, entrez le nom du type.  
  
#### <a name="to-add-a-class-resource"></a>Pour ajouter une ressource de classe  
  
1.  Ouvrez le **modifier un Assembly existant** boîte de dialogue. Pour ce faire, ouvrez le Concepteur de packages, choisissez le **avancé** onglet, choisissez un assembly, puis le **modifier** bouton.  
  
2.  Dans le **ressources de classe** volet, choisissez le **cliquez ici pour ajouter un nouvel élément** bouton.  
  
3.  Dans le **nom de fichier** colonne, choisissez les points de suspension (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")), puis choisissez la ressource de classe que vous souhaitez ajouter.  
  
## <a name="delete-custom-assemblies"></a>Supprimer des assemblys personnalisés  
 Vous pouvez supprimer des assemblys à partir d’un package SharePoint, ou supprimer des contrôles sécurisés et les ressources de classe à partir des assemblys existants.  
  
#### <a name="to-delete-an-existing-assembly"></a>Pour supprimer un assembly existant  
  
1.  Ouvrez le **Package Designer**. Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Choisissez le **avancé** onglet.  
  
3.  Dans le **des assemblys supplémentaires** volet, cliquez sur l’assembly personnalisé que vous souhaitez supprimer.  
  
4.  Choisissez le **supprimer** bouton.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Pour supprimer un contrôle sécurisé pour un assembly  
  
1.  Ouvrez le **modifier un Assembly existant** boîte de dialogue. Pour ce faire, ouvrez le Concepteur de packages, choisissez le **avancé** onglet, choisissez un assembly, puis le **modifier** bouton.  
  
2.  Choisissez le contrôle sécurisé que vous souhaitez supprimer.  
  
3.  Choisissez la touche SUPPR.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Pour supprimer une ressource de classe pour un assembly  
  
1.  Ouvrez le **modifier un Assembly existant** boîte de dialogue. Pour ce faire, ouvrez le Concepteur de packages, choisissez le **avancé** onglet, choisissez un assembly, puis le **modifier** bouton.  
  
2.  Choisissez la ressource de classe que vous souhaitez supprimer.  
  
3.  Choisissez la touche SUPPR.  
  
## <a name="see-also"></a>Voir aussi
 [Créer des fonctionnalités de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
