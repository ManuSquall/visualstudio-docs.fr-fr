---
title: ListObject (contrôle)
description: Le contrôle ListObject est une liste qui expose des événements et qui peut être liée à des données. En outre, vous pouvez ajouter des contrôles ListObject à une feuille de calcul au moment du design ou au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: becc4ab189c0f871cc3ed1284bd26a0411b30184
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849799"
---
# <a name="listobject-control"></a>ListObject (contrôle)
  Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> est une liste qui expose des événements et qui peut être liée à des données. Quand vous ajoutez une liste à une feuille de calcul, Visual Studio crée un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> que vous pouvez programmer directement, sans devoir parcourir le modèle objet Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Créer le contrôle
 Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul au moment du design ou au moment de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> uniquement au moment de l’exécution. Pour plus d’informations, consultez [Comment : ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> Par défaut, les objets de liste créées dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> prend en charge la liaison de données simple et complexe. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être lié à une source de données à l’aide des propriétés <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> et <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> au moment du design ou à la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> au moment de l’exécution.

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Excel.ListObject> est mis à jour automatiquement lorsqu’il est lié à une source de données, telles qu’un <xref:System.Data.DataTable>, qui déclenche des événements lorsque les données sont modifiées. Si vous liez le <xref:Microsoft.Office.Tools.Excel.ListObject> à une source de données qui ne déclenche pas d’événements lorsque les données changent, vous devez appeler la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> ou <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> pour mettre à jour le <xref:Microsoft.Office.Tools.Excel.ListObject>.

 Lorsque vous ajoutez un <xref:Microsoft.Office.Tools.Excel.ListObject> à une cellule de feuille de calcul en mappant un élément de schéma répétitif à cette cellule, Visual Studio mappe automatiquement le <xref:Microsoft.Office.Tools.Excel.ListObject> au dataset généré. Toutefois, le <xref:Microsoft.Office.Tools.Excel.ListObject> n’est pas lié automatiquement aux données. Vous pouvez prendre les mesures nécessaires pour lier le <xref:Microsoft.Office.Tools.Excel.ListObject> au dataset au moment du design ou au moment de l’exécution dans un projet au niveau du document. Vous pouvez lier par programmation le <xref:Microsoft.Office.Tools.Excel.ListObject> au DataSet au moment de l’exécution dans un complément VSTO.

 Dans la mesure où les données sont séparées du <xref:Microsoft.Office.Tools.Excel.ListObject>, vous devez ajouter et supprimer des données via le dataset lié, et non pas directement via le <xref:Microsoft.Office.Tools.Excel.ListObject>. Si les données du dataset lié sont mises à jour via un mécanisme quelconque, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> reflète automatiquement les modifications. Pour plus d’informations, consultez [lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Vous pouvez remplir rapidement un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> en liant le <xref:Microsoft.Office.Tools.Excel.ListObject> à une source de données. Si vous modifiez les données d’un <xref:Microsoft.Office.Tools.Excel.ListObject>lié aux données, les modifications sont aussi apportées automatiquement à la source de données. Si vous souhaitez remplir un <xref:Microsoft.Office.Tools.Excel.ListObject> et permettre ensuite à l’utilisateur de modifier les données contenue dans le <xref:Microsoft.Office.Tools.Excel.ListObject> sans modifier la source de données, vous pouvez utiliser la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> pour détacher le <xref:Microsoft.Office.Tools.Excel.ListObject> de la source de données. Pour plus d’informations, consultez [Comment : remplir des contrôles ListObject avec des données](../vsto/how-to-fill-listobject-controls-with-data.md).

> [!NOTE]
> La liaison de données n’est pas prise en charge sur des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> superposés.

### <a name="improve-performance-in-listobject-controls"></a>Améliorer les performances dans les contrôles ListObject
 La lecture d’un fichier XML dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données a tendance à être plus lente si vous liez d’abord le contrôle et que vous appelez ensuite <xref:System.Data.DataSet.ReadXml%2A> pour remplir le dataset. Pour améliorer les performances, appelez <xref:System.Data.DataSet.ReadXml%2A> avant de lier le contrôle.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Déconnecter les contrôles ListObject de la source de données
 Après avoir rempli un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> avec des données en le liant à une source de données, vous pouvez le déconnecter afin que les modifications apportées aux données dans l’objet de liste n’affectent pas la source de données. Pour plus d’informations, consultez [Comment : remplir des contrôles ListObject avec des données](../vsto/how-to-fill-listobject-controls-with-data.md).

### <a name="restore-column-and-row-order"></a>Restaurer l’ordre des colonnes et des lignes
 Lorsque vous liez des données à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui a été ajouté à un document au moment du design, Visual Studio effectue le suivi de l’ordre des colonnes et des lignes à chaque enregistrement du classeur. Si un utilisateur déplace les colonnes ou les lignes du <xref:Microsoft.Office.Tools.Excel.ListObject> lors de l’exécution, le nouvel ordre est conservé à la prochaine ouverture du classeur et le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> se lie de nouveau à la source de données.

 Si vous souhaitez rétablir l’ordre d’origine des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject> , vous pouvez appeler la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> . Cette méthode supprime les propriétés de document personnalisées liées à l’ordre des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject>spécifié. Appelez cette méthode à partir de l’événement <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> du classeur si vous ne souhaitez pas conserver l’ordre des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject>.

## <a name="format"></a>Format
 Une mise en forme qui peut être appliquée à <xref:Microsoft.Office.Interop.Excel.ListObject> peut également être appliquée à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> . Cela inclut les bordures, les polices, le format de nombre et les styles. Les utilisateurs finaux peuvent réorganiser les colonnes dans un lié aux données <xref:Microsoft.Office.Tools.Excel.ListObject> , et ces modifications sont conservées avec le document, à condition que le <xref:Microsoft.Office.Tools.Excel.ListObject> ait été ajouté au document au moment du Design. Lors de l’ouverture suivante du document, l’objet de liste est lié à la même source de données, mais l’ordre des colonnes reflète les modifications des utilisateurs.

## <a name="add-and-remove-columns-at-run-time"></a>Ajouter et supprimer des colonnes au moment de l’exécution
 Au moment de l’exécution, vous ne pouvez pas ajouter ou supprimer manuellement des colonnes dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données. Si un utilisateur final tente de supprimer une colonne, celle-ci est immédiatement restaurée et toutes les colonnes ajoutées sont supprimées. Par conséquent, il est important d’écrire du code pour expliquer aux utilisateurs pourquoi ils ne peuvent pas exécuter ces actions sur un <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données. Visual Studio fournit plusieurs événements sur un <xref:Microsoft.Office.Tools.Excel.ListObject> relatif à la liaison de données. Par exemple, vous pouvez utiliser l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> pour avertir les utilisateurs que les données qu’ils ont tenté de supprimer ne peuvent pas l’être et qu’elles ont été restaurées.

## <a name="add-and-remove-rows-at-run-time"></a>Ajouter et supprimer des lignes au moment de l’exécution
 Vous pouvez ajouter et supprimer manuellement des lignes dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données, à condition que la source de données autorise l’ajout de nouvelles lignes et qu’elle ne soit pas en lecture seule. Vous pouvez écrire du code par rapport à des événements tels que le <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> pour valider les données. Pour plus d’informations, consultez [Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).

 Il arrive que la relation de l’objet de liste à la source de données provoque des erreurs habituelles. Par exemple, vous pouvez mapper les colonnes que vous souhaitez voir apparaître dans le <xref:Microsoft.Office.Tools.Excel.ListObject>; par conséquent, si vous omettez des colonnes qui comportent des restrictions, comme un champ qui n’accepte pas les valeurs Null, des erreurs sont retournées chaque fois qu’une ligne est créée. Vous pouvez écrire du code pour ajouter les valeurs manquantes dans un gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> .

## <a name="rename-listobject-controls-in-excel"></a>Renommer des contrôles ListObject dans Excel
 Excel permet aux utilisateurs de modifier le nom des tableaux Excel au moment de l’exécution à l’aide de l’onglet **conception** . Toutefois, le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle ne prend pas en charge cette fonctionnalité. Si un utilisateur tente de renommer un tableau Excel correspondant à un <xref:Microsoft.Office.Tools.Excel.ListObject>, le nom d’origine du tableau Excel est automatiquement rétabli lors de l’enregistrement du classeur.

## <a name="events"></a>Événements
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> :

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Voir aussi
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Comment : ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Comment : redimensionner des contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Comment : mapper des colonnes ListObject à des données](../vsto/how-to-map-listobject-columns-to-data.md)
- [Comment : remplir des contrôles ListObject avec des données](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Comment : remplir des feuilles de calcul avec des données d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
