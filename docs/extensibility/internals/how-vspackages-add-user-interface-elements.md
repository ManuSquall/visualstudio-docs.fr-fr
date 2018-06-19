---
title: Comment les VSPackages ajouter les éléments d’Interface utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 930ab9e741b2fd5bbc0ca2954192fe5e2c4313d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136079"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Comment les VSPackages ajouter les éléments d’Interface utilisateur
Un VSPackage peut ajouter des éléments d’interface (interface utilisateur) utilisateur, par exemple, les menus, barres d’outils et fenêtres dans Visual Studio au moyen du fichier .vsct.  
  
 Vous trouverez des instructions de conception pour les éléments d’interface utilisateur à [recommandations expérience utilisateur de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>L’Architecture de Table de commandes de Visual Studio  
 Comme indiqué, l’Architecture de la Table de commande prend en charge les principes d’architecture qui précèdent. Les principes derrière les abstractions, des structures de données et des outils de l’Architecture de la Table de commande sont les suivantes :  
  
-   Il existe trois types de base d’éléments : menus, les commandes et les groupes. Les menus peuvent être exposés dans l’interface utilisateur comme les menus, sous-menus, barres d’outils ou les fenêtres Outil. Les commandes sont des procédures qui l’utilisateur peut exécuter dans l’IDE, et ils peuvent être exposés en tant qu’éléments de menu, des boutons, des zones de liste ou d’autres contrôles. Les groupes sont des conteneurs pour les menus et commandes.  
  
-   Chaque élément est spécifié par une définition qui décrit l’élément, sa priorité par rapport aux autres éléments et les indicateurs qui modifient son comportement.  
  
-   Chaque élément possède un placement qui décrit le parent de l’élément. Un élément peut avoir plusieurs parents, afin qu’elle peut apparaître dans plusieurs emplacements dans l’interface utilisateur.  
  
     Chaque commande doit avoir un groupe en tant que son parent, même si c’est le seul enfant de ce groupe. Chaque menu standard doit également disposer d’un groupe parent. Barres d’outils et fenêtres Outil agissent en tant que leurs parents. Un groupe peut avoir comme son parent de la barre de menus Visual Studio principale, ou n’importe quel menu, barre d’outils ou de fenêtre outil.  
  
### <a name="how-items-are-defined"></a>Comment les éléments sont définis  
 . Fichiers VSCT sont au format XML. Un fichier .vsct définit les éléments d’interface utilisateur pour un package et détermine où ces éléments s’affichent dans l’IDE. Chaque menu, groupe ou une commande dans le package est affecté un GUID et l’ID dans la `Symbols` section. Dans le reste de le .vsct fichier, chaque menu, commande et groupe sont identifié par sa combinaison GUID et ID. L’exemple suivant montre une manière classique `Symbols` section tel que généré par le modèle de Package Visual Studio lorsqu’un **commande de Menu** est sélectionné dans le modèle.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 L’élément de niveau supérieur de la `Symbols` section est la [GuidSymbol élément](../../extensibility/guidsymbol-element.md). `GuidSymbol` éléments de mappent des noms pour les GUID utilisés par l’IDE pour identifier les packages et leurs composants.  
  
> [!NOTE]
>  GUID sont générés automatiquement par le modèle de Package Visual Studio. Vous pouvez également créer un GUID unique en cliquant sur **Create GUID** sur la **outils** menu.  
  
 Le premier `GuidSymbol` élément, « guid [PackageName] Pkg », est le GUID du package lui-même. Il s’agit du GUID est utilisé par Visual Studio pour charger le package. En règle générale, il n’a pas des éléments enfants.  
  
 Par convention, les menus et les commandes sont regroupées sous un deuxième `GuidSymbol` élément, « guid [PackageName] CmdSet », et les images bitmap sont sous une troisième `GuidSymbol` élément, « guidImages ». Vous n’êtes pas obligé de suivent cette convention, mais chaque menu, un groupe, une commande et une bitmap doivent être un enfant d’un `GuidSymbol` élément.  
  
 Dans la seconde `GuidSymbol` l’élément, qui représente le jeu de commandes de package, sont plusieurs `IDSymbol` éléments. Chaque [IDSymbol élément](../../extensibility/idsymbol-element.md) associe un nom à une valeur numérique et peut représenter un menu, un groupe ou une commande qui fait partie du jeu de commandes. Le `IDSymbol` éléments dans la troisième `GuidSymbol` élément représentent les images bitmap qui peuvent être utilisés comme icônes pour les commandes. Étant donné que les paires GUID/ID doivent être uniques dans une application, aucune deux enfants du même `GuidSymbol` élément peut avoir la même valeur.  
  
### <a name="menus-groups-and-commands"></a>Menus, les groupes et les commandes  
 Lorsqu’un menu, groupe ou commande possède un GUID et l’ID, il peut être ajouté à l’IDE. Chaque élément d’interface utilisateur doit avoir les éléments suivants :  
  
-   A `guid` attribut qui correspond au nom de la `GuidSymbol` élément défini sous l’élément d’interface utilisateur.  
  
-   Un `id` attribut qui correspond au nom de la `IDSymbol` élément.  
  
     Ensemble, le `guid` et `id` attributs composent le *signature* de l’élément d’interface utilisateur.  
  
-   A `priority` attribut qui détermine l’emplacement de l’élément d’interface utilisateur dans son menu parent ou d’un groupe.  
  
-   A [élément Parent](../../extensibility/parent-element.md) qui a `guid` et `id` attributs qui spécifient la signature du menu parent ou du groupe.  
  
#### <a name="menus"></a>Menus  
 Chaque menu est défini comme un [élément de Menu](../../extensibility/menu-element.md) dans la `Menus` section. Menus doivent avoir `guid`, `id`, et `priority` attributs et un `Parent` élément et également les attributs supplémentaires suivants et enfants :  
  
-   A `type` attribut qui spécifie si le menu doit s’afficher dans l’IDE en tant qu’un type de menu ou une barre d’outils.  
  
-   A [chaînes élément](../../extensibility/strings-element.md) qui contient un [ButtonText élément](../../extensibility/buttontext-element.md), qui spécifie le titre du menu dans l’IDE et un [CommandName élément](../../extensibility/commandname-element.md), qui spécifie le nom est utilisé dans le **commande** fenêtre pour accéder au menu.  
  
-   Indicateurs facultatifs. A [élément indicateur de commande](../../extensibility/command-flag-element.md) peut apparaître dans une définition de menu pour modifier son apparence ou le comportement de l’IDE.  
  
 Chaque `Menu` élément doit avoir un groupe en tant que son parent, sauf s’il est un élément ancrable comme une barre d’outils. Un menu ancrable est son propre parent. Pour plus d’informations sur les menus et les valeurs pour le `type` d’attribut, consultez la [élément de Menu](../../extensibility/menu-element.md) documentation.  
  
 L’exemple suivant montre un menu qui s’affiche dans la barre de menus de Visual Studio, à côté du **outils** menu.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Groupes  
 Un groupe est un élément qui est défini dans la `Groups` section du fichier .vsct. Les groupes sont simplement des conteneurs. Ils n’apparaissent pas dans l’IDE, à l’exception comme une ligne de séparation dans un menu. Par conséquent, un [élément Group](../../extensibility/group-element.md) est défini uniquement par son parent, la priorité et la signature.  
  
 Un groupe peut avoir un menu, un autre groupe ou lui-même en tant que parent. Toutefois, le parent est en général, un menu ou une barre d’outils. Le menu de l’exemple précédent est un enfant de le `IDG_VS_MM_TOOLSADDINS` groupe et ce groupe est un enfant de la barre de menus de Visual Studio. Le groupe dans l’exemple suivant est un enfant du menu de l’exemple précédent.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Car il fait partie d’un menu, ce groupe contient généralement commandes. Toutefois, il peut également contenir d’autres menus. Voici comment les sous-menus sont définis, comme indiqué dans l’exemple suivant.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Commandes  
 Une commande qui est fournie à l’interface IDE est définie comme un [élément Button](../../extensibility/button-element.md) ou un [élément de liste déroulante](../../extensibility/combo-element.md). Pour être affichés dans un menu ou une barre d’outils, la commande doit avoir un groupe en tant que son parent.  
  
##### <a name="buttons"></a>Boutons  
 Boutons sont définis dans la `Buttons` section. N’importe quel élément de menu, bouton ou autre élément sur lequel un utilisateur clique pour exécuter une seule commande est considérée comme un bouton. Certains types de boutons peuvent également inclure des fonctionnalités de liste. Boutons ont les mêmes que celles requises et les attributs facultatifs de menus, et peut également avoir un [icône élément](../../extensibility/icon-element.md) qui spécifie le GUID et l’ID de la bitmap qui représente le bouton dans l’IDE. Pour plus d’informations sur les boutons et leurs attributs, consultez le [boutons élément](../../extensibility/buttons-element.md) documentation.  
  
 Le bouton dans l’exemple suivant est un enfant du groupe dans l’exemple précédent et s’affichent dans l’IDE en tant qu’un élément de menu dans le menu du parent de ce groupe.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combinés  
 Combinaisons sont définis dans la `Combos` section. Chaque `Combo` élément représente une zone de liste déroulante dans l’IDE. La zone de liste peut ou ne peut pas être accessible en écriture par des utilisateurs, selon la valeur de la `type` attribut de la liste déroulante. Combinaisons ont les mêmes éléments et de comportement des boutons ont et peut avoir également les attributs supplémentaires suivants :  
  
-   A `defaultWidth` attribut qui spécifie la largeur en pixels.  
  
-   Un `idCommandList` attribut qui spécifie une liste qui contient les éléments qui sont affichent dans la zone de liste. La liste de commandes doit être déclarée dans le même `GuidSymbol` nœud qui contient la liste déroulante.  
  
 L’exemple suivant définit un élément de liste déroulante.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Bitmaps  
 Les commandes qui seront affiche avec une icône doivent inclure un `Icon` élément qui fait référence à une image bitmap à l’aide de son GUID et le code. Chaque bitmap est défini comme un [Bitmap élément](../../extensibility/bitmap-element.md) dans la `Bitmaps` section. Le seul obligatoire des attributs pour un `Bitmap` définition sont `guid` et `href`, qui pointe vers le fichier source. Si le fichier source est une bande de la ressource, un **usedList** attribut est également requis pour lister les images disponibles dans la bande. Pour plus d’informations, consultez la [Bitmap élément](../../extensibility/bitmap-element.md) documentation.  
  
### <a name="parenting"></a>Apparenter  
 Les règles suivantes régissent la façon dont un élément peut appeler un autre élément de son parent.  
  
|Élément|Défini dans cette section de la Table de commande|Peut être contenu (en tant que parent, ou par position dans la `CommandPlacements` section, ou les deux)|Peut contenir (également appelé un parent)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Regrouper|[Élément groupes](../../extensibility/groups-element.md), l’IDE, les autres packages VS|Un menu, un groupe, l’élément lui-même|Menus, les groupes et les commandes|  
|Menu|[Élément de menus](../../extensibility/menus-element.md), l’IDE, les autres packages VS|1 pour *n* groupes|0 à *n* groupes|  
|ToolBar|[Élément de menus](../../extensibility/menus-element.md), l’IDE, les autres packages VS|L’élément proprement dit|0 à *n* groupes|  
|Élément de menu|[Boutons d’élément](../../extensibility/buttons-element.md), l’IDE, les autres packages VS|1 pour *n* des groupes, l’élément lui-même|-0 pour *n* groupes|  
|Bouton|[Boutons d’élément](../../extensibility/buttons-element.md), l’IDE, les autres packages VS|1 pour *n* des groupes, l’élément lui-même||  
|liste déroulante|[Élément de combinaisons](../../extensibility/combos-element.md), l’IDE, les autres packages VS|1 pour *n* des groupes, l’élément lui-même||  
  
### <a name="menu-command-and-group-placement"></a>Menu, commande et la sélection élective du groupe  
 Un menu, un groupe ou une commande peut apparaître dans plusieurs emplacements dans l’IDE. Pour l’élément doit apparaître dans plusieurs emplacements, il doit être ajouté à la `CommandPlacements` section comme un [CommandPlacement élément](../../extensibility/commandplacement-element.md). N’importe quel menu, groupe ou une commande peut être ajouté comme un emplacement de la commande. Toutefois, les barres d’outils ne peut pas être positionnés de cette manière, car ils ne peut pas apparaître dans plusieurs emplacements contextuelles.  
  
 Placements de commandes ont `guid`, `id`, et `priority` attributs. Le GUID et l’ID doivent correspondre à ceux de l’élément est positionné. Le `priority` attribut régit le positionnement de l’élément en ce qui concerne les autres éléments. Lorsque l’IDE fusionne deux ou plusieurs éléments qui ont la même priorité, leurs emplacements ne sont pas définis, car l’IDE ne garantit pas que les ressources du package sont lus dans le même ordre chaque fois que le package est généré.  
  
 Si un menu ou un groupe s’affiche dans plusieurs emplacements, tous les enfants de ce menu ou le groupe apparaît dans chaque instance.  
  
## <a name="command-visibility-and-context"></a>Visibilité de la commande et le contexte  
 Lorsque plusieurs VSPackages sont installés, une pluralité des menus, des éléments de menu et des barres d’outils peut surcharger l’IDE. Pour éviter ce problème, vous pouvez contrôler la visibilité des éléments individuels de l’interface utilisateur à l’aide de *contraintes de visibilité* et indicateurs de commande.  
  
##### <a name="visibility-constraints"></a>Contraintes de visibilité  
 Une contrainte de visibilité est définie comme un [VisibilityItem élément](../../extensibility/visibilityitem-element.md) dans la `VisibilityConstraints` section. Une contrainte de visibilité définit des contextes spécifiques de l’interface utilisateur dans laquelle l’élément cible est visible. Un menu ou une commande qui est inclus dans cette section est visible uniquement lorsqu’un des contextes définis est actif. Si un menu ou une commande n’est pas référencé dans cette section, il est toujours visible par défaut. Cette section ne s’applique pas aux groupes.  
  
 `VisibilityItem` les éléments doivent posséder des trois attributs, comme suit : le `guid` et `id` de l’élément d’interface utilisateur cible, et `context`. Le `context` attribut spécifie si l’élément cible est visible et accepte n’importe quel contexte de l’interface utilisateur valide en tant que sa valeur. Les constantes de contexte de l’interface utilisateur de Visual Studio sont des membres de la <xref:Microsoft.VisualStudio.VSConstants> classe. Chaque `VisibilityItem` élément peut prendre la valeur de contexte qu’une seule. Pour appliquer un deuxième contexte, créez une seconde `VisibilityItem` élément qui pointe vers le même élément, comme indiqué dans l’exemple suivant.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>Indicateurs de commande  
 Les indicateurs de commande suivants peuvent affecter la visibilité des menus et elles s’appliquent à des commandes.  
  
 AlwaysCreate  
 Menu est créé même si elle n’a aucun groupe ou les boutons.  
  
 Valide pour : `Menu`  
  
 CommandWellOnly  
 Appliquer cet indicateur si la commande n’apparaît pas dans le menu de niveau supérieur et que vous souhaitez rendre disponibles pour la personnalisation de l’interpréteur de commandes supplémentaires, par exemple, la liaison à une clé. Une fois le package Visual Studio est installé, un utilisateur peut personnaliser ces commandes en ouvrant le **Options** boîte de dialogue, puis en modifiant le placement de commande sous la **clavier environnement** catégorie. N’affecte pas la sélection élective sur les menus contextuels, les barres d’outils, les contrôleurs de menu ou les sous-menus.  
  
 Valide pour : `Button`, `Combo`  
  
 DefaultDisabled  
 Par défaut, la commande est désactivée si le VSPackage qui implémente la commande n’est pas chargé ou la méthode QueryStatus n’a pas été appelée.  
  
 Valide pour : `Button`, `Combo`  
  
 DefaultInvisible  
 Par défaut, la commande est invisible si le VSPackage qui implémente la commande n’est pas chargé ou la méthode QueryStatus n’a pas été appelée.  
  
 Doit être combiné avec le `DynamicVisibility` indicateur.  
  
 Valide pour : `Button`, `Combo`, `Menu`  
  
 DynamicVisibility  
 La visibilité de la commande peut être modifiée à l’aide de la méthode QueryStatus ou un GUID qui est inclus dans le `VisibilityConstraints` section.  
  
 S’applique aux commandes qui s’affichent dans les menus, pas sur les barres d’outils. Les éléments de barre d’outils de niveau supérieur peuvent être désactivées, mais ne pas masquées, lorsque l’indicateur OLECMDF_INVISIBLE est retourné à partir de la méthode QueryStatus.  
  
 Dans un menu, cet indicateur indique également qu’il doit être automatiquement masqué lorsque ses membres sont masquées. Cet indicateur est généralement attribué aux sous-menus, car les menus de niveau supérieur ont déjà ce comportement.  
  
 Doit être combiné avec le `DefaultInvisible` indicateur.  
  
 Valide pour : `Button`, `Combo`, `Menu`  
  
 NoShowOnMenuController  
 Si une commande qui possède cet indicateur est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.  
  
 Valide pour : `Button`  
  
 Pour plus d’informations sur les indicateurs de commande, consultez le [élément indicateur de commande](../../extensibility/command-flag-element.md) documentation.  
  
##### <a name="general-requirements"></a>Exigences générales  
 Votre commande doit passer à la série de tests suivante avant de pouvoir être affiché et activé :  
  
-   La commande est positionnée correctement.  
  
-   Le `DefaultInvisible` indicateur n’est pas défini.  
  
-   Le menu parent ou la barre d’outils est visible.  
  
-   La commande n’est pas invisible en raison d’une entrée de contexte dans le [VisibilityConstraints élément](../../extensibility/visibilityconstraints-element.md) section.  
  
-   Code VSPackage qui implémente le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface affiche et permet à votre commande. Aucun code d’interface interceptée et l’action.  
  
-   Lorsqu’un utilisateur clique sur votre commande, il est soumis à la procédure décrite dans [algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Appel des commandes prédéfinies  
 Le [UsedCommands élément](../../extensibility/usedcommands-element.md) VSPackages permet d’accéder aux commandes qui sont fournies par d’autres packages VS, ou par l’IDE. Pour ce faire, créez un [UsedCommand élément](../../extensibility/usedcommand-element.md) qui a le GUID et l’ID de la commande à utiliser. Cela garantit que la commande sera chargée par Visual Studio, même si elle n’est pas partie de la configuration actuelle de Visual Studio. Pour plus d’informations, consultez [UsedCommand élément](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Apparence de l’élément d’interface  
 Considérations pour la sélection et le positionnement des éléments de la commande sont les suivantes :  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre de nombreux éléments d’interface utilisateur qui s’affichent différemment en fonction de la sélection élective.  
  
-   Un élément d’interface utilisateur qui est défini à l’aide de la `DefaultInvisible` indicateur n’est pas affiché dans l’IDE, sauf si elle est soit affiché par son implémentation VSPackage de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> (méthode), ou associé à un contexte de l’interface utilisateur spécifique dans la `VisibilityConstraints` section.  
  
-   Même une commande correctement positionnée ne peut-être pas s’afficher. Étant donné que l’IDE automatiquement masque ou affiche des commandes, en fonction des interfaces qui le VSPackage a (ou pas) l’implémentation. Par exemple, l’implémentation d’un VSPackage de certains créer des interfaces causes build les éléments de menu à afficher automatiquement.  
  
-   Appliquer le `CommandWellOnly` indicateur dans la définition d’élément d’interface utilisateur signifie que la commande peut être ajoutée uniquement par la personnalisation.  
  
-   Commandes peuvent être uniquement disponibles dans certains contextes d’interface utilisateur, par exemple, uniquement quand une boîte de dialogue s’affiche lorsque l’IDE est en mode design.  
  
-   Pour spécifier que certains éléments d’interface utilisateur à afficher dans l’IDE, vous devez implémenter une ou plusieurs interfaces, ou écrire du code.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md)