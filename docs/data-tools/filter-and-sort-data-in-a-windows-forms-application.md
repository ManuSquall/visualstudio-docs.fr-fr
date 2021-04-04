---
title: Filtrer et trier des données dans une application Windows Forms
description: Filtrez et triez les données dans une application Windows Forms. Définissez la propriété Filter sur une expression de chaîne qui retourne les enregistrements souhaités.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215823"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms

Vous filtrez les données en affectant <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété une expression de chaîne qui retourne les enregistrements souhaités.

Vous triez les données en définissant la <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété sur le nom de la colonne sur laquelle vous souhaitez effectuer le tri ; ajouter pour effectuer un `DESC` tri dans l’ordre décroissant ou pour effectuer un tri `ASC` dans l’ordre croissant.

> [!NOTE]
> Si votre application n’utilise pas de <xref:System.Windows.Forms.BindingSource> composants, vous pouvez filtrer et trier les données à l’aide d' <xref:System.Data.DataView> objets. Pour plus d’informations, consultez les [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne les clients avec un `CompanyName` qui commence par « B » :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Sort%2A> à la propriété la colonne sur laquelle vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur la `CompanyName` colonne dans l’ordre décroissant :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
