---
title: 'Comment : modifier le type de retour d’une méthode DataContext (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658838"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Guide pratique pour changer le type de retour d’une méthode DataContext (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le type de retour d’une méthode <xref:System.Data.Linq.DataContext> (créée selon une procédure stockée ou fonction) diffère selon l’endroit où vous placez la procédure stockée ou la fonction dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si vous déposez directement un élément sur une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d'entité est créée (si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d'entité). Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.

> [!NOTE]
> Vous ne pouvez pas rétablir les méthodes <xref:System.Data.Linq.DataContext> dont le jeu de types de retour est une classe d’entité afin de retourner le type généré automatiquement via la fenêtre **Propriétés**. Pour rétablir une méthode <xref:System.Data.Linq.DataContext> afin de retourner un type généré automatiquement, vous devez faire glisser l'objet de base de données d'origine vers le Concepteur O/R.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Pour modifier le type de retour d’une méthode DataContext du type généré automatiquement vers une classe d’entité

1. Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.

2. Sélectionnez **Type de retour** dans la fenêtre **Propriétés**, puis sélectionnez une classe d’entité disponible dans la liste **Type de retour**. Si la classe d’entité souhaitée ne figure pas dans la liste, ajoutez-la à ou créez-la dans la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] pour l’ajouter à la liste.

3. Enregistrez le fichier .dbml.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Pour modifier le type de retour d'une méthode DataContext d'une classe d'entité vers le type généré automatiquement

1. Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes et supprimez-la.

2. Faites glisser l’objet de base de données à partir de **Explorateur de serveurs** / **Explorateur de base de données** dans une zone vide du Concepteur O/R.

3. Enregistrez le fichier .dbml.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [méthodes DataContext (concepteur o/r)](../data-tools/datacontext-methods-o-r-designer.md) [Comment : créer des méthodes DataContext mappées à des procédures stockées et des fonctions (concepteur o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
