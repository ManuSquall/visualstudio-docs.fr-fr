---
title: 'Procédure : Localiser une fonctionnalité | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26eb3a1352228d48fb451e3a3520162cdea18b73
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867375"
---
# <a name="how-to-localize-a-feature"></a>Procédure : Localiser une fonctionnalité
  Par défaut, les descriptions et les titres des fonctionnalités utilisent des valeurs de chaîne codées en dur. Pour localiser le titre de la fonctionnalité et la description, remplacez les chaînes avec des expressions qui référencent des ressources localisées.  
  
## <a name="localize-a-feature"></a>Localiser une fonctionnalité  
  
#### <a name="to-localize-a-feature"></a>Pour localiser une fonctionnalité  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **Feature1** nœud, puis choisissez **ajouter une ressource de fonctionnalité**.  
  
2.  Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **langue indifférente** dans la liste selon la culture pour le fichier de ressources de fonctionnalité de langage par défaut.  
  
3.  Répétez l’étape précédente pour chaque langue localisée, en choisissant les langues de votre choix pour la fonctionnalité localisée des fichiers de ressources.  
  
     Fichiers de ressources de fonctionnalité distincts sont créés : un pour la langue par défaut et un pour chaque langue localisée que vous souhaitez prendre en charge.  
  
4.  Ouvrez chaque fichier de ressources dans l’éditeur de ressources et entrez tous les ID de chaîne et leurs valeurs.  
  
     Par exemple, dans le fichier de ressources de fonctionnalité par défaut, entrez un ID de chaîne de **titre** avec la valeur **mon titre de fonctionnalité**, et un deuxième ID de chaîne de **Description** avec la valeur **Ma Description de la fonctionnalité**. Pour chaque fichier de ressources localisé, utilisez la même chaîne ID utilisés dans la ressource de fonctionnalité par défaut, mais entrez des chaînes localisées pour les valeurs.  
  
5.  Après avoir entré toutes les valeurs de ressource, ouvrez le menu contextuel de la fonctionnalité (par exemple, *Feature1.feature*), puis choisissez **Concepteur de vue** pour ouvrir la fonctionnalité dans le Concepteur de fonctionnalités.  
  
6.  Pour localiser le **titre** et **Description** champs dans la fonctionnalité, utilisez le format suivant pour entrer des valeurs dans leurs zones :  
  
     `$Resources:` *ID de chaîne*  
  
     Par exemple, entrez $Resources :**titre** dans le **titre de la fonctionnalité** boîte et $Resources :**Description** dans le **Description de la fonctionnalité** boîte .  
  
     Les ID de chaîne doivent correspondre à celles qui sont utilisées dans les fichiers de ressources.  
  
7.  Choisissez le **F5** clé pour générer et exécuter l’application.  
  
8.  Dans SharePoint, ouvrez le **Actions du Site** menu, choisissez **paramètres du Site**, puis, dans le **Actions du Site** section choisir le **gérer les fonctionnalités du Site** lien.  
  
9. Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Le titre de la fonctionnalité localisée et la description apparaissent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit avoir installé un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi
 [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Guide pratique pour Ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Guide pratique pour Localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Guide pratique pour Localiser le code](../sharepoint/how-to-localize-code.md)  
