---
title: Étendre les fonctionnalités d’un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672358"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Étendre les fonctionnalités d’un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.

 Le code qui définit un TableAdapter est régénéré lorsqu’une modification est apportée au TableAdapter dans le **Concepteur de DataSet**, ou lorsqu’un Assistant modifie la configuration d’un TableAdapter. Pour empêcher la suppression de votre code pendant la régénération d’un TableAdapter, ajoutez du code au fichier de classe partielle du TableAdapter.

 Les classes partielles permettent à du code pour une classe spécifique d’être divisé entre plusieurs fichiers physiques. Pour plus d’informations, consultez [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [Partial (type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Localiser des TableAdapters dans le code
 Alors que les TableAdapters sont conçus avec l' **Concepteur de DataSet**, les classes TableAdapter générées ne sont pas des classes imbriquées de <xref:System.Data.DataSet> . Les TableAdapters se trouvent dans un espace de noms basé sur le nom du jeu de données associé du TableAdapter. Par exemple, si votre application contient un dataset nommé `HRDataSet` , les TableAdapters se trouvent dans l' `HRDataSetTableAdapters` espace de noms. (La Convention d’affectation de noms suit ce modèle : *NomGroupeDonnées*  +  `TableAdapters` ).

 L’exemple suivant suppose qu’un TableAdapter nommé `CustomersTableAdapter` est dans un projet avec `NorthwindDataSet` .

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Pour créer une classe partielle pour un TableAdapter

1. Ajoutez une nouvelle classe à votre projet en accédant au menu **projet** et en sélectionnant**Ajouter une classe**.

2. Nommez la classe `CustomersTableAdapterExtended`.

3. Sélectionnez **Ajouter**.

4. Remplacez le code par l’espace de noms et le nom de classe partiels appropriés pour votre projet, comme suit :

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Voir aussi
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
