---
title: "Comment : localiser une fonctionnalité | Documents Microsoft"
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
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53dbaa806ae3b65314d5aeed8df9338905a946cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-a-feature"></a>Comment : localiser une fonctionnalité
  Par défaut, les descriptions et titres de fonction utilisent des valeurs de chaîne codée en dur. Pour localiser le titre de la fonctionnalité et la description, remplacez les chaînes avec des expressions qui référencent des ressources localisées.  
  
## <a name="localizing-a-feature"></a>Localisation d’une fonctionnalité  
  
#### <a name="to-localize-a-feature"></a>Pour localiser une fonctionnalité  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **Feature1** nœud, puis choisissez **ajouter une ressource de fonctionnalité**.  
  
2.  Dans le **ajouter une ressource** boîte de dialogue, choisissez **Langue invariante** dans la liste selon la culture pour le fichier de ressources de fonctionnalité de langue par défaut.  
  
3.  Répétez l’étape précédente pour chaque langue localisée, en choisissant les langues de votre choix pour la fonctionnalité localisée des fichiers de ressources.  
  
     Les fichiers de ressources de fonctionnalité distincts sont créés : un pour la langue par défaut et un pour chaque langue localisée que vous souhaitez prendre en charge.  
  
4.  Ouvrez chaque fichier de ressources dans l’éditeur de ressources, puis entrez tous les ID de chaîne et leurs valeurs.  
  
     Par exemple, dans le fichier de ressources par défaut, entrez un ID de chaîne de **titre** avec la valeur **titre de la fonctionnalité Mes**, et un deuxième ID de chaîne de **Description** avec la valeur **Ma Description de la fonctionnalité**. Pour chaque fichier de ressources localisé, utilisez la même chaîne ID utilisés dans la ressource de fonctionnalité par défaut, mais entrez des chaînes localisées pour les valeurs.  
  
5.  Après avoir entré toutes les valeurs de ressource, ouvrez le menu contextuel pour la fonctionnalité (par exemple, Feature1.feature), puis choisissez **Concepteur de vue** pour ouvrir la fonctionnalité dans le Concepteur de fonctionnalités.  
  
6.  Pour localiser le **titre** et **Description** champs dans la fonction, utilisez le format suivant pour entrer des valeurs dans les zones :  
  
     `$Resources:`*ID de chaîne*  
  
     Par exemple, entrez $Resources :**titre** dans les **titre de la fonctionnalité** boîte et $Resources :**Description** dans le **Description de la fonctionnalité** boîte .  
  
     Les ID de chaîne doivent correspondre à celles qui sont utilisées dans les fichiers de ressources.  
  
7.  Appuyez sur la touche F5 pour générer et exécuter l’application.  
  
8.  Dans SharePoint, ouvrez le **Actions du Site** menu, choisissez **paramètres du Site**, puis, dans le **Actions du Site** section choisir le **gérer les fonctionnalités du Site** lien.  
  
9. Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Le titre de la fonctionnalité localisée et la description s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Localisation de Solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Guide pratique pour localiser du code](../sharepoint/how-to-localize-code.md)  
  
  