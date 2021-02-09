---
title: Bookmark (contrôle)
description: Découvrez comment le contrôle Bookmark est un signet qui a un nom unique, qui expose des événements et qui peut être lié à des données.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1da30943eff228aad3c5413c5d8faea337634e9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905255"
---
# <a name="bookmark-control"></a>Bookmark (contrôle)
  Le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> est un signet qui possède un nom unique, qui expose des événements et qui peut être lié à des données. Vous pouvez utiliser le signet comme espace réservé pour marquer un élément ou un emplacement dans un document Microsoft Office Word. Le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> est une combinaison d’un objet <xref:Microsoft.Office.Interop.Word.Bookmark> et d’un objet <xref:Microsoft.Office.Interop.Word.Range> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> à votre document au moment du design ou au moment de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> à tout document ouvert au moment de l’exécution. Pour plus d’informations, consultez [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> prend en charge la liaison de données simple. Le signet doit être lié à une source de données à l’aide de la propriété <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . La propriété de liaison de données par défaut du signet est la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .

 Si les données du dataset lié sont mises à jour, le <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle affiche les modifications.

 Dans les projets au niveau du document, vous pouvez également lier des données à des signets via la fenêtre **Sources de données** . Pour plus d’informations, consultez [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Mise en forme
 Une mise en forme qui peut être appliquée à <xref:Microsoft.Office.Interop.Word.Bookmark> peut également être appliquée à un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> . Cette mise en forme comprend les polices, les retraits, l’espacement, la numérotation et les styles.

## <a name="assign-text-to-the-bookmark"></a>Assigner du texte au signet
 Il existe une différence supplémentaire entre un objet <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> et un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> . Il s’agit du comportement observé quand vous assignez du texte au signet. Si vous assignez du texte à un <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>de longueur nulle, ce texte est ajouté à droite du signet. Par ailleurs, le signet conserve une longueur nulle. Toutefois, si vous assignez du texte à un <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>de longueur nulle, le texte est inséré dans le signet. Par ailleurs, la longueur du signet se développe en fonction du nombre total de caractères insérés.

 Le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> possède également la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> . Cette propriété est différente de la <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> propriété qui est disponible sur la <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> propriété d’un <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> contrôle ou la <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> propriété d’un <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objet.

|Text (propriété)|Description|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Utilisez cette propriété pour afficher le texte contenu dans le signet, et laisser le signet dans le document. L’assignation de texte au signet développe la plage du signet et ne supprime pas le signet.<br /><br /> Par exemple, `Bookmark1.Text = "Hello world"` insère le texte dans le signet et laisse le signet intact.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Utilisez cette propriété pour afficher du texte à l’emplacement du signet et supprimer automatiquement le signet. Par exemple, `Bookmark1.Range.Text = "Hello world"` insère le texte dans le signet et supprime le signet.|

## <a name="rename-the-control-at-design-time"></a>Renommer le contrôle au moment du design
 Dans les projets au niveau du document, quand vous faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> de la **Boîte à outils** vers votre document, Visual Studio génère automatiquement un nom pour le contrôle. Vous pouvez changer le nom du contrôle dans la fenêtre **Propriétés** .

## <a name="overlapping-controls"></a>Chevauchement de contrôles
 Les contrôles Bookmark peuvent se chevaucher. Le même texte peut être partagé par plusieurs signets. Quand vous assignez un nouveau texte à l’un des signets qui se chevauchent, il contient uniquement le nouveau texte et les signets ne se chevauchent plus. L’autre signet contient désormais uniquement le texte qui n’était pas partagé entre les signets qui se chevauchaient à l’origine.

 Le tableau suivant montre comment la phrase « Voici un exemple textuel. » est partagé par deux signets qui se chevauchent :

|Signet|Texte|
|--------------|----------|
|Chevauchement de signets|[voici un {exemple] textuel.}|
|Signet1|Voici un exemple|
|Signet2|exemple textuel.|

 Si vous assignez le nouveau texte « Voici un remplacement. » au Bookmark1, les signets ne se chevauchent pas et Bookmark2 conserve uniquement le texte qui n’était pas initialement inclus dans Bookmark1.

|Signet|Texte|
|--------------|----------|
|Deux signets séparés|[voici un remplacement]{ textuel.}|
|Signet1|Voici un remplacement|
|Signet2|textuel.|

Si vous modifiez le texte d’un signet qui contient un autre signet, le signet interne n’est pas supprimé. Toutefois, le signet interne devient un signet vide et se déplace à la fin du signet externe.

Le tableau suivant montre comment la phrase « Voici un exemple textuel. » est partagée par un signet contenu dans un autre signet :

|Signet|Texte|
|--------------|----------|
|Chevauchement de signets|[voici un {exemple} textuel.]|
|Signet1|Voici un exemple textuel.|
|Signet2|sample|

 Si vous assignez le nouveau texte « Voici un remplacement. » à Signet1, les signets ne se chevauchent plus. Par ailleurs, Signet2 devient un signet vide situé à la fin de Signet1.

|Signet|Texte|
|--------------|----------|
|Deux signets séparés|[il s’agit du remplacement.]{}|
|Signet1|Voici un remplacement.|
|Signet2|*\<empty>*|

## <a name="events"></a>Événements

Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> :

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Voir aussi

- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Procédure pas à pas : créer des menus contextuels pour les signets](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)