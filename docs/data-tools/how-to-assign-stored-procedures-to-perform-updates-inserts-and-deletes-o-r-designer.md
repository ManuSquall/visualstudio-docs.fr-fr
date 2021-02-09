---
title: Utiliser des procédures stockées dans LINQ to SQL pour mettre à jour des données
description: Utilisez des procédures stockées dans le Concepteur Objet Relationnel LINQ to SQL (Concepteur O/R) pour effectuer des mises à jour, des insertions et des suppressions de données.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f0b7ab161a252e1d3a89ef856325963bddffdc56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866851"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)

Les procédures stockées peuvent être ajoutées au **Concepteur O/R** et exécutées comme méthodes <xref:System.Data.Linq.DataContext> typiques. Elles peuvent également être utilisées pour substituer le comportement par défaut LINQ to SQL au moment de l’exécution qui effectue des insertions, des mises à jour et des suppressions lorsque des modifications sont enregistrées à partir de classes d’entité dans une base de données (par exemple, lors de l’appel de la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode).

> [!NOTE]
> Si votre procédure stockée retourne des valeurs qui doivent être renvoyées au client (par exemple, les valeurs sont calculées dans la procédure stockée), créez des paramètres de sortie dans vos procédures stockées. Si vous ne pouvez pas utiliser de paramètres de sortie, écrivez une implémentation de méthode partielle au lieu de vous fier aux substitutions générées par le Concepteur O/R. Les membres mappés aux valeurs générées par base de données doivent avoir les valeurs appropriées lorsque les opérations INSERT ou UPDATE se sont correctement achevées. Pour plus d’informations, consultez [responsabilités du développeur en matière de substitution du comportement par défaut](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL gère automatiquement les valeurs générées par la base de données pour les colonnes Identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et timestamp. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées par la base de données, vous devez définir manuellement <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> sur **true** et <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> sur l’un des éléments suivants : [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)ou [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurer le comportement de mise à jour d’une classe d’entité

Par défaut, la logique de mise à jour d’une base de données (insertions, mises à jour et suppressions) avec les modifications apportées aux données dans LINQ to SQL classes d’entité est fournie par le runtime LINQ to SQL. Le runtime crée des commandes INSERT, UPDATE et DELETE par défaut basées sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour en affectant des procédures stockées spécifiques pour exécuter les insertions, mises à jour et suppressions nécessaires à la manipulation des données dans votre table. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables à l'aide de procédures stockées.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Pour assigner des procédures stockées afin de substituer le comportement par défaut d'une classe d'entité

1. Ouvrez le fichier **LINQ to SQL** dans le concepteur. (Double-cliquez sur le fichier **.dbml** dans l’**Explorateur de solutions**.)

2. Dans l’**Explorateur de serveurs** ou l’**Explorateur de bases de données**, développez **Procédures stockées** et localisez les procédures stockées à utiliser pour l’insertion, la mise à jour et/ou la suppression de la classe d’entité.

3. Faites glisser la procédure stockée vers le **Concepteur O/R**.

     La procédure stockée est ajoutée au volet de méthodes comme méthode <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Sélectionnez la classe d'entité pour laquelle vous souhaitez utiliser la procédure stockée afin d'effectuer des mises à jour.

5. Dans la fenêtre **Propriétés**, sélectionnez la commande à substituer (**Insert**, **Update** ou **Delete**).

6. Cliquez sur les points de suspension (...) en regard des mots **Utiliser le runtime** pour ouvrir la boîte de dialogue **Configurer le comportement**.

7. Sélectionnez **Personnaliser**.

8. Sélectionnez la procédure stockée voulue dans la liste **Personnaliser**.

9. Inspectez la liste des **Arguments de méthode** et des **Propriétés de classe** pour vérifier que les **Arguments de méthode** mappent aux **Propriétés de classe** appropriées. Mappez les arguments de méthode d’origine ( `Original_<ArgumentName>` ) aux propriétés d’origine ( `<PropertyName> (Original)` ) pour les `Update` `Delete` commandes et.

    > [!NOTE]
    > Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété ont été modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O/R ne peut pas déterminer le mappage correct.

10. Cliquez sur **OK** ou **Appliquer**.

    > [!NOTE]
    > Vous pouvez continuer à configurer le comportement pour chaque combinaison de classe et de comportement tant que vous cliquez sur **appliquer** après avoir effectué chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement s’affiche et vous donne la possibilité d’appliquer vos modifications.

Pour rétablir l’utilisation de la logique runtime par défaut pour les mises à jour, cliquez sur les points de suspension à côté de la commande **Insert**, **Update** ou **Delete** dans la fenêtre **Propriétés**, puis sélectionnez **Utiliser le runtime** dans la boîte de dialogue **Configurer le comportement**.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Méthodes DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Opérations d’insertion, de mise à jour et de suppression (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
