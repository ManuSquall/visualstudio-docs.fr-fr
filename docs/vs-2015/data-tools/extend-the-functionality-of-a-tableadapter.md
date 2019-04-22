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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a060444ec5ec8085b56810862e87e523c56fddb6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656061"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Étendre les fonctionnalités d’un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre les fonctionnalités d’un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.  
  
 Le code qui définit un TableAdapter est régénéré lorsque des modifications sont apportées au TableAdapter dans le **Concepteur de Dataset**, ou quand un Assistant modifie la configuration d’un TableAdapter. Pour empêcher que votre code en cours de suppression pendant la régénération d’un TableAdapter, ajoutez le code au fichier de classe partielle du TableAdapter.  
  
 Classes partielles permettent au code pour une classe spécifique être réparti entre plusieurs fichiers physiques. Pour plus d’informations, consultez [partielle](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [partial (Type)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Recherchez les TableAdapters dans le code  
 Alors que les TableAdapters sont conçus avec le **Concepteur de Dataset**, les classes TableAdapter générées ne sont pas des classes imbriquées de <xref:System.Data.DataSet>. Les TableAdapters sont situés dans un espace de noms basé sur le nom de jeu de données du TableAdapter associé. Par exemple, si votre application contienne un dataset nommé `HRDataSet`, les TableAdapters se trouvent dans le `HRDataSetTableAdapters` espace de noms. (La convention d’affectation de noms suit ce modèle : *DatasetName* + `TableAdapters`).  
  
 L’exemple suivant suppose un TableAdapter nommé `CustomersTableAdapter`est dans un projet avec `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Pour créer une classe partielle pour un TableAdapter  
  
1.  Ajouter une nouvelle classe à votre projet en accédant à la **projet** menu et en sélectionnant**ajouter une classe**.  
  
2.  Nommez la classe `CustomersTableAdapterExtended`.  
  
3.  Sélectionnez **Ajouter**.  
  
4.  Remplacez le code avec le nom de classe partielle pour votre projet et un espace de noms approprié comme suit :  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
