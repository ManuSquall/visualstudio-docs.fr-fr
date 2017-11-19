---
title: "Étendre les fonctionnalités d’un TableAdapter | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0fda0f47084370cd41440311f0cf31c43a69a408
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Étendre les fonctionnalités d’un TableAdapter
Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.  
  
 Le code qui définit un TableAdapter est régénéré lorsque des modifications sont apportées au TableAdapter dans le **Concepteur de Dataset**, ou quand un Assistant modifie la configuration d’un TableAdapter. Pour empêcher votre code d’être supprimé pendant la régénération d’un TableAdapter, ajoutez le code au fichier de classe partielle du TableAdapter.  
  
 Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type).  
  
## <a name="locate-tableadapters-in-code"></a>Recherchez les TableAdapters dans le code  
 Alors que les TableAdapters sont créés avec le **Concepteur de Dataset**, les classes TableAdapter générées ne sont pas des classes imbriquées de <xref:System.Data.DataSet>. Les TableAdapters sont situés dans un espace de noms basé sur le nom du jeu de données associé du TableAdapter. Par exemple, si votre application contienne un dataset nommé `HRDataSet`, les TableAdapters se trouvent dans le `HRDataSetTableAdapters` espace de noms. (La convention d’affectation de noms suit ce modèle : *DatasetName* + `TableAdapters`).  
  
 L’exemple suivant suppose un TableAdapter nommé `CustomersTableAdapter`est dans un projet avec `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Pour créer une classe partielle pour un TableAdapter  
  
1.  Ajouter une nouvelle classe à votre projet en accédant à la **projet** menu et en sélectionnant **ajouter une classe**.  
  
2.  Nommez la classe `CustomersTableAdapterExtended`.  
  
3.  Sélectionnez **ajouter**.  
  
4.  Remplacez le code de l’espace de noms approprié et le nom de classe partielle pour votre projet comme suit :  
  
     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)