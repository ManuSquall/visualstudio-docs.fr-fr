---
title: Procédures d’utilisation stockée pour effectuer la mise à jour, insérer et supprimer dans le concepteur Linq to SQL O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089774"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)

Les procédures stockées peuvent être ajoutés à la **Concepteur O/R** et exécutées comme typique <xref:System.Data.Linq.DataContext> méthodes. Ils peuvent également être utilisés pour remplacer la valeur par défaut LINQ au comportement d’exécution SQL qui effectue des insertions, mises à jour et des suppressions lorsque les modifications sont enregistrées à partir des classes d’entité dans une base de données (par exemple, lorsque vous appelez le <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode).

> [!NOTE]
> Si votre procédure stockée retourne des valeurs qui doivent être renvoyées au client (par exemple, les valeurs sont calculées dans la procédure stockée), créez des paramètres de sortie dans vos procédures stockées. Si vous ne pouvez pas utiliser de paramètres de sortie, écrivez une implémentation de méthode partielle au lieu de vous fier aux substitutions générées par le Concepteur O/R. Les membres mappés aux valeurs générées par base de données doivent avoir les valeurs appropriées lorsque les opérations INSERT ou UPDATE se sont correctement achevées. Pour plus d’informations, consultez [responsabilités du développeur de substitution par défaut comportement](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL gère la base de données générée automatiquement les valeurs pour identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et les colonnes timestamp. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées à la base de données, vous devez définir manuellement <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à **true** et <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> à une des opérations suivantes : [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), ou [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurer le comportement de mise à jour d’une classe d’entité

Par défaut, la logique pour mettre à jour une base de données (insertions, mises à jour et suppressions) avec les modifications apportées aux données dans LINQ aux classes d’entité SQL est fournie par l’exécution LINQ to SQL. Le runtime crée par défaut des commandes INSERT, UPDATE et DELETE qui sont basés sur le schéma de la table (la colonne et les informations de clé primaire). Lorsque le comportement par défaut n’est pas souhaité, vous pouvez configurer le comportement de mise à jour en assignant des procédures stockées spécifiques pour l’exécution des instructions d’insertion, des mises à jour et des suppressions requises pour manipuler les données dans votre table. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables à l'aide de procédures stockées.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Pour assigner des procédures stockées afin de substituer le comportement par défaut d'une classe d'entité

1.  Ouvrez le **LINQ to SQL** fichier dans le concepteur. (Double-cliquez sur le **.dbml** fichier **l’Explorateur de solutions**.)

2.  Dans **Explorateur de serveurs** ou **Database Explorer**, développez **Stored Procedures** et localisez les procédures stockées que vous souhaitez utiliser pour l’insertion, mise à jour, et/ou supprimer commandes de la classe d’entité.

3.  Faites glisser la procédure stockée sur le **Concepteur O/R**.

     La procédure stockée est ajoutée au volet de méthodes comme méthode <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Sélectionnez la classe d'entité pour laquelle vous souhaitez utiliser la procédure stockée afin d'effectuer des mises à jour.

5.  Dans le **propriétés** fenêtre, sélectionnez la commande à substituer (**insérer**, **mise à jour**, ou **supprimer**).

6.  Cliquez sur les points de suspension (...) à côté de l’option **utiliser le Runtime** pour ouvrir le **configurer le comportement** boîte de dialogue.

7.  Sélectionnez **personnaliser**.

8.  Sélectionnez la procédure stockée requise dans le **personnaliser** liste.

9. Inspectez la liste de **Arguments de méthode** et **propriétés de la classe** pour vérifier que le **Arguments de méthode** mappage approprié **propriétés de la classe**. Mappez les arguments de méthode d’origine (`Original_<ArgumentName>`) aux propriétés d’origine (`<PropertyName> (Original)`) pour le `Update` et `Delete` commandes.

    > [!NOTE]
    > Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété ont été modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O/R ne peut pas déterminer le mappage correct.

10. Cliquez sur **OK** ou **appliquer**.

    > [!NOTE]
    >  Vous pouvez continuer à configurer le comportement pour chaque combinaison classe et le comportement, que vous cliquez sur **appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement s’affiche et vous offre la possibilité d’appliquer vos modifications.

Pour revenir à l’aide de la logique d’exécution par défaut des mises à jour, cliquez sur les points de suspension en regard du **insérer**, **mise à jour**, ou **supprimer** commande dans le **propriétés**  fenêtre, puis sélectionnez **utiliser runtime** dans le **configurer le comportement** boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Méthodes DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Insérer, mettre à jour et supprimer des opérations (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)