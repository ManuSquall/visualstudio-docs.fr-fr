---
title: 'Comment : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665979"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les procédures stockées et les fonctions peuvent être ajoutées [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] aux <xref:System.Data.Linq.DataContext> méthodes As. En appelant la méthode pour passer les paramètres requis, la procédure stockée ou fonction est exécutée sur la base de données et retourne les données dans le type de retour de la méthode <xref:System.Data.Linq.DataContext>. Pour plus d’informations sur les <xref:System.Data.Linq.DataContext> méthodes, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Les procédures stockées peuvent également être utilisées pour substituer le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque les modifications sont enregistrées des classes d'entité vers une base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Création de méthodes DataContext
 Vous pouvez créer des <xref:System.Data.Linq.DataContext> méthodes en faisant glisser des procédures stockées ou des fonctions à partir de **Explorateur de serveurs/Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> Le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l’endroit où vous placez la procédure stockée ou fonction dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Le déplacement direct des éléments vers une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité. Le dépôt d’éléments sur une zone vide dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crée une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement. Vous pouvez modifier le type de retour d’une <xref:System.Data.Linq.DataContext> méthode après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Pour créer des méthodes DataContext qui retournent automatiquement les types générés

1. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez le nœud **procédures stockées** de la base de données que vous utilisez.

2. Localisez la procédure stockée requise et faites-la glisser vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     La méthode <xref:System.Data.Linq.DataContext> est créée avec un type de retour généré automatiquement et apparaît dans le volet **Méthodes**.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Pour créer des méthodes DataContext qui ont le type de retour d'une classe d'entité

1. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez le nœud **procédures stockées** de la base de données que vous utilisez.

2. Localisez la procédure stockée requise et faites-la glisser sur une classe d'entité existante dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     La méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour de la classe d’entité sélectionnée et apparaît dans le volet **Méthodes**.

> [!NOTE]
> Pour plus d’informations sur la modification du type de retour d’existant <xref:System.Data.Linq.DataContext> méthodes, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [, méthodes (concepteur o/R)](../data-tools/datacontext-methods-o-r-designer.md) [procédure pas à pas : création de classes LINQ to SQL (concepteur o-r)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Introduction à LINQ dans Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [Comment : écrire des requêtes LINQ en C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
