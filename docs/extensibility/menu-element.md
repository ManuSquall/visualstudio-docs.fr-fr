---
title: Élément du menu ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702598"
---
# <a name="menu-element"></a>Élément de menu
Définit un élément de menu. Ce sont les six types de menus: Contexte, Menu, MenuController, MenuControllerLatched, Toolbar, et ToolWindowToolbar.

## <a name="syntax"></a>Syntaxe

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identifiant de commande GUID/ID.|
|id|Obligatoire. ID de l’identifiant de commande GUID/ID.|
|priority|facultatif. Une valeur numérique qui spécifie la position relative d’un menu dans un groupe de menus.|
|ToolbarPriorityInBand|facultatif. Une valeur numérique qui spécifie la position relative d’une barre d’outils dans une bande lorsque la fenêtre est amarrée.|
|type|facultatif. Une valeur énumérée qui spécifie le genre d’élément.<br /><br /> S’il n’est pas présent, le type par défaut est Menu.<br /><br /> Context<br /> Un menu raccourci qui s’affiche lorsqu’un utilisateur clique à droite sur une fenêtre. Un menu raccourci présente les caractéristiques suivantes :<br /><br /> - N’utilise pas les champs **Parent** et **Priorité** lorsque le menu doit être affiché sous forme de menu raccourci.<br />- Peut être utilisé comme un sous-mois et aussi comme un menu raccourci. Dans ce cas, les domaines **d’identification de groupe** et **de priorité** sont respectés.<br />- N’est pas toujours disponible.<br /><br /> Un menu raccourci n’est affiché que lorsque les conditions suivantes sont vraies :<br /><br /> - La fenêtre qui l’héberge est affichée.<br />- Un gestionnaire de souris dans le VSPackage détecte un clic droit sur la fenêtre, puis appelle une méthode qui gère la commande.<br />- Le menu raccourci est <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> affiché en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> méthode (l’approche recommandée) ou la méthode.<br /><br /> Menu<br /> Fournit un menu de décrochage. Un menu déroulant a les caractéristiques suivantes :<br /><br /> - Respecte le Parent dans sa définition.<br />- Doit avoir un groupe parent, ou un CommandPlacement à un groupe.<br />- Peut être un sous-mois dans n’importe quel autre type de menu.<br />- Est automatiquement affiché chaque fois que son menu parent est affiché.<br />- N’exige pas la mise en œuvre d’un code VSPackage pour le rendre affiché.<br /><br /> MenuController<br /> Fournit un menu de décrochage à boutons partagés, qui est généralement utilisé dans les barres d’outils. Un menu De menucontroller a les caractéristiques suivantes :<br /><br /> - Doit être contenu dans un autre menu par l’intermédiaire de Parent ou CommandPlacement.<br />- Respecte le Parent dans sa définition.<br />- Peut avoir n’importe quel type de menu en tant que parent.<br />- Est automatiquement disponible chaque fois que son menu parent est affiché.<br />- Ne nécessite pas de soutien programmatique pour afficher le menu.<br /><br /> Une commande du menu bouton fendu s’affiche sur le bouton du menu. La commande affichée a l’une des caractéristiques suivantes :<br /><br /> - C’est la dernière commande qui a été utilisée si la commande est encore affichée et activée.<br />- C’est la première commande affichée.<br /><br /> MenuControllerLatched<br /> Fournit un menu déroulant à boutons partagés pour lequel une commande peut être spécifiée comme sélection par défaut en marquant la commande comme verrouillée.<br /><br /> Une commande verrouillée est une commande qui est marquée dans le menu tel que sélectionné, généralement en affichant une marque de contrôle. Une commande peut être marquée comme verrouillée si elle a le drapeau OLECMDF_LATCHED `QueryStatus` mis <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sur elle dans une mise en œuvre de la méthode de l’interface. Un menuControllerLatched a les caractéristiques suivantes :<br /><br /> - Doit être contenu dans un autre menu par l’intermédiaire d’un groupe Parent ou d’un CommandPlacement.<br />- Respecte le Parent dans sa définition.<br />- Peut avoir n’importe quel type de menu en tant que parent.<br />- Est disponible chaque fois que son menu parent est affiché.<br />- Ne nécessite pas de soutien programmatique pour afficher le menu.<br /><br /> Une commande du menu bouton fendu s’affiche sur le bouton du menu. La commande affichée a l’une des caractéristiques suivantes :<br /><br /> - C’est la première commande affichée qui est verrouillée.<br />- C’est la première commande affichée.<br /><br /> Barre d'outils<br /> Fournit une barre d’outils. Une barre d’outils a les caractéristiques suivantes :<br /><br /> - Ignore le parent dans sa définition.<br />- Ne peut pas être fait un sous-présage d’un groupe, pas même en utilisant CommandPlacement.<br />- Peut toujours être affiché en cliquant sur **les barres d’outils** sur le menu **View.**<br />- Peut être affiché à l’aide d’un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- N’a besoin d’aucun code pour le créer. Pour un exemple sur la façon de créer une barre d’outils, voir [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fournit une barre d’outils qui est attachée à une fenêtre d’outil spécifique, tout comme une barre d’outils est attachée à l’environnement de développement.<br /><br /> - Ignore le parent dans sa définition.<br />- Ne peut pas être fait un sous-présage d’un groupe, pas même en utilisant CommandPlacement.<br />- est affiché uniquement lorsque la fenêtre d’outil qui héberge la barre d’outils est affichée et le VSPackage ajoute explicitement la barre d’outils à la fenêtre d’outil. Ceci est généralement fait lorsque la fenêtre d’outil est créée en <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> obtenant la propriété d’hôte <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> de barre d’outils (représentée par l’interface) à partir du cadre de fenêtre d’outil, puis en appelant la méthode.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|facultatif. L’élément parent de l’élément menu.|
|CommandFlag (commandFlag)|Obligatoire. Voir [l’élément drapeau du Commandement](../extensibility/command-flag-element.md). Les valeurs commandflag valides pour un menu sont les suivantes :<br /><br /> -   **Toujourscréer**<br />-   **DéfautDocked**<br />-   **DefaultInvisible** - Ce drapeau n’affecte pas l’affichage des barres d’outils.<br />-   **DontCache (en)**<br />-   **DynamicVisibility** - Ce drapeau n’affecte pas l’affichage des barres d’outils.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose (noToolbarClose)**<br />-   **TextChanges TextChanges TextChanges TextChang**<br />-   **TextIsAnchorCommand**|
|Chaînes|Obligatoire. Voir [l’élément Cordes](../extensibility/strings-element.md). L’élément enfant `ButtonText` doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage met en œuvre.|

## <a name="example"></a>Exemple

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>Voir aussi
- [Table de commande Visual Studio (.vsct) Fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
