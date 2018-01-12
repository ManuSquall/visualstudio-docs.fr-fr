---
title: "ListObject (contrôle) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2100a1c30fda5981d3d7e58f2f5077e0cdf87a2d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="listobject-control"></a>ListObject (contrôle)
  Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> est une liste qui expose des événements et qui peut être liée à des données. Quand vous ajoutez une liste à une feuille de calcul, Visual Studio crée un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> que vous pouvez programmer directement, sans devoir parcourir le modèle objet Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Création du contrôle  
 Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul au moment du design ou au moment de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> uniquement au moment de l’exécution. Pour plus d'informations, consultez [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Par défaut, les objets de liste créées dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> prend en charge la liaison de données simple et complexe. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être lié à une source de données à l’aide des propriétés <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> et <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> au moment du design ou à la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> au moment de l’exécution.  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Tools.Excel.ListObject> est mis à jour automatiquement lorsqu’il est lié à une source de données, telles qu’un <xref:System.Data.DataTable>, qui déclenche des événements lorsque les données sont modifiées. Si vous liez le <xref:Microsoft.Office.Tools.Excel.ListObject> à une source de données qui ne déclenche pas d’événements lorsque les données changent, vous devez appeler la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> ou <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> pour mettre à jour le <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Lorsque vous ajoutez un <xref:Microsoft.Office.Tools.Excel.ListObject> à une cellule de feuille de calcul en mappant un élément de schéma répétitif à cette cellule, Visual Studio mappe automatiquement le <xref:Microsoft.Office.Tools.Excel.ListObject> au dataset généré. Toutefois, le <xref:Microsoft.Office.Tools.Excel.ListObject> n’est pas lié automatiquement aux données. Vous pouvez prendre les mesures nécessaires pour lier le <xref:Microsoft.Office.Tools.Excel.ListObject> au dataset au moment du design ou au moment de l’exécution dans un projet au niveau du document. Vous pouvez lier par programmation le <xref:Microsoft.Office.Tools.Excel.ListObject> au dataset en cours d’exécution dans un complément VSTO.  
  
 Dans la mesure où les données sont séparées du <xref:Microsoft.Office.Tools.Excel.ListObject>, vous devez ajouter et supprimer des données via le dataset lié, et non pas directement via le <xref:Microsoft.Office.Tools.Excel.ListObject>. Si les données du dataset lié sont mises à jour via un mécanisme quelconque, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> reflète automatiquement les modifications. Pour plus d’informations, consultez [liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Vous pouvez remplir rapidement un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> en liant le <xref:Microsoft.Office.Tools.Excel.ListObject> à une source de données. Si vous modifiez les données d’un <xref:Microsoft.Office.Tools.Excel.ListObject>lié aux données, les modifications sont aussi apportées automatiquement à la source de données. Si vous souhaitez remplir un <xref:Microsoft.Office.Tools.Excel.ListObject> et permettre ensuite à l’utilisateur de modifier les données contenue dans le <xref:Microsoft.Office.Tools.Excel.ListObject> sans modifier la source de données, vous pouvez utiliser la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> pour détacher le <xref:Microsoft.Office.Tools.Excel.ListObject> de la source de données. Pour plus d’informations, consultez [Comment : remplir des contrôles ListObject données](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  La liaison de données n’est pas prise en charge sur des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> superposés.  
  
### <a name="improving-performance-in-listobject-controls"></a>Amélioration des performances dans les contrôles ListObject  
 La lecture d’un fichier XML dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données a tendance à être plus lente si vous liez d’abord le contrôle et que vous appelez ensuite <xref:System.Data.DataSet.ReadXml%2A> pour remplir le dataset. Pour améliorer les performances, appelez <xref:System.Data.DataSet.ReadXml%2A> avant de lier le contrôle.  
  
### <a name="disconnecting-listobject-controls-from-the-data-source"></a>Déconnexion des contrôles ListObject de la source de données  
 Après avoir rempli un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> avec des données en le liant à une source de données, vous pouvez le déconnecter afin que les modifications apportées aux données dans l’objet de liste n’affectent pas la source de données. Pour plus d’informations, consultez [Comment : remplir des contrôles ListObject données](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### <a name="restoring-column-and-row-order"></a>Restauration de l’ordre des colonnes et des lignes  
 Lorsque vous liez des données à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui a été ajouté à un document au moment du design, Visual Studio effectue le suivi de l’ordre des colonnes et des lignes à chaque enregistrement du classeur. Si un utilisateur déplace les colonnes ou les lignes du <xref:Microsoft.Office.Tools.Excel.ListObject> lors de l’exécution, le nouvel ordre est conservé à la prochaine ouverture du classeur et le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> se lie de nouveau à la source de données.  
  
 Si vous souhaitez rétablir l’ordre d’origine des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject> , vous pouvez appeler la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> . Cette méthode supprime les propriétés de document personnalisées liées à l’ordre des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject>spécifié. Appelez cette méthode à partir de l’événement <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> du classeur si vous ne souhaitez pas conserver l’ordre des colonnes et des lignes du <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## <a name="formatting"></a>Mise en forme  
 Une mise en forme qui peut être appliquée à un <xref:Microsoft.Office.Interop.Excel.ListObject> peut également être appliquée à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> . Cela inclut les bordures, les polices, le format de nombre et les styles. Les utilisateurs finaux peuvent réorganiser les colonnes dans un <xref:Microsoft.Office.Tools.Excel.ListObject>lié aux données, et ces modifications sont rendues persistantes dans le document, à condition que le <xref:Microsoft.Office.Tools.Excel.ListObject> ait été ajouté au document au moment du design. Lors de l’ouverture suivante du document, l’objet de liste est lié à la même source de données, mais l’ordre des colonnes reflète les modifications des utilisateurs.  
  
## <a name="adding-and-removing-columns-at-run-time"></a>Ajout et suppression de colonnes au moment de l’exécution  
 Au moment de l’exécution, vous ne pouvez pas ajouter ou supprimer manuellement des colonnes dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données. Si un utilisateur final essaie de supprimer une colonne, elle est immédiatement restaurée et toutes les colonnes ajoutées sont supprimées. Par conséquent, il est important d’écrire du code pour expliquer aux utilisateurs pourquoi ils ne peuvent pas exécuter ces actions sur un <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données. Visual Studio fournit plusieurs événements sur un <xref:Microsoft.Office.Tools.Excel.ListObject> relatif à la liaison de données. Par exemple, vous pouvez utiliser l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> pour avertir les utilisateurs que les données qu’ils ont tenté de supprimer ne peuvent pas l’être et qu’elles ont été restaurées.  
  
## <a name="adding-and-removing-rows-at-run-time"></a>Ajout et suppression de lignes au moment de l’exécution  
 Vous pouvez ajouter et supprimer manuellement des lignes dans un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données, à condition que la source de données autorise l’ajout de nouvelles lignes et qu’elle ne soit pas en lecture seule. Vous pouvez écrire du code par rapport à des événements tels que le <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> pour valider les données. Pour plus d'informations, consultez [How to: Validate Data When a New Row is Added to a ListObject Control](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Il arrive que la relation de l’objet de liste à la source de données provoque des erreurs habituelles. Par exemple, vous pouvez mapper les colonnes que vous souhaitez voir apparaître dans le <xref:Microsoft.Office.Tools.Excel.ListObject>; par conséquent, si vous omettez des colonnes qui comportent des restrictions, comme un champ qui n’accepte pas les valeurs Null, des erreurs sont retournées chaque fois qu’une ligne est créée. Vous pouvez écrire du code pour ajouter les valeurs manquantes dans un gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> .  
  
## <a name="renaming-listobject-controls-in-excel"></a>Attribution d’un nouveau nom aux contrôles ListObject dans Excel  
 Excel permet aux utilisateurs de modifier le nom des tableaux Excel au moment de l’exécution en utilisant l’onglet **Création** . Toutefois, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> ne prend pas en charge cette fonctionnalité. Si un utilisateur tente de renommer un tableau Excel correspondant à un <xref:Microsoft.Office.Tools.Excel.ListObject>, le nom d’origine du tableau Excel est automatiquement rétabli lors de l’enregistrement du classeur.  
  
## <a name="events"></a>Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> :  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>Voir aussi  
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Comment : mapper des colonnes ListObject aux données](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Comment : remplir de données des contrôles ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : remplir des feuilles de calcul avec des données à partir d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  