---
title: 'Comment : obtenir des Versions spécifiques d’un DataRow | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 5bd8ae12c77c671e375043a0381a4b580d1a03d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255484"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Comment : obtenir des versions spécifiques d'un DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque des modifications sont apportées aux lignes de données, le jeu de données conserve les deux d’origine (<xref:System.Data.DataRowVersion>) et les nouveaux (<xref:System.Data.DataRowVersion>) versions de la ligne. Par exemple, avant d’appeler le `AcceptChanges` (méthode), votre application peut accéder à différentes versions d’un enregistrement (tel que défini dans le <xref:System.Data.DataRowVersion> énumération) et traiter les modifications en conséquence.  
  
> [!NOTE]
>  Différentes versions d’une ligne existent uniquement après qu’elle a été modifié et avant qu’elle ait le `AcceptChanges` méthode appelée. Après le `AcceptChanges` méthode a été appelée, les versions actuelles et d’origine sont identiques.  
  
 En passant le <xref:System.Data.DataRowVersion> valeur, ainsi que l’index de colonne (ou le nom de la colonne sous forme de chaîne) retourne la valeur de la version de ligne particulière de cette colonne. La colonne modifiée est identifiée pendant le <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.ColumnChanged> événements, c’est un bon moment pour inspecter le qui se différencie des versions à des fins de validation de ligne. Toutefois, si vous avez temporairement interrompu des contraintes, ces événements ne seront pas déclenchés et vous devez identifier par programmation les colonnes qui ont été modifiés. Ce faire, vous pouvez itérer au sein du <xref:System.Data.DataTable.Columns%2A> collection et en comparant les différentes <xref:System.Data.DataRowVersion> valeurs.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Accès à la Version d’origine d’un DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Pour obtenir la version d’origine d’un enregistrement  
  
-   Accéder à la valeur d’une colonne en passant le <xref:System.Data.DataRowVersion> de la ligne que vous souhaitez retourner.  
  
     L’exemple suivant montre comment vous pouvez utiliser un <xref:System.Data.DataRowVersion> valeur à obtenir la valeur d’origine d’un `CompanyName` champ dans un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>L’accès à la Version actuelle d’un DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Pour obtenir la version actuelle d’un enregistrement  
  
-   Accéder à la valeur d’une colonne et ajouter un paramètre à l’index indiquant quelle version d’une ligne que vous souhaitez retourner.  
  
     L’exemple suivant montre comment vous pouvez utiliser un <xref:System.Data.DataRowVersion> valeur à obtenir la valeur actuelle d’un `CompanyName` champ dans un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [L’enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d’ensemble des Applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)