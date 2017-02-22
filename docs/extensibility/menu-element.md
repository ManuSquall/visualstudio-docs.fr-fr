---
title: "&#201;l&#233;ment de menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, Menus"
  - "Élément de menus (schéma XML de VSCT)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# &#201;l&#233;ment de menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit un élément de menu. Voici les six types de menus : contexte, un Menu, MenuController, MenuControllerLatched, barre d'outils et ToolWindowToolbar.  
  
## Syntaxe  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. GUID de l'identificateur de commande\/ID GUID.|  
|ID|Obligatoire. ID de l'identificateur de commande\/ID GUID.|  
|priority|Facultatif. Une valeur numérique qui spécifie la position relative d'un menu dans un groupe de menus.|  
|ToolbarPriorityInBand|Facultatif. Une valeur numérique qui spécifie la position relative d'une barre d'outils dans une bande lorsque la fenêtre est ancrée.|  
|type|Facultatif. Valeur énumérée qui spécifie le type d'élément.<br /><br /> Sinon, le type par défaut est Menu.<br /><br /> Contexte<br /> Un menu contextuel qui s'affiche lorsqu'un utilisateur clique sur une fenêtre. Un menu contextuel présente les caractéristiques suivantes :<br /><br /> -   N'utilise pas les champs Parent et priorité lorsque le menu doit être affichée sous forme de menu contextuel.<br />-   Peut être utilisé en tant que sous\-menu et également comme un menu contextuel. Dans ce cas, les champs ID de groupe et de priorité sont respectées.<br />-   N'est pas toujours disponible.<br /><br /> Un menu contextuel s'affiche uniquement lorsque les conditions suivantes sont remplies :<br /><br /> -   La fenêtre qui héberge ce dernier s'affiche.<br />-   Un gestionnaire de souris dans le VSPackage détecte un clic droit sur la fenêtre, puis appelle une méthode qui gère la commande.<br />-   Le menu contextuel s'affiche en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> \(méthode\) \(recommandé\) ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> \(méthode\).<br /><br /> Menu<br /> Fournit une liste déroulante. Un menu déroulant présente les caractéristiques suivantes :<br /><br /> -   Respecte le Parent dans sa définition.<br />-   Doit avoir un groupe Parent, ou un CommandPlacement à un groupe.<br />-   Peut être un sous\-menu dans n'importe quel autre menu.<br />-   S'affiche automatiquement chaque fois que son menu parent est affiché.<br />-   Ne nécessite pas l'implémentation de n'importe quel code VSPackage pour rendre l'afficher.<br /><br /> MenuController<br /> Fournit un menu déroulant du bouton partagé, qui est généralement utilisé dans les barres d'outils. Un menu MenuController présente les caractéristiques suivantes :<br /><br /> -   Doit être contenu dans un autre menu Parent ou CommandPlacement.<br />-   Respecte le Parent dans sa définition.<br />-   Peut avoir n'importe quel menu parent.<br />-   Est automatiquement mis à disposition lorsque son menu parent est affiché.<br />-   Ne nécessite pas de prise en charge par programmation pour rendre le menu qui s'affiche.<br /><br /> Une commande dans le menu du bouton partagé est affichée sur le bouton de menu. La commande affiche a l'une des caractéristiques suivantes :<br /><br /> -   Il est la dernière commande qui a été utilisée si la commande est toujours affichée et activée.<br />-   Il est la première commande affichée.<br /><br /> MenuControllerLatched<br /> Fournit un menu déroulant de bouton partagé pour lequel une commande peut être spécifiée comme étant la sélection par défaut en sélectionnant la commande comme verrouillée.<br /><br /> Une commande verrouillée est une commande qui est marquée dans le menu sélectionné, généralement en affichant une coche. Une commande peut être marquée comme verrouillée si elle a la OLECMDF\_LATCHED l'indicateur est défini sur ce dernier dans une implémentation de la `QueryStatus` méthode de le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Un menu MenuControllerLatched présente les caractéristiques suivantes :<br /><br /> -   Doit être contenu dans un autre menu via un CommandPlacement ou un groupe Parent.<br />-   Respecte le Parent dans sa définition.<br />-   Peut avoir n'importe quel menu parent.<br />-   Est accessible lorsque son menu parent est affiché.<br />-   Ne nécessite pas de prise en charge par programmation pour rendre le menu qui s'affiche.<br /><br /> Une commande dans le menu du bouton partagé est affichée sur le bouton de menu. La commande affiche a l'une des caractéristiques suivantes :<br /><br /> -   Il est la première commande affichée est verrouillée.<br />-   Il est la première commande affichée.<br /><br /> ToolBar<br /> Fournit une barre d'outils. Une barre d'outils présente les caractéristiques suivantes :<br /><br /> -   Ignore le Parent dans sa définition.<br />-   Impossible d'établir un sous\-menu d'un groupe, pas même à l'aide de CommandPlacement.<br />-   Peut toujours être affichée en cliquant sur **barres d'outils** sur la **affichage** menu.<br />-   Peut être affichée en utilisant un [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis).<br />-   Ne nécessite pas de code pour le créer. Pour obtenir un exemple expliquant comment créer une barre d'outils, consultez [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fournit une barre d'outils qui est attaché à une fenêtre outil spécifique, comme une barre d'outils est associé à l'environnement de développement.<br /><br /> -   Ignore le Parent dans sa définition.<br />-   Impossible d'établir un sous\-menu d'un groupe, pas même à l'aide de CommandPlacement.<br />-   S'affiche uniquement lorsque la fenêtre outil qui héberge la barre d'outils s'affiche et le VSPackage ajoute explicitement la barre d'outils à la fenêtre outil. Cela est généralement effectué lors de la fenêtre outil est créée en obtenant la propriété barre d'outils de l'hôte \(tel que représenté par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interface\) dans le frame de fenêtre outil et en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> \(méthode\).|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Facultatif. L'élément parent de l'élément de menu.|  
|CommandFlag|Obligatoire. Consultez [Élément indicateur de commande](../extensibility/command-flag-element.md). Les valeurs CommandFlag valides pour un Menu sont comme suit :<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-cet indicateur n'affecte pas l'affichage des barres d'outils.<br />-   **DontCache**<br />-   **DynamicVisibility** \-cet indicateur n'affecte pas l'affichage des barres d'outils.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TexteModifie**<br />-   **TextIsAnchorCommand**|  
|Chaînes|Obligatoire. Consultez [Élément de chaînes](../extensibility/strings-element.md). L'enfant `ButtonText` élément doit être défini.|  
|Annotation|Commentaire facultatif.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
  
## Exemple  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)