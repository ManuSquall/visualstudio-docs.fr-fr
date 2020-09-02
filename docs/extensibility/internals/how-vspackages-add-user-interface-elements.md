---
title: Comment les VSPackages ajoutent des éléments d’interface utilisateur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649597"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Comment les VSPackages ajoutent des éléments d’interface utilisateur
Un VSPackage peut ajouter des éléments d’interface utilisateur, tels que des menus, des barres d’outils et des fenêtres outil, à Visual Studio au moyen du fichier *. vsct* .

Vous trouverez des instructions de conception pour les éléments d’interface utilisateur dans [les instructions d’expérience utilisateur de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Architecture des tables de commandes Visual Studio
Comme indiqué précédemment, l’architecture de table de commande prend en charge les principes architecturaux précédents. Les principes qui sous-tendent les abstractions, les structures de données et les outils de l’architecture de table de commande sont les suivants :

- Il existe trois types d’éléments de base : les menus, les commandes et les groupes. Les menus peuvent être affichés dans l’interface utilisateur en tant que menus, sous-menus, barres d’outils ou fenêtres outil. Les commandes sont des procédures que l’utilisateur peut exécuter dans l’IDE, et elles peuvent être exposées en tant qu’éléments de menu, boutons, zones de liste ou autres contrôles. Les groupes sont des conteneurs pour les menus et les commandes.

- Chaque élément est spécifié par une définition qui décrit l’élément, sa priorité par rapport à d’autres éléments et les indicateurs qui modifient son comportement.

- Chaque élément a un emplacement qui décrit le parent de l’élément. Un élément peut avoir plusieurs parents, afin qu’il puisse apparaître à plusieurs emplacements dans l’interface utilisateur.

Chaque commande doit avoir un groupe comme parent, même s’il s’agit du seul enfant dans ce groupe. Chaque menu standard doit également avoir un groupe parent. Les barres d’outils et les fenêtres outil jouent le rôle de parents. Un groupe peut avoir comme parent la barre de menus principale de Visual Studio, ou n’importe quel menu, barre d’outils ou fenêtre outil.

### <a name="how-items-are-defined"></a>Définition des éléments
Un fichier *. vsct* est mis en forme au format XML. Il définit les éléments d’interface utilisateur d’un package et détermine l’emplacement d’affichage de ces éléments dans l’IDE. Chaque menu, groupe ou commande du package reçoit d’abord un GUID et un ID dans la `Symbols` section. Dans le reste du fichier *. vsct* , chaque menu, commande et groupe est identifié par sa combinaison GUID et ID. L’exemple suivant montre une `Symbols` section typique telle qu’elle est générée par le modèle de package Visual Studio lorsqu’une **commande de menu** est sélectionnée dans le modèle.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

L’élément de niveau supérieur de la `Symbols` section est l' [élément GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` les éléments mappent les noms aux GUID utilisés par l’IDE pour identifier les packages et leurs composants.

> [!NOTE]
> Les GUID sont générés automatiquement par le modèle de package Visual Studio. Vous pouvez également créer un GUID unique en cliquant sur **créer un GUID** dans le menu **Outils** .

Le premier `GuidSymbol` élément, `guid<PackageName>Pkg` , est le GUID du package lui-même. Il s’agit du GUID utilisé par Visual Studio pour charger le package. En règle générale, il n’a pas d’éléments enfants.

Par Convention, les menus et les commandes sont regroupés sous un deuxième `GuidSymbol` élément, `guid<PackageName>CmdSet` , et les bitmaps sont sous un troisième `GuidSymbol` élément, `guidImages` . Vous n’êtes pas obligé de suivre cette Convention, mais chaque menu, groupe, commande et bitmap doit être un enfant d’un `GuidSymbol` élément.

Dans le deuxième `GuidSymbol` élément, qui représente le jeu de commandes du package, plusieurs éléments sont disponibles `IDSymbol` . Chaque [élément IDSymbol](../../extensibility/idsymbol-element.md) mappe un nom à une valeur numérique et peut représenter un menu, un groupe ou une commande qui fait partie du jeu de commandes. Les `IDSymbol` éléments du troisième `GuidSymbol` élément représentent des bitmaps qui peuvent être utilisés comme icônes pour les commandes. Étant donné que les paires GUID/ID doivent être uniques dans une application, deux enfants du même `GuidSymbol` élément ne peuvent pas avoir la même valeur.

### <a name="menus-groups-and-commands"></a>Menus, groupes et commandes
Quand un menu, un groupe ou une commande possède un GUID et un ID, il peut être ajouté à l’IDE. Chaque élément d’interface utilisateur doit avoir les éléments suivants :

- `guid`Attribut qui correspond au nom de l' `GuidSymbol` élément sous lequel l’élément d’interface utilisateur est défini.

- `id`Attribut qui correspond au nom de l’élément associé `IDSymbol` .

Ensemble, les `guid` `id` attributs et composent la *signature* de l’élément d’interface utilisateur.

- `priority`Attribut qui détermine le positionnement de l’élément d’interface utilisateur dans son menu ou groupe parent.

- [Élément parent](../../extensibility/parent-element.md) ayant les `guid` attributs et `id` qui spécifient la signature du menu ou du groupe parent.

#### <a name="menus"></a>Menus
Chaque menu est défini en tant qu' [élément de menu](../../extensibility/menu-element.md) dans la `Menus` section. Les menus doivent avoir des `guid` `id` attributs,, et `priority` , ainsi qu’un `Parent` élément, ainsi que les attributs et enfants supplémentaires suivants :

- `type`Attribut qui spécifie si le menu doit apparaître dans l’IDE sous forme de type de menu ou de barre d’outils.

- [Élément Strings](../../extensibility/strings-element.md) qui contient un [élément ButtonText](../../extensibility/buttontext-element.md), qui spécifie le titre du menu dans l’IDE et un [élément CommandName](../../extensibility/commandname-element.md), qui spécifie le nom utilisé dans la fenêtre de **commande** pour accéder au menu.

- Indicateurs facultatifs. Un [élément CommandFlag](../../extensibility/command-flag-element.md) peut apparaître dans une définition de menu pour modifier son apparence ou son comportement dans l’IDE.

Chaque `Menu` élément doit avoir un groupe comme parent, sauf s’il s’agit d’un élément Ancrable tel qu’une barre d’outils. Un menu Ancrable est son propre parent. Pour plus d’informations sur les menus et les valeurs de l' `type` attribut, consultez la documentation de l' [élément de menu](../../extensibility/menu-element.md) .

L’exemple suivant montre un menu qui s’affiche dans la barre de menus de Visual Studio, en regard du menu **Outils** .

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Groupes
Un groupe est un élément défini dans la `Groups` section du fichier *. vsct* . Les groupes sont simplement des conteneurs. Ils n’apparaissent pas dans l’IDE, à l’exception de la ligne de séparation d’un menu. Par conséquent, un [élément de groupe](../../extensibility/group-element.md) est défini uniquement par sa signature, sa priorité et son parent.

Un groupe peut avoir un menu, un autre groupe ou lui-même en tant que parent. Toutefois, le parent est généralement un menu ou une barre d’outils. Dans l’exemple précédent, le menu est un enfant du `IDG_VS_MM_TOOLSADDINS` groupe et ce groupe est un enfant de la barre de menus de Visual Studio. Le groupe dans l’exemple suivant est un enfant du menu dans l’exemple précédent.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Étant donné qu’il fait partie d’un menu, ce groupe contient généralement des commandes. Toutefois, il peut également contenir d’autres menus. Voici comment les sous-menus sont définis, comme illustré dans l’exemple suivant.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Commandes
Une commande fournie à l’IDE est définie comme un [élément Button](../../extensibility/button-element.md) ou un [élément combo](../../extensibility/combo-element.md). Pour apparaître dans un menu ou une barre d’outils, la commande doit avoir un groupe comme parent.

##### <a name="buttons"></a>Boutons
Les boutons sont définis dans la `Buttons` section. Tout élément de menu, bouton ou autre élément sur lequel un utilisateur clique pour exécuter une commande unique est considéré comme un bouton. Certains types de boutons peuvent également inclure des fonctionnalités de liste. Les boutons ont les mêmes attributs obligatoires et facultatifs que ceux des menus, et peuvent également avoir un [élément Icon](../../extensibility/icon-element.md) qui spécifie le GUID et l’ID de la bitmap qui représente le bouton dans l’IDE. Pour plus d’informations sur les boutons et leurs attributs, consultez la documentation des [éléments Buttons](../../extensibility/buttons-element.md) .

Dans l’exemple suivant, le bouton est un enfant du groupe dans l’exemple précédent et apparaît dans l’IDE sous la forme d’un élément de menu dans le menu parent de ce groupe.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Combos
Les combos sont définis dans la `Combos` section. Chaque `Combo` élément représente une zone de liste déroulante dans l’IDE. La zone de liste peut être accessible en écriture par les utilisateurs, en fonction de la valeur de l' `type` attribut de la liste déroulante. Les combos ont les mêmes éléments et le même comportement que les boutons, et peuvent également avoir les attributs supplémentaires suivants :

- `defaultWidth`Attribut qui spécifie la largeur en pixels.

- `idCommandList`Attribut qui spécifie une liste qui contient les éléments affichés dans la zone de liste. La liste de commandes doit être déclarée dans le `GuidSymbol` nœud qui contient la liste déroulante.

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

##### <a name="bitmaps"></a>Images bitmap
Les commandes qui s’affichent avec une icône doivent inclure un `Icon` élément qui fait référence à une bitmap en utilisant son GUID et son ID. Chaque bitmap est définie en tant qu' [élément bitmap](../../extensibility/bitmap-element.md) dans la `Bitmaps` section. Les seuls attributs requis pour une `Bitmap` définition sont `guid` et `href` , qui pointe vers le fichier source. Si le fichier source est une bande de ressources, un attribut **usedList** est également requis pour répertorier les images disponibles dans la bande. Pour plus d’informations, consultez la documentation de l' [élément bitmap](../../extensibility/bitmap-element.md) .

### <a name="parenting"></a>Parentage
Les règles suivantes régissent la façon dont un élément peut appeler un autre élément comme son parent.

|Élément|Défini dans cette section de la table de commandes|Peut être contenu (en tant que parent ou en position dans la `CommandPlacements` section, ou les deux)|Peut contenir (désigné sous le terme de parent)|
|-------------| - | - | - |
|Grouper|[Groups, élément](../../extensibility/groups-element.md), IDE, autres VSPackages|Un menu, un groupe, l’élément lui-même|Menus, groupes et commandes|
|Menu|[Élément menus](../../extensibility/menus-element.md), IDE, autres VSPackages|groupes de 1 à *n*|0 à *n* groupes|
|Barre d’outils|[Élément menus](../../extensibility/menus-element.md), IDE, autres VSPackages|L’élément lui-même|0 à *n* groupes|
|Élément de menu|[Buttons, élément](../../extensibility/buttons-element.md), IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même|-0 à *n* groupes|
|Bouton|[Buttons, élément](../../extensibility/buttons-element.md), IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même||
|Combiné|[Élément combos](../../extensibility/combos-element.md), IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même||

### <a name="menu-command-and-group-placement"></a>Positionnement des menus, des commandes et des groupes
Un menu, un groupe ou une commande peut apparaître à plusieurs emplacements dans l’IDE. Pour qu’un élément apparaisse dans plusieurs emplacements, il doit être ajouté à la `CommandPlacements` section en tant qu' [élément commandplacement ayant](../../extensibility/commandplacement-element.md). Vous pouvez ajouter n’importe quel menu, groupe ou commande en tant que placement de commande. Toutefois, les barres d’outils ne peuvent pas être positionnées de cette manière, car elles ne peuvent pas apparaître dans plusieurs emplacements contextuels.

Les emplacements de commande ont des `guid` `id` attributs, et `priority` . Le GUID et l’ID doivent correspondre à ceux de l’élément positionné. L' `priority` attribut régit l’emplacement de l’élément par rapport à d’autres éléments. Lorsque l’IDE fusionne deux éléments ou plus ayant la même priorité, leurs emplacements ne sont pas définis, car l’IDE ne garantit pas que les ressources de package sont lues dans le même ordre à chaque fois que le package est généré.

Si un menu ou un groupe apparaît à plusieurs emplacements, tous les enfants de ce menu ou groupe s’affichent dans chaque instance.

## <a name="command-visibility-and-context"></a>Visibilité de la commande et contexte
Lorsque plusieurs VSPackages sont installés, une profusion des menus, des éléments de menu et des barres d’outils peut encombrer l’IDE. Pour éviter ce problème, vous pouvez contrôler la visibilité des éléments d’interface utilisateur individuels à l’aide de *contraintes de visibilité* et d’indicateurs de commande.

### <a name="visibility-constraints"></a>Contraintes de visibilité
Une contrainte de visibilité est définie en tant qu' [élément VisibilityItem](../../extensibility/visibilityitem-element.md) dans la `VisibilityConstraints` section. Une contrainte de visibilité définit des contextes d’interface utilisateur spécifiques dans lesquels l’élément cible est visible. Un menu ou une commande inclus dans cette section est visible uniquement lorsque l’un des contextes définis est actif. Si un menu ou une commande n’est pas référencé dans cette section, il est toujours visible par défaut. Cette section ne s’applique pas aux groupes.

`VisibilityItem` les éléments doivent avoir trois attributs, comme suit : `guid` et `id` de l’élément d’interface utilisateur cible, et `context` . L' `context` attribut spécifie le moment où l’élément cible sera visible et prend comme valeur un contexte d’interface utilisateur valide. Les constantes de contexte d’interface utilisateur pour Visual Studio sont des membres de la <xref:Microsoft.VisualStudio.VSConstants> classe. Chaque `VisibilityItem` élément ne peut prendre qu’une seule valeur de contexte. Pour appliquer un deuxième contexte, créez un deuxième `VisibilityItem` élément qui pointe vers le même élément, comme indiqué dans l’exemple suivant.

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

### <a name="command-flags"></a>Indicateurs de commande
Les indicateurs de commande suivants peuvent affecter la visibilité des menus et des commandes auxquels ils s’appliquent.

`AlwaysCreate` Le menu est créé même s’il n’a pas de groupes ou de boutons.

Valide pour : `Menu`

`CommandWellOnly` Appliquez cet indicateur si la commande n’apparaît pas dans le menu de niveau supérieur et si vous souhaitez la rendre disponible pour une personnalisation de l’interpréteur de commandes supplémentaire, par exemple pour la lier à une clé. Une fois le VSPackage installé, un utilisateur peut personnaliser ces commandes en ouvrant la boîte de dialogue **options** , puis en modifiant le placement de la commande sous la catégorie **environnement clavier** . N’affecte pas le positionnement dans les menus contextuels, les barres d’outils, les contrôleurs de menu ou les sous-menus.

Valide pour : `Button` , `Combo`

`DefaultDisabled` Par défaut, la commande est désactivée si le VSPackage qui implémente la commande n’est pas chargé ou si la méthode QueryStatus n’a pas été appelée.

Valide pour : `Button` , `Combo`

`DefaultInvisible` Par défaut, la commande est invisible si le VSPackage qui implémente la commande n’est pas chargé ou si la méthode QueryStatus n’a pas été appelée.

Doit être combiné avec l' `DynamicVisibility` indicateur.

Valide pour : `Button` , `Combo` , `Menu`

`DynamicVisibility` La visibilité de la commande peut être modifiée à l’aide de la `QueryStatus` méthode ou d’un GUID de contexte qui est inclus dans la `VisibilityConstraints` section.

S’applique aux commandes qui s’affichent dans les menus, pas dans les barres d’outils. Les éléments de barre d’outils de niveau supérieur peuvent être désactivés, mais ne sont pas masqués, lorsque l' `OLECMDF_INVISIBLE` indicateur est retourné à partir de la `QueryStatus` méthode.

Dans un menu, cet indicateur indique également qu’il doit être masqué automatiquement lorsque ses membres sont masqués. Cet indicateur est généralement affecté aux sous-menus, car les menus de niveau supérieur ont déjà ce comportement.

Doit être combiné avec l' `DefaultInvisible` indicateur.

Valide pour : `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Si une commande avec cet indicateur est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.

Valide pour : `Button`

Pour plus d’informations sur les indicateurs de commande, consultez la documentation de l' [élément CommandFlag](../../extensibility/command-flag-element.md) .

#### <a name="general-requirements"></a>Conditions générales
Votre commande doit passer la série de tests suivante avant de pouvoir être affichée et activée :

- La commande est positionnée correctement.

- L' `DefaultInvisible` indicateur n’est pas défini.

- Le menu parent ou la barre d’outils est visible.

- La commande n’est pas invisible en raison d’une entrée de contexte dans la section de l' [élément VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .

- Le code VSPackage qui implémente l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface affiche et active votre commande. Aucun code d’interface ne l’a interceptée et n’a agi dessus.

- Lorsqu’un utilisateur clique sur votre commande, il est soumis à la procédure décrite dans [algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Appeler des commandes prédéfinies
L' [élément UsedCommands](../../extensibility/usedcommands-element.md) permet aux VSPackages d’accéder aux commandes fournies par d’autres VSPackages ou par l’IDE. Pour ce faire, créez un [élément UsedCommand](../../extensibility/usedcommand-element.md) contenant le GUID et l’ID de la commande à utiliser. Cela permet de s’assurer que la commande sera chargée par Visual Studio, même si elle ne fait pas partie de la configuration actuelle de Visual Studio. Pour plus d’informations, consultez [élément UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Apparence de l’élément d’interface
Les éléments à prendre en compte pour la sélection et le positionnement des éléments de commande sont les suivants :

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre de nombreux éléments d’interface utilisateur qui s’affichent différemment en fonction de leur position.

- Un élément d’interface utilisateur défini à l’aide de l' `DefaultInvisible` indicateur ne sera pas affiché dans l’IDE à moins qu’il soit affiché par son implémentation VSPackage de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> méthode, ou associé à un contexte d’interface utilisateur particulier dans la `VisibilityConstraints` section.

- Même une commande correctement positionnée ne peut pas être affichée. Cela est dû au fait que l’IDE masque ou affiche automatiquement certaines commandes, en fonction des interfaces que le VSPackage a (ou n’a pas) implémentées. Par exemple, l’implémentation d’un VSPackage de certaines interfaces de génération entraîne l’affichage automatique des éléments de menu liés à la génération.

- L’application de l' `CommandWellOnly` indicateur dans la définition de l’élément d’interface utilisateur signifie que la commande ne peut être ajoutée que par la personnalisation.

- Les commandes peuvent uniquement être disponibles dans certains contextes d’interface utilisateur, par exemple, uniquement lorsqu’une boîte de dialogue est affichée lorsque l’IDE est en mode Design.

- Pour que certains éléments de l’interface utilisateur s’affichent dans l’IDE, vous devez implémenter une ou plusieurs interfaces ou écrire du code.

## <a name="see-also"></a>Voir aussi
- [Étendre des menus et des commandes](../../extensibility/extending-menus-and-commands.md)
