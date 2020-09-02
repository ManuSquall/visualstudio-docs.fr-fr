---
title: Contrôles de contenu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8683f5379aaa33446b150adf34f8a5aa57a83ff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986180"
---
# <a name="content-controls"></a>Contrôles de contenu
  Les contrôles de contenu vous permettent de concevoir des documents et des modèles qui ont les fonctionnalités suivantes :

- Une interface utilisateur dont les entrées sont contrôlées comme dans le cas d'un formulaire.

- Des restrictions qui empêchent les utilisateurs de modifier les sections protégées du document ou du modèle. Pour plus d’informations, consultez [protéger des parties de documents à l’aide de contrôles de contenu](#Protection).

- La liaison à une source de données. Pour plus d’informations, consultez [lier des données à des contrôles de contenu](#DataBinding).

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [liaison de données aux contrôles de contenu Word 2007 à l’aide de Visual Studio Tools pour Office System (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="overview-of-content-controls"></a>Vue d’ensemble des contrôles de contenu
 Les contrôles de contenu fournissent une interface utilisateur optimisée à la fois pour l'entrée d'utilisateur et pour l'impression. Lorsque vous ajoutez un contrôle de contenu à un document, le contrôle est identifié par une bordure, un titre et un texte temporaire qui peut fournir des instructions à l'utilisateur. La bordure et le titre du contrôle n'apparaissent pas dans les versions imprimées du document.

 Par exemple, si vous souhaitez que l'utilisateur entre une date dans une section de votre document, vous pouvez ajouter un contrôle du contenu de sélecteur de dates au document. Lorsque les utilisateurs cliquent sur le contrôle, l'interface utilisateur du sélecteur de dates standard s'affiche. Vous pouvez également définir les propriétés du contrôle de manière à configurer le calendrier régional affiché et à spécifier le format de date. Lorsque l'utilisateur a choisi une date, l'interface utilisateur du contrôle est masquée et seule la date apparaît si l'utilisateur imprime le document.

 Les contrôles de contenu vous aident également à effectuer les opérations suivantes :

- Empêcher les utilisateurs de modifier ou de supprimer des parties d'un document. Cela peut s'avérer utile si votre document ou modèle contient des informations que les utilisateurs doivent pouvoir lire mais pas modifier, ou si vous souhaitez que les utilisateurs puissent modifier des contrôles de contenu mais pas les supprimer.

- Lier des parties d'un document ou d'un modèle à des données. Vous pouvez lier des contrôles de contenu à des champs de base de données, à des objets managés dans le [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], à des éléments XML stockés dans le document et à d'autres sources de données.

  Dans les projets au niveau du document, vous pouvez ajouter des contrôles de contenu à votre document au moment du design ou au moment de l'exécution. Dans les projets VSTO, vous pouvez ajouter des contrôles de contenu à tout document ouvert au moment de l’exécution. Pour plus d’informations, consultez [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).

> [!NOTE]
> Vous pouvez utiliser les contrôles de contenu uniquement dans les documents enregistrés au format Open XML. Vous ne pouvez pas utiliser de contrôles de contenu dans les documents enregistrés au format de document Word 97-2003 (*. doc*).

## <a name="types-of-content-controls"></a>Types de contrôles de contenu
 Vous pouvez ajouter neuf types de contrôles de contenu différents à des documents. La plupart des contrôles de contenu disposent d'un type correspondant dans l'espace de noms <xref:Microsoft.Office.Tools.Word>. Vous avez également la possibilité d'utiliser un <xref:Microsoft.Office.Tools.Word.ContentControl> générique, qui peut représenter l'un des contrôles de contenu disponibles. Pour obtenir une procédure pas à pas qui montre comment utiliser chacun des contrôles de contenu disponibles, consultez [procédure pas à pas : créer un modèle à l’aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

### <a name="build-block-gallery"></a>Galerie de bloc de build
 Une galerie de blocs de construction permet aux utilisateurs de sélectionner dans une liste de *blocs de construction de document* à insérer dans un document. Un bloc de construction de document est une partie de contenu créée pour être utilisée plusieurs fois, telle qu'une page de garde commune, un tableau mis en forme ou un en-tête. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>. Pour plus d’informations sur les blocs de construction, consultez [nouveautés pour les développeurs dans Word 2007](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).

### <a name="check-box"></a>Case à cocher
 Une case à cocher fournit une interface utilisateur qui représente un état binaire : coché ou décoché.

 Contrairement aux autres types de contrôles de contenu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ne fournit pas de type spécifique qui représente un contrôle de contenu de case à cocher. En d'autres termes, il n'existe pas de type `CheckBoxContentControl`. Toutefois, vous pouvez créer un contrôle de contenu de case à cocher en ajoutant par programmation un <xref:Microsoft.Office.Tools.Word.ContentControl> générique à un document. Pour plus d’informations, consultez [contrôles de contenu de case à cocher dans les projets Word](#checkbox).

### <a name="combo-box"></a>Combo box
 Une zone de liste modifiable affiche une liste d'éléments que les utilisateurs peuvent sélectionner. Contrairement à une liste déroulante, la zone de liste modifiable permet aux utilisateurs d'ajouter leurs propres éléments. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.

### <a name="date-picker"></a>Sélecteur de dates
 Un sélecteur de dates fournit une interface utilisateur de calendrier permettant de sélectionner une date. Le calendrier s’affiche lorsque l’utilisateur final clique sur la flèche déroulante vers le bas dans le contrôle. Vous pouvez utiliser des calendriers régionaux et des formats de date différents. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.

### <a name="drop-down-list"></a>Liste déroulante
 Une liste déroulante affiche la liste des éléments que les utilisateurs peuvent sélectionner. Contrairement à une zone de liste modifiable, la liste déroulante ne permet pas aux utilisateurs d’ajouter ou de modifier des éléments. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>.

### <a name="group"></a>Grouper
 Un contrôle de groupe définit une zone protégée d'un document que les utilisateurs ne peuvent pas modifier ou supprimer. Un contrôle de groupe peut contenir tous types d'éléments de document : du texte, des tableaux, des graphiques et d'autres contrôles de contenu. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

### <a name="picture"></a>Photo
 Un contrôle d'image affiche une image. Vous pouvez spécifier l'image au moment du design ou au moment de l'exécution, ou les utilisateurs peuvent cliquer sur ce contrôle pour sélectionner une image à insérer dans le document. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.PictureContentControl>.

### <a name="rich-text"></a>Texte enrichi
 Un contrôle de texte enrichi contient du texte ou d'autres éléments, comme des tableaux, des images ou d'autres contrôles de contenu. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.

### <a name="plain-text"></a>Texte brut
 Un contrôle de texte brut contient du texte. Un contrôle de texte brut ne peut pas contenir d'autres éléments, comme des tableaux, des images ou d'autres contrôles de contenu. En outre, tout le texte d'un contrôle de texte brut a la même mise en forme. Par exemple, si vous mettez en italique un mot d'une phrase contenue dans un contrôle de texte brut, tout le texte à l'intérieur du contrôle est mis en italique. Pour plus d'informations, consultez le type <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>.

### <a name="generic-content-control"></a>Contrôle de contenu générique
 Un contrôle de contenu générique est un objet <xref:Microsoft.Office.Tools.Word.ContentControl> qui peut représenter l'un des types de contrôles de contenu disponibles. Vous pouvez utiliser la propriété <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> pour modifier un objet <xref:Microsoft.Office.Tools.Word.ContentControl> de manière à ce qu'il se comporte comme un autre type de contrôle de contenu. Par exemple, si vous créez un objet <xref:Microsoft.Office.Tools.Word.ContentControl> qui représente un contrôle de texte brut, vous pouvez le modifier au moment de l'exécution afin qu'il se comporte comme une zone de liste modifiable.

 Vous pouvez créer des objets <xref:Microsoft.Office.Tools.Word.ContentControl> uniquement au moment de l'exécution, et pas au moment du design. Pour plus d’informations, consultez [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).

## <a name="common-features-of-content-controls"></a>Fonctionnalités courantes des contrôles de contenu
 La plupart des contrôles de contenu partagent un ensemble de membres que vous pouvez utiliser pour exécuter des tâches courantes. Le tableau suivant décrit quelques-unes des tâches que vous pouvez effectuer à l'aide de ces membres.

|Pour cette tâche :|Procédez comme suit :|
|--------------------|--------------|
|Obtenir ou définir le texte affiché dans le contrôle|Utilisez la propriété **Text** . **Remarque :**  Les <xref:Microsoft.Office.Tools.Word.PictureContentControl> <xref:Microsoft.Office.Tools.Word.ContentControl> types et n’ont pas cette propriété.|
|Obtenir ou définir le texte temporaire affiché dans le contrôle jusqu'à ce qu'un utilisateur modifie le contrôle, que le contrôle soit rempli avec les données d'une source de données ou que le contenu du contrôle soit supprimé.|Utilisez la propriété **PlaceholderText** . **Remarque :**  Le <xref:Microsoft.Office.Tools.Word.PictureContentControl> type n’a pas cette propriété.|
|Obtenir ou définir le titre affiché dans la bordure du contrôle de contenu lorsque l'utilisateur clique sur ce dernier.|Utilisez la propriété **title** .|
|Supprimer automatiquement le contrôle du document après que l'utilisateur a modifié le contrôle. (Le texte du contrôle reste dans le document.)|Utilisez la propriété **Temporary** .|
|Exécuter le code lorsque l'utilisateur clique dans le contrôle de contenu ou lorsque le curseur est déplacé par programmation dans le contrôle de contenu.|Gérez l'événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> du contrôle.|
|Exécuter le code lorsque l'utilisateur clique en dehors du contrôle de contenu ou lorsque le curseur est déplacé par programmation en dehors du contrôle de contenu.|Gérez l'événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> du contrôle.|
|Exécuter le code après que le contrôle de contenu a été ajouté au document à la suite d'une opération de rétablissement ou d'annulation.|Gérez l'événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> du contrôle.|
|Exécutez le code juste avant que le contrôle de contenu soit supprimé du document.|Gérez l'événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> du contrôle.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> Protéger des parties de documents à l’aide de contrôles de contenu
 Lorsque vous protégez une partie d'un document, vous empêchez les utilisateurs de modifier ou de supprimer le contenu dans cette partie du document. Il existe plusieurs manières de protéger des parties d'un document à l'aide de contrôles de contenu.

 Si la zone que vous souhaitez protéger se trouve à l'intérieur d'un contrôle de contenu, vous pouvez utiliser les propriétés du contrôle de contenu pour empêcher des utilisateurs de modifier ou de supprimer le contrôle :

- La propriété **LockContents** empêche les utilisateurs de modifier le contenu.

- La propriété **LockContentControl** empêche les utilisateurs de supprimer le contrôle.

  Si la zone que vous souhaitez protéger ne se trouve pas à l'intérieur d'un contrôle de contenu, ou si vous souhaitez protéger une zone qui contient des contrôles de contenu et d'autres types de contenu, vous pouvez placer la zone entière dans un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Contrairement à d'autres contrôles de contenu, un <xref:Microsoft.Office.Tools.Word.GroupContentControl> ne fournit aucune interface utilisateur visible par l'utilisateur. Son seul but est de définir une zone que les utilisateurs ne peuvent pas modifier.

> [!NOTE]
> Si vous créez un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient des contrôles de contenu incorporés, ces contrôles ne sont pas protégés automatiquement. Vous devez utiliser la propriété **LockContents** de chaque contrôle incorporé pour empêcher les utilisateurs de modifier leur contenu.

 Pour plus d’informations sur l’utilisation des contrôles de contenu pour protéger des parties de documents, consultez [Comment : protéger des parties de documents à l’aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> Lier des données à des contrôles de contenu
 Vous pouvez afficher des données dans des documents en liant un contrôle de contenu à une source de données. Lorsque la source de données est mise à jour, le contrôle de contenu reflète les modifications apportées. Vous pouvez également enregistrer les modifications dans la source de données.

 Les contrôles de contenu fournissent les options de liaison des données suivantes :

- Vous pouvez lier des contrôles de contenu à des champs de base de données ou à des objets managés en utilisant le même modèle de liaison de données que Windows Forms.

- Vous pouvez lier des contrôles de contenu à des éléments de morceaux de code XML (également appelés *parties XML personnalisées*) incorporés dans le document.

  Pour obtenir une vue d’ensemble de la liaison de contrôles hôtes aux données dans les solutions Office, consultez [liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="use-the-windows-forms-data-binding-model"></a>Utiliser le modèle de liaison de données Windows Forms
 La plupart des contrôles de contenu prennent en charge le modèle de liaison de données simple que Windows Forms utilise. La liaison de données simple signifie qu'un contrôle est lié à un élément de données unique, tel qu'une valeur dans une colonne d'une table de données. Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Dans les projets au niveau du document, vous pouvez lier des données à des contrôles de contenu à l’aide de la fenêtre **sources de données** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour plus d’informations sur l’ajout de contrôles de contenu liés aux données à des documents, consultez [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md) et [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md).

 Le tableau suivant répertorie les contrôles de contenu que vous pouvez lier à chaque type de données dans la fenêtre **sources de données** .

|Type de données|Contrôle de contenu par défaut|Autres contrôles de contenu qui peuvent être liés à ce type de données|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> tableau|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|None|

 Dans les projets au niveau du document et les projets de complément VSTO, vous pouvez lier par programmation un contrôle de contenu à une source de données en utilisant la méthode <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la propriété <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> du contrôle. Si vous procédez ainsi, transmettez le **texte** de chaîne au paramètre *PropertyName* de la <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> méthode. La propriété **Text** est la propriété de liaison de données par défaut des contrôles de contenu.

 Les contrôles de contenu prennent également en charge la liaison de données bidirectionnelle, dans laquelle les modifications apportées au contrôle sont répercutées dans la source de données. Pour plus d’informations, consultez [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

> [!NOTE]
> Les contrôles de contenu ne prennent pas en charge la liaison de données complexe. Si vous liez un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ou un <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> à une source de données à l'aide du modèle de données Windows Forms, les utilisateurs ne verront qu'une seule valeur lorsqu'ils cliqueront sur le contrôle. Si vous voulez lier ces contrôles à une série de valeurs données à partir de laquelle les utilisateurs peuvent choisir, vous pouvez lier ces contrôles à des éléments d'une partie XML personnalisée.

### <a name="bind-content-controls-to-custom-xml-parts"></a>Lier des contrôles de contenu à des parties XML personnalisées
 Vous pouvez lier des contrôles de contenu à des éléments dans des parties XML personnalisées qui sont incorporées dans le document. Pour plus d’informations sur les parties XML personnalisées, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

 Pour lier un contrôle de contenu à un élément dans une partie XML personnalisée, utilisez la propriété **XMLMapping** du contrôle. L'exemple de code suivant montre comment lier un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> à l'élément `Price` sous le nœud `Product` dans une partie XML personnalisée qui a déjà été ajoutée au document.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 Pour obtenir une procédure pas à pas qui montre comment lier des contrôles de contenu à des parties XML personnalisées plus en détail, consultez [procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

 Lorsque vous liez un contrôle de contenu à une partie XML personnalisée, la liaison de données bidirectionnelle est automatiquement activée. Si un utilisateur modifie le texte dans le contrôle, les éléments XML correspondants sont automatiquement mis à jour. De la même façon, si les valeurs d'élément dans les parties XML personnalisées sont modifiées, les contrôles de contenu liés aux éléments XML afficheront les nouvelles données.

 Vous pouvez lier les types de contrôles de contenu suivants à des parties XML personnalisées :

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>Événements de liaison de données pour les contrôles de contenu
 Tous les contrôles de contenu fournissent un jeu des événements que vous pouvez gérer afin d'effectuer des tâches liées aux données, par exemple pour vérifier que le texte d'un contrôle répond à certains critères avant que la source de données soit mise à jour. Le tableau suivant répertorie les événements de contrôle de contenu associés à la liaison de données.

|Tâche|Événement|
|----------|-----------|
|Exécuter le code juste avant que Word mette automatiquement à jour le texte d'un contrôle de contenu lié à une partie XML personnalisée.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Exécuter le code juste avant que Word mette automatiquement à jour les données dans une partie XML personnalisée liée à un contrôle de contenu (autrement dit, après que le texte du contrôle de contenu a été modifié).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Exécuter votre propre code pour valider le contenu du contrôle en fonction de critères personnalisés.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Exécuter le code après que le contenu du contrôle a été validé avec succès.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>Limitations des contrôles de contenu
 Lorsque vous utilisez des contrôles de contenu dans vos projets Office, vous devez garder à l'esprit les limitations suivantes.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Différences de comportement entre le moment de la conception et le Runtime
 Un grand nombre des limitations que Microsoft Office Word impose aux contrôles de contenu au moment de l'exécution ne sont pas appliquées au moment du design. Lorsque vous concevez l'interface utilisateur d'une solution au niveau du document dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], veillez à n'apporter aux contrôles de contenu que des modifications susceptibles d'être prises en charge au moment de l'exécution.

 Si vous modifiez un contrôle de contenu au moment du design d'une façon que le contrôle ne prend pas en charge au moment de l'exécution, le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne vous signalera pas les modifications non prises en charge. Toutefois, lorsque vous déboguez ou exécutez le projet, ou si vous enregistrez puis rouvrez le projet, Word affichera un message d'erreur et demandera l'autorisation de réparer le document. Lorsque vous réparez le document, Word supprime du contrôle tout le contenu et toute la mise en forme non pris en charge.

 Par exemple, Word ne vous empêche pas d'ajouter un tableau à un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> au moment du design. Cependant, comme les objets <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> ne peuvent pas contenir de tableaux au moment de l'exécution, Word affichera un message d'erreur à l'ouverture du document.

 Notez également que de nombreuses propriétés qui définissent le comportement des contrôles de contenu n'ont aucun effet au moment du design. Par exemple, si vous affectez la valeur **true** à la propriété **LockContents** d’un contrôle de contenu au moment du design, vous pouvez toujours modifier le texte dans le contrôle dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Concepteur. Cette propriété empêche seulement les utilisateurs de modifier le contrôle au moment de l'exécution.

### <a name="event-limitations"></a>Limitations des événements
 Les contrôles de contenu ne fournissent pas un événement déclenché lorsque l'utilisateur modifie le texte ou d'autres éléments dans le contrôle. Par exemple, aucun événement n'est déclenché lorsqu'un utilisateur sélectionne un autre élément dans un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ou un <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.

 Pour déterminer quand un utilisateur modifie le contenu d'un contrôle de contenu, vous pouvez lier le contrôle à une partie XML personnalisée, puis gérer l'événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>. Cet événement est déclenché lorsque l'utilisateur modifie le contenu d'un contrôle lié à une partie XML personnalisée. Pour obtenir une procédure pas à pas qui montre comment lier un contrôle de contenu à une partie XML personnalisée, consultez [procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Contrôles de contenu de case à cocher dans les projets Word
 Word 2010 a introduit un nouveau type de contrôle de contenu représentant une case à cocher. Toutefois, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ne fournit pas de type CheckBoxContentControl correspondant que vous pouvez utiliser dans les projets Office. Pour créer un contrôle de contenu de case à cocher dans un projet [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou Word 2010, utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> pour créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl>, puis passez la valeur <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> à la méthode pour spécifier un contrôle de contenu de case à cocher. L'exemple de code suivant montre comment procéder.

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procédure pas à pas : création d’un modèle à l’aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
