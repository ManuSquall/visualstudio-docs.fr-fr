---
title: Modifier le type de retour de la méthode DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da1dc0437ccd4a7fad2a24b40542a58d8310bf17
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036663"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Guide pratique pour changer le type de retour d’une méthode DataContext (Concepteur O/R)
Le type de retour d’une <xref:System.Data.Linq.DataContext> méthode (créée selon une procédure stockée ou une fonction) diffère selon l’endroit où vous déposez la procédure stockée ou la fonction dans le **Concepteur O/R**. Si vous déposez directement un élément sur une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d'entité est créée (si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d'entité). Si vous déposez un élément dans une zone vide du **Concepteur O/R**, une <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.

> [!NOTE]
> Vous ne pouvez pas rétablir les méthodes <xref:System.Data.Linq.DataContext> dont le jeu de types de retour est une classe d’entité afin de retourner le type généré automatiquement via la fenêtre **Propriétés**. Pour rétablir une <xref:System.Data.Linq.DataContext> méthode afin de retourner un type généré automatiquement, vous devez faire glisser l’objet de base de données d’origine vers le **Concepteur O/R** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Pour modifier le type de retour d’une méthode DataContext du type généré automatiquement vers une classe d’entité

1. Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.

2. Sélectionnez **Type de retour** dans la fenêtre **Propriétés**, puis sélectionnez une classe d’entité disponible dans la liste **Type de retour**. Si la classe d’entité souhaitée ne figure pas dans la liste, ajoutez-la à ou créez-la dans le **Concepteur O/R** pour l’ajouter à la liste.

3. Enregistrez le fichier *. dbml* .

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Pour modifier le type de retour d'une méthode DataContext d'une classe d'entité vers le type généré automatiquement

1. Sélectionnez la <xref:System.Data.Linq.DataContext> méthode dans le volet **méthodes** et supprimez-la.

2. Faites glisser l’objet de base de données à partir de **Explorateur de serveurs** ou **Explorateur de base de données** dans une zone vide du **Concepteur O/R**.

3. Enregistrez le fichier *. dbml* .

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Méthode DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
