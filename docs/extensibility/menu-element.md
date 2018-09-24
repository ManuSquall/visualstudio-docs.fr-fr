---
title: Élément de menu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d69a6951cdae84ba2abc06bcdfde19fffa665c03
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637508"
---
# <a name="menu-element"></a>Élément de menu
Définit un élément de menu. Voici les six types de menus : contexte, un Menu, MenuController, MenuControllerLatched, barre d’outils et ToolWindowToolbar.  
  
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
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.|  
|ID|Obligatoire. ID de l’identificateur de commande/ID GUID.|  
|priority|Facultatif. Une valeur numérique qui spécifie la position relative d’un menu dans un groupe de menus.|  
|ToolbarPriorityInBand|Facultatif. Une valeur numérique qui spécifie la position relative d’une barre d’outils dans une bande lorsque la fenêtre est ancrée.|  
|type|Facultatif. Valeur énumérée qui spécifie le type d’élément.<br /><br /> Si elle est absente, le type par défaut est de Menu.<br /><br /> Contexte<br /> Un menu contextuel qui s’affiche quand un utilisateur clique sur une fenêtre. Un menu contextuel présente les caractéristiques suivantes :<br /><br /> -N’utilise pas le **Parent** et **priorité** champs quand le menu à afficher sous forme de menu contextuel.<br />-Utilisable en tant que sous-menu et également comme un menu contextuel. Dans ce cas, les deux **ID de groupe** et **priorité** champs sont respectées.<br />-N’est pas toujours disponible.<br /><br /> Un menu contextuel s’affiche uniquement lorsque les conditions suivantes sont remplies :<br /><br /> -La fenêtre qui l’héberge est affichée.<br />-Un gestionnaire de souris dans le package Visual Studio détecte un clic droit sur la fenêtre, puis appelle une méthode qui gère la commande.<br />-Le menu contextuel s’affiche en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> (méthode) (recommandé) ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> (méthode).<br /><br /> Menu<br /> Fournit un menu déroulant. Un menu déroulant présente les caractéristiques suivantes :<br /><br /> -Respecte le Parent dans sa définition.<br />-Doit avoir un groupe Parent, ou un CommandPlacement à un groupe.<br />-Peut être un sous-menu dans n’importe quel autre type de menu.<br />-Apparaît automatiquement chaque fois que son menu parent s’affiche.<br />-Ne nécessite pas l’implémentation de n’importe quel code VSPackage pour la rendre affiché.<br /><br /> MenuController<br /> Fournit un menu déroulant du bouton partagé, qui est généralement utilisé dans les barres d’outils. Un menu MenuController présente les caractéristiques suivantes :<br /><br /> -Doit être contenu dans un autre menu Parent ou CommandPlacement.<br />-Respecte le Parent dans sa définition.<br />-Vous pouvez avoir n’importe quel type de menu en tant que son parent.<br />-Est automatiquement mis à disposition dès que son menu parent s’affiche.<br />-Ne nécessite pas de prise en charge par programmation pour rendre le menu qui s’affiche.<br /><br /> Une commande dans le menu du bouton partagé est affichée sur le bouton de menu. La commande affiche a l’une des caractéristiques suivantes :<br /><br /> -Il est la dernière commande qui a été utilisée si la commande est toujours affichée et activée.<br />-Il est la première commande affichée.<br /><br /> MenuControllerLatched<br /> Fournit un menu déroulant de bouton partagé pour lequel une commande peut être spécifiée comme la sélection par défaut en marquant la commande comme verrouillée.<br /><br /> Une commande verrouillée est une commande qui est marquée dans le menu comme étant sélectionnée, généralement en affichant une coche. Une commande peut être marquée comme verrouillée si elle a la OLECMDF_LATCHED l’indicateur est défini sur ce dernier dans une implémentation de la `QueryStatus` méthode de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Un menu MenuControllerLatched présente les caractéristiques suivantes :<br /><br /> -Doit être contenu dans un autre menu via un groupe Parent ou le CommandPlacement.<br />-Respecte le Parent dans sa définition.<br />-Vous pouvez avoir n’importe quel type de menu en tant que son parent.<br />-Est accessible à chaque fois que son menu parent s’affiche.<br />-Ne nécessite pas de prise en charge par programmation pour rendre le menu qui s’affiche.<br /><br /> Une commande dans le menu du bouton partagé est affichée sur le bouton de menu. La commande affiche a l’une des caractéristiques suivantes :<br /><br /> -Il est la première commande affichée qui est verrouillée.<br />-Il est la première commande affichée.<br /><br /> ToolBar<br /> Fournit une barre d’outils. Une barre d’outils présente les caractéristiques suivantes :<br /><br /> -Ignore le Parent dans sa définition.<br />-Impossible d’établir un sous-menu d’un groupe, pas même à l’aide de CommandPlacement.<br />-Peut toujours être affichée en cliquant sur **barres d’outils** sur le **vue** menu.<br />-Peuvent être affichées en utilisant un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Ne requiert pas de code pour le créer. Pour obtenir un exemple sur la création d’une barre d’outils, consultez [ajouter une barre d’outils](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fournit une barre d’outils qui est attaché à une fenêtre outil spécifique, comme une barre d’outils est associé à l’environnement de développement.<br /><br /> -Ignore le Parent dans sa définition.<br />-Impossible d’établir un sous-menu d’un groupe, pas même à l’aide de CommandPlacement.<br />-Est affichée uniquement lorsque la fenêtre outil qui héberge la barre d’outils est affichée et que le VSPackage ajoute explicitement la barre d’outils à la fenêtre outil. Cela est généralement le cas lors de la fenêtre outil est créée en obtenant la propriété d’hôte de barre d’outils (telle que représentée par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interface) à partir du frame de fenêtre outil et l’appeler ensuite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> (méthode).|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Facultatif. L’élément parent de l’élément de menu.|  
|CommandFlag|Obligatoire. Consultez [élément Command flag](../extensibility/command-flag-element.md). Les valeurs CommandFlag valides pour un Menu sont comme suit :<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -cet indicateur n’affecte pas l’affichage des barres d’outils.<br />-   **DontCache**<br />-   **DynamicVisibility** -cet indicateur n’affecte pas l’affichage des barres d’outils.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Chaînes|Obligatoire. Consultez [élément Strings](../extensibility/strings-element.md). L’enfant `ButtonText` élément doit être défini.|  
|Annotation|Commentaire facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
  
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
 [Fichiers de la table de commande Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)