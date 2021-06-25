---
title: Menu, élément | Microsoft Docs
description: L’élément de menu définit un élément de menu. Les types de menu sont Context, menu, MenuController, MenuControllerLatched, Toolbar et ToolWindowToolbar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2ffa029dd05e7fe3d32a9df4a1d06c90c8b9c6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901537"
---
# <a name="menu-element"></a>Élément menu
Définit un élément de menu. Il s’agit des six types de menus : Context, menu, MenuController, MenuControllerLatched, Toolbar et ToolWindowToolbar.

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
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.|
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|
|priority|Optionnel. Valeur numérique qui spécifie la position relative d’un menu dans un groupe de menus.|
|ToolbarPriorityInBand|Optionnel. Valeur numérique qui spécifie la position relative d’une barre d’outils dans une bande lorsque la fenêtre est ancrée.|
|type|Optionnel. Valeur énumérée qui spécifie le genre d’élément.<br /><br /> S’il n’est pas présent, le type par défaut est menu.<br /><br /> Contexte<br /> Menu contextuel qui s’affiche lorsqu’un utilisateur clique avec le bouton droit sur une fenêtre. Un menu contextuel présente les caractéristiques suivantes :<br /><br /> -N’utilise pas les champs **parent** et de **priorité** lorsque le menu doit être affiché sous la forme d’un menu contextuel.<br />-Peut être utilisé comme sous-menu et également comme menu contextuel. Dans ce cas, les champs **ID de groupe** et **priorité** sont respectés.<br />-N’est pas toujours disponible.<br /><br /> Un menu contextuel s’affiche uniquement lorsque les conditions suivantes sont remplies :<br /><br /> -La fenêtre qui l’héberge s’affiche.<br />: Un gestionnaire de souris dans le VSPackage détecte un clic droit sur la fenêtre, puis appelle une méthode qui gère la commande.<br />-Le menu contextuel s’affiche en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> méthode (l’approche recommandée) ou la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> méthode.<br /><br /> Menu<br /> Fournit un menu déroulant. Un menu déroulant présente les caractéristiques suivantes :<br /><br /> -Respecte le parent dans sa définition.<br />-Doit avoir un groupe parent, ou un Commandplacement ayant à un groupe.<br />-Peut être un sous-menu dans tout autre type de menu.<br />-S’affiche automatiquement chaque fois que son menu parent est affiché.<br />-Ne requiert pas l’implémentation de tout code VSPackage pour le rendre affiché.<br /><br /> MenuController<br /> Fournit un menu déroulant de bouton partagé, qui est généralement utilisé dans les barres d’outils. Un menu MenuController présente les caractéristiques suivantes :<br /><br /> -Doit être contenu dans un autre menu via parent ou Commandplacement ayant.<br />-Respecte le parent dans sa définition.<br />-Peut avoir n’importe quel type de menu comme parent.<br />-Est automatiquement mis à disposition chaque fois que son menu parent est affiché.<br />-Ne nécessite pas de prise en charge par programmation pour afficher le menu.<br /><br /> Une commande du menu du bouton partagé s’affiche sur le bouton de menu. La commande affichée présente l’une des caractéristiques suivantes :<br /><br /> -Il s’agit de la dernière commande qui a été utilisée si la commande est toujours affichée et activée.<br />-Il s’agit de la première commande affichée.<br /><br /> MenuControllerLatched<br /> Fournit un menu déroulant de bouton partagé pour lequel une commande peut être spécifiée en tant que sélection par défaut en marquant la commande comme étant verrouillée.<br /><br /> Une commande verrouillée est une commande marquée dans le menu sélectionné, généralement en affichant une coche. Une commande peut être marquée comme verrouillée si l’indicateur OLECMDF_LATCHED est défini dans une implémentation de la `QueryStatus` méthode de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Un menu MenuControllerLatched présente les caractéristiques suivantes :<br /><br /> -Doit être contenu dans un autre menu par le biais d’un groupe parent ou d’un Commandplacement ayant.<br />-Respecte le parent dans sa définition.<br />-Peut avoir n’importe quel type de menu comme parent.<br />-Est rendu disponible chaque fois que son menu parent est affiché.<br />-Ne nécessite pas de prise en charge par programmation pour afficher le menu.<br /><br /> Une commande du menu du bouton partagé s’affiche sur le bouton de menu. La commande affichée présente l’une des caractéristiques suivantes :<br /><br /> -Il s’agit de la première commande affichée qui est verrouillée.<br />-Il s’agit de la première commande affichée.<br /><br /> Barre d’outils<br /> Fournit une barre d’outils. Une barre d’outils présente les caractéristiques suivantes :<br /><br /> -Ignore le parent dans sa définition.<br />-Ne peut pas être un sous-menu d’un groupe, pas même à l’aide de Commandplacement ayant.<br />-Peut toujours être affiché en cliquant sur **barres d’outils** dans le menu **affichage** .<br />-Peut être affiché à l’aide d’un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Ne nécessite pas de code pour le créer. Pour obtenir un exemple de création d’une barre d’outils, consultez [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fournit une barre d’outils attachée à une fenêtre outil spécifique, de la même façon qu’une barre d’outils est attachée à l’environnement de développement.<br /><br /> -Ignore le parent dans sa définition.<br />-Ne peut pas être un sous-menu d’un groupe, pas même à l’aide de Commandplacement ayant.<br />-S’affiche uniquement lorsque la fenêtre outil qui héberge la barre d’outils s’affiche et que le VSPackage ajoute explicitement la barre d’outils à la fenêtre outil. Cette opération est généralement effectuée lors de la création de la fenêtre outil en obtenant la propriété de l’hôte de la barre d’outils (telle qu’elle est représentée par l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interface) à partir du frame de la fenêtre outil, puis en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> méthode.|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|Optionnel. Élément parent de l’élément de menu.|
|CommandFlag|Obligatoire. Consultez [élément indicateur de commande](../extensibility/command-flag-element.md). Les valeurs CommandFlag valides pour un menu sont les suivantes :<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** : cet indicateur n’affecte pas l’affichage des barres d’outils.<br />-   **DontCache**<br />-   **DynamicVisibility** : cet indicateur n’affecte pas l’affichage des barres d’outils.<br />-   **IconAndText**<br />-   **Nocustom**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **Textchanges au**<br />-   **TextIsAnchorCommand**|
|Chaînes|Obligatoire. Consultez l' [élément Strings](../extensibility/strings-element.md). L' `ButtonText` élément enfant doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage implémente.|

## <a name="example"></a>Exemple

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
