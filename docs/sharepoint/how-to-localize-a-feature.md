---
title: 'Comment : localiser une fonctionnalité | Microsoft Docs'
description: Apprenez à localiser les titres et les descriptions des fonctionnalités dans SharePoint en remplaçant les valeurs de chaîne codées en dur par des expressions qui font référence à des ressources localisées.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4a3c427f207f6aac9f6a827eb6c24b799d635b46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913602"
---
# <a name="how-to-localize-a-feature"></a>Comment : localiser une fonctionnalité
  Par défaut, les titres et les descriptions des fonctionnalités utilisent des valeurs de chaîne codées en dur. Pour localiser le titre et la description de la fonctionnalité, remplacez les chaînes par des expressions qui font référence à des ressources localisées.

## <a name="localize-a-feature"></a>Localiser une fonctionnalité

#### <a name="to-localize-a-feature"></a>Pour localiser une fonctionnalité

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **Feature1** , puis choisissez **Ajouter une ressource de fonctionnalité**.

2. Dans la boîte de dialogue **Ajouter une ressource** , choisissez **Langue indifférente** dans la liste en tant que culture du fichier de ressources de fonctionnalité de langue par défaut.

3. Répétez l’étape précédente pour chaque langue localisée, en choisissant les langues de votre choix pour les fichiers de ressources de fonctionnalités localisés.

     Des fichiers de ressources de fonctionnalité distincts sont créés : un pour la langue par défaut et un pour chaque langue localisée que vous souhaitez prendre en charge.

4. Ouvrez chaque fichier de ressources dans l’éditeur de ressources, puis entrez tous les ID de chaîne et leurs valeurs.

     Par exemple, dans le fichier de ressources de fonctionnalité par défaut, entrez un ID de chaîne de **titre** avec la valeur **My Feature title** et un deuxième ID de chaîne **Description** avec la valeur **My Feature Description**. Pour chaque fichier de ressources localisé, utilisez les mêmes ID de chaîne que ceux utilisés dans la ressource de fonctionnalité par défaut, mais entrez des chaînes localisées pour les valeurs.

5. Après avoir entré toutes les valeurs de ressource, ouvrez le menu contextuel pour la fonctionnalité (par exemple, *Feature1. Feature*), puis choisissez **Concepteur de vues** pour ouvrir la fonctionnalité dans le concepteur de fonctionnalités.

6. Pour localiser les champs de **titre** et de **Description** dans la fonctionnalité, utilisez le format suivant pour entrer des valeurs dans leurs zones :

     `$Resources:` *Identificateur de chaîne*

     Par exemple, entrez $Resources :**titre** dans la zone titre de la **fonctionnalité** et $Resources :**Description** dans la zone Description de la **fonctionnalité** .

     Les ID de chaîne doivent correspondre à ceux utilisés dans les fichiers de ressources.

7. Appuyez sur la touche **F5** pour générer et exécuter l’application.

8. Dans SharePoint, ouvrez le menu **actions du site** , choisissez Paramètres du **site**, puis, dans la section actions du **site** , choisissez le lien gérer les **fonctionnalités du site** .

9. Dans SharePoint, modifiez la langue d’affichage par défaut.

     Le titre et la description de la fonctionnalité localisée s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.

## <a name="see-also"></a>Voir aussi
- [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)
- [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Comment : localiser du code](../sharepoint/how-to-localize-code.md)
