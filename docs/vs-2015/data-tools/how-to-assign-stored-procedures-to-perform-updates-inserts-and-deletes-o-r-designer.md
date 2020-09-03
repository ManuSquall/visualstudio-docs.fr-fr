---
title: 'Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609981"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les procédures stockées peuvent être ajoutées au Concepteur O/R et être exécutées comme méthodes <xref:System.Data.Linq.DataContext> typiques. Elles peuvent également être utilisées pour substituer le comportement d’exécution par défaut [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque des modifications sont enregistrées à partir de classes d’entité dans une base de données (par exemple, lors de l’appel de la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode).

> [!NOTE]
> Si votre procédure stockée retourne des valeurs qui doivent être renvoyées au client (par exemple, les valeurs sont calculées dans la procédure stockée), créez des paramètres de sortie dans vos procédures stockées. Si vous ne pouvez pas utiliser de paramètres de sortie, écrivez une implémentation de méthode partielle au lieu de vous fier aux substitutions générées par le Concepteur O/R. Les membres mappés aux valeurs générées par base de données doivent avoir les valeurs appropriées lorsque les opérations INSERT ou UPDATE se sont correctement achevées. Pour plus d’informations, consultez [responsabilités du développeur en matière de substitution du comportement par défaut](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gère automatiquement les valeurs générées par une base de données pour les colonnes identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et timestamp. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées par une base de données, vous devez affecter la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à `true` et l'une des valeurs suivantes à <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configuration du comportement de mise à jour d'une classe d'entité
 Par défaut, la logique de mise à jour d'une base de données (insertions, mises à jour et suppressions) avec les modifications apportées aux données dans les classes de l'entité [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] est fournie par le runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Le runtime crée des commandes d’insertion, de mise à jour et de suppression par défaut qui sont basées sur le schéma de la table (la colonne et les informations de clé primaire). Si vous ne voulez pas du comportement par défaut, vous pouvez configurer le comportement de mise à jour en assignant des procédures stockées spécifiques pour effectuer les insertions, mises à jour et suppressions requises afin de manipuler les données dans votre table. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables à l'aide de procédures stockées.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Pour assigner des procédures stockées afin de substituer le comportement par défaut d'une classe d'entité

1. Ouvrez le fichier **LINQ to SQL** dans le concepteur. (Double-cliquez sur le fichier .dbml dans l’**Explorateur de solutions**.)

2. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez **procédures stockées** et localisez les procédures stockées que vous souhaitez utiliser pour les commandes d’insertion, de mise à jour et/ou de suppression de la classe d’entité.

3. Faites glisser la procédure stockée vers le Concepteur O/R.

     La procédure stockée est ajoutée au volet de méthodes comme méthode <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Sélectionnez la classe d'entité pour laquelle vous souhaitez utiliser la procédure stockée afin d'effectuer des mises à jour.

5. Dans la fenêtre **Propriétés**, sélectionnez la commande à substituer (**Insert**, **Update** ou **Delete**).

6. Cliquez sur les points de suspension (...) en regard des mots **Utiliser le runtime** pour ouvrir la boîte de dialogue **Configurer le comportement**.

7. Sélectionnez **Personnaliser**.

8. Sélectionnez la procédure stockée voulue dans la liste **Personnaliser**.

9. Inspectez la liste des **Arguments de méthode** et des **Propriétés de classe** pour vérifier que les **Arguments de méthode** mappent aux **Propriétés de classe** appropriées. Mappez les arguments de méthode d’origine (Original_*ArgumentName*) aux propriétés d’origine (*PropertyName* (original)) pour les commandes Update et DELETE.

    > [!NOTE]
    > Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété ont été modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O/R ne peut pas déterminer le mappage correct.

10. Cliquez sur **OK** ou **Appliquer**.

    > [!NOTE]
    > Vous pouvez continuer à configurer le comportement de chaque combinaison classe/comportement tant que vous cliquez sur **Appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement vous donnant la possibilité d’appliquer toutes les modifications s’affiche.

     Pour revenir à l’utilisation de la logique de Runtime par défaut pour les mises à jour, cliquez sur les points de suspension en regard de la commande d’insertion, de mise à jour ou de suppression dans la fenêtre **Propriétés** , puis sélectionnez **utiliser le runtime** dans la boîte de dialogue Configurer le **comportement** .

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [, méthodes (concepteur o/R)](../data-tools/datacontext-methods-o-r-designer.md) [procédure pas à pas : création de classes LINQ to SQL (concepteur o-r)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [opérations d’insertion, de mise à jour et de suppression](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
