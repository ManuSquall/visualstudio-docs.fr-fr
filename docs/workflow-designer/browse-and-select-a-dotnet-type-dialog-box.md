---
title: Rechercher et sélectionner un type .NET (boîte de dialogue)
description: Découvrez comment vous pouvez utiliser la boîte de dialogue Parcourir et sélectionner un type .NET pour choisir un type dans une arborescence d’assemblys et de projets dans Concepteur de flux de travail.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f0a7ffb9e100a621019a5d0ced855575a05708ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875300"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Rechercher et sélectionner un type .NET, boîte de dialogue

Dans la fenêtre **Propriétés** , les boîtes de dialogue ou les concepteurs tels que le concepteur de variables, lorsque vous sélectionnez **Rechercher des types** dans une liste de types de données, est la boîte de dialogue **Parcourir et sélectionner un type .net** (désignée sous la forme abrégée « Explorateur de types »). Cette boîte de dialogue vous permet de choisir un type dans une arborescence d'assemblys et de projets.

Elle est employée dans plusieurs scénarios utilisateur, notamment les suivants :

- lors de la définition du type d'une variable ou d'argument ;

- lors de la sélection d'un type pour une activité générique ;

- lors de l'ajout d'un catch sur l'activité <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> L'explorateur de types peut afficher des types de tableau en escalier Visual Basic, mais pas des types de tableau multidimensionnel. Pour plus d’informations, consultez [tableaux en escalier](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) et [tableaux multidimensionnels](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Sélection d'un type valeur ou référence dans l'Explorateur de types

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Pour sélectionner un type valeur ou référence dans l'Explorateur de types

1. Dans la zone **nom de type** , entrez le nom du type que vous souhaitez utiliser.

2. Effectuez l’une des actions suivantes :

    - Une fois que le nom du type que vous souhaitez utiliser s’affiche dans l’arborescence, dans la zone **nom de type** , double-cliquez sur le type pour le sélectionner.

    - Tapez suffisamment de caractères dans la zone **nom de type** pour identifier de manière unique le type que vous souhaitez utiliser, puis appuyez sur entrée pour sélectionner le type

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Pour sélectionner un type générique dans l'Explorateur de types

1. Dans la zone **nom de type** , tapez le nom du type que vous souhaitez utiliser.

2. Une fois que le nom du type que vous souhaitez utiliser s’affiche dans l’arborescence, dans la zone **nom de type** , cliquez sur le type pour le sélectionner et faire apparaître des zones de liste déroulante.

     Sélectionnez le type que vous souhaitez utiliser pour fermer le générique dans les zones de liste déroulante, puis cliquez sur **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Types affichés dans l'Explorateur de types

Les types affichés dans l'Explorateur de types peuvent varier selon le mode de lancement de l'Explorateur de types. Si l’Explorateur de types a été lancé à partir d’un projet de workflow à l’intérieur de **VS2010**, par défaut, tous les types des assemblys référencés et des projets référencés sont affichés. Si l’Explorateur de types a été lancé en dehors d’un système de projet **VS2010** (comme dans une application de flux de travail réhébergée ou dans un fichier de flux de travail autonome), les types de tous les assemblys chargés dans AppDomain sont affichés par défaut.

Les types dans l'Explorateur de types peuvent être filtrés par développeurs de concepteurs d'activités. Pour une activité donnée, seul un sous-ensemble des types peut s'afficher. Par exemple, dans l'activité <xref:System.Activities.Statements.TryCatch>, seuls les types dérivés de <xref:System.Exception> sont affichés dans l'Explorateur de types.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrage des résultats de la recherche dans l'Explorateur de types

La liste des types dans la zone **nom de type** est plus petite lorsque vous tapez plus de caractères pour rechercher une correspondance. Seuls les types dont le nom fullyqualified commence par la chaîne que vous avez tapée ou des types dont le nom Short commence par la chaîne que vous avez tapée s’affichent dans la liste filtrée.

Par exemple :

1. L' **opération** de frappe correspond à <xref:System.OperationCanceledException> , mais pas à <xref:System.InvalidOperationException> . Pour trouver <xref:System.InvalidOperationException>, commencez par taper System.I ou Invalid.

2. La saisie de correspondances **génériques** <xref:System.GenericUriParser> , mais pas de types dans l' <xref:System.Collections.Generic> espace de noms. Pour rechercher des types dans l' <xref:System.Collections.Generic> espace de noms, tapez le nom complet de l’espace de noms.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Sélectionner un contrat de service à l'aide de la boîte de dialogue de l'Explorateur de types

Lorsque vous sélectionnez un type de contrat de service, l'Explorateur de types affiche uniquement les types possédant l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Voir aussi

- [Utilisation des concepteurs d'activités](control-flow-activity-designers.md)
