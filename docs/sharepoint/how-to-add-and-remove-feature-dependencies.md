---
title: "Comment : ajouter et supprimer des dépendances de fonctionnalité | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d758c5d4f410881989492f64dd7a7e5b8dc73804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Comment : ajouter et supprimer des dépendances de fonctionnalités
  Votre fonctionnalité SharePoint peut dépendre d’autres fonctionnalités pour les fonctionnalités ou de données. Dans ce cas, vous pouvez marquer ces fonctionnalités en tant que dépendances de votre fonction. De cette manière, le serveur SharePoint garantit que les fonctionnalités dépendantes sont activées avant votre fonctionnalité est activée.  
  
## <a name="adding-dependencies"></a>Ajout de dépendances  
 Vous pouvez ajouter d’autres fonctionnalités dans votre solution en tant que dépendances. De cette manière, vous pouvez vous assurer que les fonctionnalités requises sont installées et activées pour permettre à votre composant est installé.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Pour ajouter une dépendance sur une fonctionnalité dans la solution  
  
1.  Ouvrez le Concepteur de fonctionnalités, développez le **des dépendances d’Activation de fonctionnalité** nœud, puis choisissez le **ajouter** bouton.  
  
2.  Dans le **ajouter des dépendances d’Activation de fonctionnalité** boîte de dialogue, choisissez le **ajouter une dépendance sur les fonctionnalités de la solution** case d’option, cliquez sur le titre de la fonctionnalité que vous souhaitez ajouter en tant que dépendance, puis Choisissez le **ajouter** bouton.  
  
     Vous pouvez ajouter plusieurs fonctionnalités en sélectionnant plusieurs titres tout en appuyant sur la touche CTRL enfoncée.  
  
## <a name="adding-custom-dependencies"></a>Ajout de dépendances personnalisées  
 Vous pouvez ajouter des fonctionnalités qui sont déjà déployées sur un serveur SharePoint en tant que dépendance. De cette manière, le processus d’activation de SharePoint vérifie pour vous assurer que tous les composants dépendants sont activés avant que votre fonctionnalité est installée.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Pour ajouter une dépendance par l’ID de fonctionnalité  
  
1.  Ouvrez le Concepteur de fonctionnalités, développez le **des dépendances d’Activation de fonctionnalité** nœud, puis choisissez le **ajouter** bouton.  
  
2.  Dans le **ajouter des dépendances d’Activation de fonctionnalité** boîte de dialogue, choisissez le **ajouter une dépendance personnalisée** case d’option.  
  
3.  Dans le **ID de la fonctionnalité** texte, entrez le GUID de la fonctionnalité que vous souhaitez marquer comme une dépendance d’activation, puis choisissez le **ajouter** bouton.  
  
## <a name="editing-custom-dependencies"></a>Modification de dépendances personnalisées  
 Vous pouvez modifier des dépendances personnalisées que vous avez ajouté précédemment. Toutefois, les fonctionnalités dépendantes sont dans votre solution peuvent uniquement être supprimée, pas modifié.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Pour modifier une dépendance sur une fonctionnalité dans la solution  
  
1.  Ouvrez le Concepteur de fonctionnalités, puis le **des dépendances d’Activation de fonctionnalité** nœud.  
  
2.  Choisissez le nom de la fonctionnalité que vous souhaitez modifier, puis choisissez le **modifier** bouton.  
  
3.  Dans le **modifier la dépendance d’Activation personnalisée fonctionnalité** boîte de dialogue Modifier le titre, un ID de fonctionnalité ou une description, puis choisissez le **Submit** bouton.  
  
## <a name="removing-dependencies"></a>Suppression de dépendances  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Pour supprimer une dépendance sur une fonctionnalité dans la solution  
  
1.  Dans le Concepteur de fonctionnalités, développez le **des dépendances d’Activation de fonctionnalité** nœud, choisissez le nom de la fonctionnalité que vous souhaitez supprimer, puis choisissez le **supprimer** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Guide pratique pour ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  