---
title: Filtrer et trier des données dans une application Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 68adaf6df9f97bee94e7cb393fa01ee133444c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648454"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms

Vous filtrez les données en définissant la propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> sur une expression de chaîne qui retourne les enregistrements souhaités.

Vous triez les données en définissant la propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> sur le nom de la colonne sur laquelle vous souhaitez effectuer le tri. Ajoutez `DESC` pour effectuer un tri dans l’ordre décroissant, ou ajoutez `ASC` pour effectuer un tri dans l’ordre croissant.

> [!NOTE]
> Si votre application n’utilise pas de composants <xref:System.Windows.Forms.BindingSource>, vous pouvez filtrer et trier les données à l’aide d’objets <xref:System.Data.DataView>. Pour plus d’informations, consultez les [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer des données à l’aide d’un composant BindingSource

- Affectez à la propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne les clients dont le `CompanyName` commence par « B » :

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier des données à l’aide d’un composant BindingSource

- Définissez la propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> sur la colonne sur laquelle vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur la colonne `CompanyName` dans l’ordre décroissant :

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)