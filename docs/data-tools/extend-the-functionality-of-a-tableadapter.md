---
title: Étendre les fonctionnalités d’un TableAdapter
description: Apprenez à étendre les fonctionnalités d’un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f8cea8ec761bf50ddc0f928112975c366f62418b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215836"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Étendre les fonctionnalités d’un TableAdapter

Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.

Le code qui définit un TableAdapter est régénéré lorsqu’une modification est apportée au TableAdapter dans le **Concepteur de DataSet**, ou lorsqu’un Assistant modifie la configuration d’un TableAdapter. Pour empêcher la suppression de votre code pendant la régénération d’un TableAdapter, ajoutez du code au fichier de classe partielle du TableAdapter.

Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [Partial (type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Localiser des TableAdapters dans le code

Alors que les TableAdapters sont conçus avec l' **Concepteur de DataSet**, les classes TableAdapter générées ne sont pas des classes imbriquées de <xref:System.Data.DataSet> . Les TableAdapters se trouvent dans un espace de noms basé sur le nom du jeu de données associé du TableAdapter. Par exemple, si votre application contient un dataset nommé `HRDataSet` , les TableAdapters se trouvent dans l' `HRDataSetTableAdapters` espace de noms. (La Convention d’affectation de noms suit ce modèle : *NomGroupeDonnées*  +  `TableAdapters` ).

L’exemple suivant suppose qu’un TableAdapter nommé `CustomersTableAdapter` est dans un projet avec `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Pour créer une classe partielle pour un TableAdapter

1. Ajoutez une nouvelle classe à votre projet en accédant au menu **projet** et en sélectionnant **Ajouter une classe**.

2. Nommez la classe `CustomersTableAdapterExtended`.

3. Sélectionnez **Ajouter**.

4. Remplacez le code par l’espace de noms et le nom de classe partiels appropriés pour votre projet, comme suit :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
