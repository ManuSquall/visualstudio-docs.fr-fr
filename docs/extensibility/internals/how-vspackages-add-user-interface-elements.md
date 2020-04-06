---
title: Comment VSPackages ajouter des éléments d’interface utilisateur (fr) Microsoft Docs
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
ms.openlocfilehash: 3b7d37bfe81c77536871248592d4a2e0734d1c62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707758"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Comment VSPackages ajoute des éléments d’interface utilisateur
Un VSPackage peut ajouter des éléments d’interface utilisateur (interface utilisateur), par exemple, des menus, des barres d’outils et des fenêtres d’outils, à Visual Studio au moyen du fichier *.vsct.*

 Vous pouvez trouver des lignes directrices de conception pour les éléments d’interface utilisateur à [Visual Studio directives d’expérience utilisateur](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>L’architecture de la table de commande Visual Studio
 Comme nous l’avons mentionné, l’architecture de la table de commandement soutient les principes architecturaux qui précèdent. Les principes derrière les abstractions, les structures de données et les outils de l’architecture de la table de commande sont les suivants :

- Il existe trois types d’articles de base : les menus, les commandes et les groupes. Les menus peuvent être exposés dans l’interface utilisateur sous forme de menus, de sous-menus, de barres d’outils ou de fenêtres d’outils. Les commandes sont des procédures que l’utilisateur peut exécuter dans l’IDE, et elles peuvent être exposées sous forme d’éléments de menu, de boutons, de boîtes de liste ou d’autres contrôles. Les groupes sont des conteneurs pour les menus et les commandes.

- Chaque élément est spécifié par une définition qui décrit l’élément, sa priorité par rapport à d’autres éléments, et les drapeaux qui modifient son comportement.

- Chaque élément a un placement qui décrit le parent de l’article. Un article peut avoir plusieurs parents, de sorte qu’il peut apparaître à plusieurs endroits dans l’interface utilisateur.

     Chaque commande doit avoir un groupe comme parent, même si c’est le seul enfant de ce groupe. Chaque menu standard doit également avoir un groupe de parents. Les barres d’outils et les fenêtres d’outils agissent comme leurs propres parents. Un groupe peut avoir comme parent la barre principale de menu Visual Studio, ou n’importe quel menu, barre d’outils, ou fenêtre d’outil.

### <a name="how-items-are-defined"></a>Comment les éléments sont définis
 Un fichier *.vsct* est formaté dans XML. Il définit les éléments d’interface utilisateur pour un paquet et détermine où ces éléments apparaissent dans l’IIDE. Chaque menu, groupe ou commande dans le paquet est d’abord attribué un GUID et une pièce d’identité dans la `Symbols` section. Tout au long du reste du fichier *.vsct,* chaque menu, commande et groupe est identifié par sa combinaison GUID et ID. L’exemple suivant `Symbols` montre une section typique générée par le modèle de paquet Visual Studio lorsqu’une **commande de menu** est sélectionnée dans le modèle.

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

 L’élément de haut `Symbols` niveau de la section est l’élément [GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`éléments de la carte des noms de guiDs qui sont utilisés par l’IDE pour identifier les paquets et leurs composants.

> [!NOTE]
> Les GUID sont générés automatiquement par le modèle de paquet Visual Studio. Vous pouvez également créer un GUID unique en cliquant sur **Create GUID** sur le menu **Tools.**

 Le `GuidSymbol` premier `guid<PackageName>Pkg`élément, est le GUID du paquet lui-même. Il s’agit du GUID qui est utilisé par Visual Studio pour charger le paquet. En règle générale, il n’a pas d’éléments pour enfants.

 Par convention, les menus et les `GuidSymbol` commandes `guid<PackageName>CmdSet`sont regroupés sous un `GuidSymbol` deuxième `guidImages`élément, et les bitmaps sont sous un troisième élément, . Vous n’avez pas à suivre cette convention, mais chaque menu, groupe, `GuidSymbol` commande et bitmap doit être un enfant d’un élément.

 Dans le `GuidSymbol` deuxième élément, qui représente l’ensemble de commande de paquet, sont plusieurs `IDSymbol` éléments. Chaque [élément IDSymbol](../../extensibility/idsymbol-element.md) cartographie un nom à valeur numérique, et peut représenter un menu, un groupe ou une commande qui fait partie de l’ensemble de commande. Les `IDSymbol` éléments du `GuidSymbol` troisième élément représentent des bitmaps qui peuvent être utilisés comme icônes pour les commandes. Étant donné que les paires GUID/ID doivent être `GuidSymbol` uniques dans une application, aucun enfant du même élément ne peut avoir la même valeur.

### <a name="menus-groups-and-commands"></a>Menus, groupes et commandes
 Lorsqu’un menu, un groupe ou une commande a un GUID et une pièce d’identité, il peut être ajouté à l’IDE. Chaque élément d’interface utilisateur doit avoir les choses suivantes :

- Un `guid` attribut qui correspond `GuidSymbol` au nom de l’élément sous lequel l’élément d’interface utilisateur est défini.

- Un `id` attribut qui correspond au `IDSymbol` nom de l’élément associé.

     Ensemble, `guid` les `id` attributs et les attributs composent la *signature* de l’élément d’interface utilisateur.

- Un `priority` attribut qui détermine le placement de l’élément d’assurance-chômage dans son menu ou groupe parent.

- Un [élément](../../extensibility/parent-element.md) Parent `guid` qui a et `id` attribue qui spécifie la signature du menu ou du groupe parent.

#### <a name="menus"></a>Menus
 Chaque menu est défini comme `Menus` un élément de [menu](../../extensibility/menu-element.md) dans la section. Les menus `guid` `id`doivent `priority` avoir, et `Parent` les attributs, et un élément, et aussi les attributs supplémentaires suivants et les enfants:

- Un `type` attribut qui précise si le menu doit apparaître dans l’IDE comme une sorte de menu ou comme une barre d’outils.

- Un [élément cordes](../../extensibility/strings-element.md) qui contient un élément [ButtonText](../../extensibility/buttontext-element.md), qui spécifie le titre du menu dans l’IDE, et un élément [CommandName](../../extensibility/commandname-element.md), qui spécifie le nom qui est utilisé dans la fenêtre **de commande** pour accéder au menu.

- Drapeaux optionnels. Un [élément CommandFlag](../../extensibility/command-flag-element.md) peut apparaître dans une définition de menu pour changer son apparence ou son comportement dans l’IDE.

  Chaque `Menu` élément doit avoir un groupe comme parent, à moins qu’il ne s’agit d’un élément dockable tel qu’une barre d’outils. Un menu amarré est son propre parent. Pour plus d’informations sur `type` les menus et les valeurs de l’attribut, consultez la documentation de [l’élément Menu.](../../extensibility/menu-element.md)

  L’exemple suivant montre un menu qui apparaît sur le menu Visual Studio bar, à côté du menu **Tools.**

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
 Un groupe est un élément `Groups` qui est défini dans la section du fichier *.vsct.* Les groupes ne sont que des conteneurs. Ils n’apparaissent pas dans l’IDE sauf comme ligne de démarcation sur un menu. Par conséquent, un [élément du Groupe](../../extensibility/group-element.md) n’est défini que par sa signature, sa priorité et son parent.

 Un groupe peut avoir un menu, un autre groupe, ou lui-même en tant que parent. Cependant, le parent est généralement un menu ou une barre d’outils. Le menu dans l’exemple précédent `IDG_VS_MM_TOOLSADDINS` est un enfant du groupe, et ce groupe est un enfant de la barre de menu Visual Studio. Le groupe dans l’exemple suivant est un enfant du menu dans l’exemple précédent.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Parce qu’il fait partie d’un menu, ce groupe contient généralement des commandes. Cependant, il pourrait également contenir d’autres menus. C’est ainsi que les sous-hommes sont définis, comme le montre l’exemple suivant.

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
 Une commande fournie à l’IDE est définie comme un [élément Bouton](../../extensibility/button-element.md) ou un [élément Combo](../../extensibility/combo-element.md). Pour apparaître sur un menu ou une barre d’outils, la commande doit avoir un groupe comme parent.

##### <a name="buttons"></a>Boutons
 Les boutons sont `Buttons` définis dans la section. Tout élément de menu, bouton ou autre élément qu’un utilisateur clique pour exécuter une seule commande est considéré comme un bouton. Certains types de boutons peuvent également inclure la fonctionnalité de liste. Les boutons ont les mêmes attributs requis et facultatifs que les menus ont, et peuvent également avoir un [élément Icon](../../extensibility/icon-element.md) qui spécifie le GUID et l’ID de la bitmap qui représente le bouton dans l’IDE. Pour plus d’informations sur les boutons et leurs attributs, consultez la documentation de [l’élément Boutons.](../../extensibility/buttons-element.md)

 Le bouton dans l’exemple suivant est un enfant du groupe dans l’exemple précédent, et apparaîtrait dans l’IDE comme un élément de menu sur le menu parent de ce groupe.

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
 Les combos sont `Combos` définis dans la section. Chaque `Combo` élément représente une case de liste d’abandon dans l’IDE. La boîte de liste peut ou non être aptisée `type` par les utilisateurs, selon la valeur de l’attribut du combo. Combos ont les mêmes éléments et le comportement que les boutons ont, et peut également avoir les attributs supplémentaires suivants:

- Un `defaultWidth` attribut qui spécifie la largeur des pixels.

- Un `idCommandList` attribut qui spécifie une liste qui contient les éléments qui sont affichés dans la boîte de liste. La liste de commande doit `GuidSymbol` être déclarée dans le même nœud qui contient le combo.

  L’exemple suivant définit un élément combo.

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
 Les commandes qui seront affichées avec `Icon` une icône doivent inclure un élément qui se réfère à une bitmap en utilisant son GUID et ID. Chaque bitmap est défini comme un `Bitmaps` [élément Bitmap](../../extensibility/bitmap-element.md) dans la section. Les seuls attributs `Bitmap` requis `guid` pour `href`une définition sont et, qui indique le fichier source. Si le fichier source est une bande de ressources, un attribut **utiliséList** est également nécessaire, pour énumérer les images disponibles dans la bande. Pour plus d’informations, consultez la documentation sur les [éléments Bitmap.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Parentales
 Les règles suivantes régissent la façon dont un article peut appeler un autre élément comme parent.

|Élément|Défini dans cette section de la Table de Commandement|Peut être contenu (en tant que `CommandPlacements` parent, ou par placement dans la section, ou les deux)|Peut contenir (appelé parent)|
|-------------| - | - | - |
|Groupe|[Éléments élément](../../extensibility/groups-element.md), l’IDE, autres VSPackages|Un menu, un groupe, l’article lui-même|Menus, groupes et commandes|
|Menu|[Menus élément](../../extensibility/menus-element.md), l’IDE, autres VSPackages|1 à *n* groupes|0 à *n* groupes|
|Barre d'outils|[Menus élément](../../extensibility/menus-element.md), l’IDE, autres VSPackages|L’article lui-même|0 à *n* groupes|
|Élément de menu|[Élément boutons](../../extensibility/buttons-element.md), l’IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même|-0 à *n* groupes|
|Bouton|[Élément boutons](../../extensibility/buttons-element.md), l’IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même||
|Combiné|[Combos élément](../../extensibility/combos-element.md), l’IDE, autres VSPackages|1 à *n* groupes, l’élément lui-même||

### <a name="menu-command-and-group-placement"></a>Menu, commande et placement de groupe
 Un menu, un groupe ou une commande peut apparaître à plus d’un endroit dans l’IDE. Pour qu’un élément apparaisse à plusieurs `CommandPlacements` endroits, il doit être ajouté à la section sous forme d’élément [CommandPlacement](../../extensibility/commandplacement-element.md). N’importe quel menu, groupe ou commande peut être ajouté comme placement de commande. Toutefois, les barres d’outils ne peuvent pas être positionnées de cette manière parce qu’elles ne peuvent pas apparaître dans plusieurs endroits sensibles au contexte.

 Les placements `guid` `id`de `priority` commande ont, , et attributs. Le GUID et l’ID doivent correspondre à ceux de l’élément qui est positionné. L’attribut `priority` régit le placement de l’élément par rapport à d’autres éléments. Lorsque l’IDE fusionne deux éléments ou plus qui ont la même priorité, leurs placements ne sont pas définis parce que l’IDE ne garantit pas que les ressources de paquet sont lues dans le même ordre chaque fois que le paquet est construit.

 Si un menu ou un groupe apparaît à plusieurs endroits, tous les enfants de ce menu ou de ce groupe apparaîtront dans chaque cas.

## <a name="command-visibility-and-context"></a>Visibilité et contexte de commande
 Lorsque plusieurs VSPackages sont installés, une profusion de menus, d’éléments de menu et de barres d’outils peut encombrer l’IDE. Pour éviter ce problème, vous pouvez contrôler la visibilité des éléments individuels de l’interface utilisateur en utilisant des contraintes de *visibilité* et des drapeaux de commande.

### <a name="visibility-constraints"></a>Contraintes de visibilité
 Une contrainte de visibilité est définie comme `VisibilityConstraints` [élément VisibilityItem](../../extensibility/visibilityitem-element.md) dans la section. Une contrainte de visibilité définit des contextes spécifiques d’interface utilisateur dans lesquels l’élément cible est visible. Un menu ou une commande inclus dans cette section n’est visible que lorsque l’un des contextes définis est actif. Si un menu ou une commande n’est pas référencé dans cette section, il est toujours visible par défaut. Cet article ne s’applique pas aux groupes.

 `VisibilityItem`doivent avoir trois attributs, comme `guid` `id` suit : l’élément `context`d’interface utilisateur cible et. L’attribut `context` spécifie quand l’élément cible sera visible, et prend n’importe quel contexte d’interface utilisateur valide comme valeur. Les constantes de contexte d’interface <xref:Microsoft.VisualStudio.VSConstants> utilisateur pour Visual Studio sont membres de la classe. Chaque `VisibilityItem` élément ne peut prendre qu’une seule valeur contextuelle. Pour appliquer un deuxième contexte, créez un deuxième `VisibilityItem` élément qui indique le même élément, comme le montre l’exemple suivant.

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

### <a name="command-flags"></a>Drapeaux de commandement
 Les drapeaux de commande suivants peuvent affecter la visibilité des menus et des commandes à laquelle ils s’appliquent.

 `AlwaysCreate`Le menu est créé même s’il n’a pas de groupes ou de boutons.

 Valable pour :`Menu`

 `CommandWellOnly`Appliquez ce drapeau si la commande n’apparaît pas sur le menu de haut niveau et que vous souhaitez la rendre disponible pour une personnalisation supplémentaire de la coquille, par exemple, la liant à une clé. Une fois le VSPackage installé, un utilisateur peut personnaliser ces commandes en ouvrant la boîte de dialogue **Options,** puis en éditant le placement de commande dans la catégorie **Environnement clavier.** N’affecte pas le placement sur les menus raccourcis, les barres d’outils, les contrôleurs de menu ou les sous-hommes.

 Valable pour: `Button`,`Combo`

 `DefaultDisabled`Par défaut, la commande est désactivée si le VSPackage qui implémente la commande n’est pas chargé ou si la méthode QueryStatus n’a pas été appelée.

 Valable pour: `Button`,`Combo`

 `DefaultInvisible`Par défaut, la commande est invisible si le VSPackage qui implémente la commande n’est pas chargé ou si la méthode QueryStatus n’a pas été appelée.

 Doit être combiné `DynamicVisibility` avec le drapeau.

 Valable `Button`pour: `Combo`, ,`Menu`

 `DynamicVisibility`La visibilité de la commande peut `QueryStatus` être modifiée en utilisant la `VisibilityConstraints` méthode ou un contexte GUID qui est inclus dans la section.

 S’applique aux commandes qui apparaissent sur les menus, et non sur les barres d’outils. Les éléments de barre d’outils de haut `OLECMDF_INVISIBLE` niveau peuvent être `QueryStatus` désactivés, mais pas cachés, lorsque le drapeau est retourné de la méthode.

 Sur un menu, ce drapeau indique également qu’il doit être automatiquement caché lorsque ses membres sont cachés. Ce drapeau est généralement attribué à submenus parce que les menus de haut niveau ont déjà ce comportement.

 Doit être combiné `DefaultInvisible` avec le drapeau.

 Valable `Button`pour: `Combo`, ,`Menu`

 `NoShowOnMenuController`Si une commande qui a ce drapeau est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.

 Valable pour :`Button`

 Pour plus d’informations sur les drapeaux de commandement, consultez la documentation sur [l’élément CommandFlag.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Conditions générales
 Votre commande doit passer la série de tests suivante avant qu’elle puisse être affichée et activée :

- La commande est positionnée correctement.

- Le `DefaultInvisible` drapeau n’est pas fixé.

- Le menu parent ou la barre d’outils est visible.

- La commande n’est pas invisible en raison d’une entrée de contexte dans la section [de l’élément VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- Code VSPackage qui <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémente l’interface affiche et permet votre commande. Aucun code d’interface ne l’a intercepté et n’a agi dessus.

- Lorsqu’un utilisateur clique sur votre commande, elle devient soumise à la procédure décrite dans [l’algorithme Routing](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Appelez des commandes prédéfinises
 [L’élément UsedCommands](../../extensibility/usedcommands-element.md) permet aux VSPackages d’accéder aux commandes fournies par d’autres VSPackages ou par l’IDE. Pour ce faire, créez un [élément UsedCommand](../../extensibility/usedcommand-element.md) qui a le GUID et l’ID de la commande à utiliser. Cela garantit que la commande sera chargée par Visual Studio, même si elle ne fait pas partie de la configuration actuelle Visual Studio. Pour plus d’informations, voir [UsedCommand element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Aspect d’élément d’interface
 Les considérations relatives à la sélection et au positionnement des éléments de commande sont les suivantes :

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]offre de nombreux éléments d’interface utilisateur qui apparaissent différemment selon le placement.

- Un élément d’interface utilisateur `DefaultInvisible` défini par l’utilisation du drapeau ne sera pas affiché dans <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> l’IDE à moins qu’il `VisibilityConstraints` ne soit affiché par sa mise en œuvre VSPackage de la méthode, ou associé à un contexte particulier d’interface utilisateur dans la section.

- Même une commande bien positionnée peut ne pas être affichée. C’est parce que l’IDE cache ou affiche automatiquement certaines commandes, en fonction des interfaces que le VSPackage a (ou n’a pas) mis en œuvre. Par exemple, la mise en œuvre de certaines interfaces de construction par VSPackage fait que les éléments de menu liés à la construction sont automatiquement affichés.

- L’application du `CommandWellOnly` drapeau dans la définition de l’élément d’interface utilisateur signifie que la commande ne peut être ajoutée que par personnalisation.

- Les commandes ne peuvent être disponibles que dans certains contextes d’interface utilisateur, par exemple, uniquement lorsqu’une boîte de dialogue est affichée lorsque l’IDE est en vue de conception.

- Pour que certains éléments d’interface utilisateur soient affichés dans l’IDE, vous devez implémenter une ou plusieurs interfaces ou écrire du code.

## <a name="see-also"></a>Voir aussi
- [Étendre les menus et les commandes](../../extensibility/extending-menus-and-commands.md)
