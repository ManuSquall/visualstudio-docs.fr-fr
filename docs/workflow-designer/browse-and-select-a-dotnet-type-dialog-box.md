---
title: Concepteur de flux de travail - Parcourir et sélectionner une Type .NET, boîte de dialogue
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5430e489b90a99a2bec2acc368a26671d7ffd4cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995984"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Rechercher et sélectionner un type .NET, boîte de dialogue

Dans le **propriétés** fenêtre, les boîtes de dialogue ou les concepteurs, tels que le Concepteur de variables, lorsque vous sélectionnez **rechercher des Types** à partir d’une liste des types de données, est le **Parcourir et sélectionner un Type .NET** boîte de dialogue (appelée dans la forme abrégée « Explorateur de types »). Cette boîte de dialogue vous permet de choisir un type dans une arborescence d’assemblys et de projets.

Elle est employée dans plusieurs scénarios utilisateur, notamment les suivants :

-   lors de la définition du type d'une variable ou d'argument ;

-   lors de la sélection d'un type pour une activité générique ;

-   lors de l'ajout d'un catch sur l'activité <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> L'explorateur de types peut afficher des types de tableau en escalier Visual Basic, mais pas des types de tableau multidimensionnel. Consultez [tableaux en escalier](http://go.microsoft.com/fwlink/?LinkId=195226) et [tableaux multidimensionnels](http://go.microsoft.com/fwlink/?LinkId=195227) pour plus d’informations.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Sélection d'un type valeur ou référence dans l'Explorateur de types

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Pour sélectionner un type valeur ou référence dans l'Explorateur de types

1.  Dans le **nom de Type** , entrez le nom du type que vous souhaitez utiliser.

2.  Effectuez l’une des opérations suivantes :

    -   Une fois que le nom du type que vous souhaitez utiliser s’affiche dans l’arborescence de la **nom de Type** , double-cliquez sur le type pour le sélectionner.

    -   Tapez suffisamment de caractères dans le **nom de Type** boîte pour identifier de façon unique le type que vous souhaitez utiliser et appuyez sur ENTRÉE pour sélectionner le type

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Pour sélectionner un type générique dans l'Explorateur de types

1.  Dans le **nom de Type** zone, tapez le nom du type que vous souhaitez utiliser.

2.  Une fois que le nom du type que vous souhaitez utiliser s’affiche dans l’arborescence de la **nom de Type** boîte, cliquez sur le type à sélectionner et faire des listes déroulantes s’affichent.

     Sélectionnez le type que vous souhaitez utiliser pour fermer le type générique dans les zones de liste déroulante, puis cliquez sur **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Types affichés dans l'Explorateur de types

Les types affichés dans l'Explorateur de types peuvent varier selon le mode de lancement de l'Explorateur de types. Si l’Explorateur de types a été lancé à partir d’un projet de flux de travail à l’intérieur de **vs2010**, par défaut, tous les types dans les assemblys référencés et les projets référencés sont affichés. Si l’Explorateur de types a été lancé en dehors d’un **vs2010** système (par exemple, comme dans une application de workflow réhébergée ou dans un fichier de flux de travail autonome), de projet par défaut s’affichent les types à partir de tous les assemblys chargés dans l’AppDomain .

Les types dans l'Explorateur de types peuvent être filtrés par développeurs de concepteurs d'activités. Pour une activité donnée, seul un sous-ensemble des types peut s'afficher. Par exemple, dans l'activité <xref:System.Activities.Statements.TryCatch>, seuls les types dérivés de <xref:System.Exception> sont affichés dans l'Explorateur de types.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrage des résultats de la recherche dans l'Explorateur de types

La liste des types dans le **nom de Type** zone obtient plus court à mesure que vous tapez plus de caractères pour rechercher une correspondance. Seuls les types fullyqualified dont le nom commence par la chaîne que vous avez tapé ou des types dont le nom court commence par la chaîne que vous avez tapé s’affichent dans la liste filtrée.

Exemple :

1.  Tapant **opération** correspond à <xref:System.OperationCanceledException> mais pas <xref:System.InvalidOperationException>. Pour trouver <xref:System.InvalidOperationException>, commencez par taper System.I ou Invalid.

2.  Tapant **générique** correspond à <xref:System.GenericUriParser> mais pas les types dans le <xref:System.Collections.Generic> espace de noms. Pour rechercher les types dans le <xref:System.Collections.Generic> espace de noms, tapez le nom qualifié complet de l’espace de noms.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Sélectionner un contrat de service à l'aide de la boîte de dialogue de l'Explorateur de types

Lorsque vous sélectionnez un type de contrat de service, l'Explorateur de types affiche uniquement les types possédant l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Voir aussi

- [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)