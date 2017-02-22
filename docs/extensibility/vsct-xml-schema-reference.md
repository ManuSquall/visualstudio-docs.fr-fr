---
title: "R&#233;f&#233;rence de sch&#233;ma XML de VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fichiers de Visual Studio commande table configuration (VSCT), de schéma XML"
  - "Éléments de schéma XML de VSCT"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# R&#233;f&#233;rence de sch&#233;ma XML de VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fournit un tableau d'éléments de schéma de commande Table compilateur, avec enfant autorisé éléments et attributs pour chacun.  
  
 Un fichier de configuration \(.vsct\) de table de commande basé sur XML définit les éléments de commande qui fournit un VSPackage à l'environnement de développement intégré \(IDE\). Ces éléments incluent les éléments de menu, des menus, des barres d'outils et des zones de liste déroulante.  
  
> [!NOTE]
>  Le compilateur VSCT peut exécuter un préprocesseur sur le fichier .vsct. Car il s'agit généralement inclut le préprocesseur, que vous pouvez définir C\+\+ et les macros qui ont la même syntaxe qui est utilisée dans les fichiers de C\+\+. Des exemples sont fournis dans le .vsct de fichiers qui le **Nouveau projet** Assistant créer un projet VSPackage.  
  
## Éléments facultatifs  
 Certains éléments VSCT sont facultatifs. Si un `Parent` argument n'est pas spécifié, Group\_Undefined:0 sera être implicite. Si un `Icon` argument n'est pas spécifié, guidOfficeIcon:msotcidNoIcon sera être implicite. Lorsqu'une touche de raccourci est définie, l'émulation, qui est généralement inutilisée, est facultative.  
  
 Éléments de bitmap peuvent être incorporés au moment de la compilation en spécifiant l'emplacement de la bande bitmap dans le `href` argument. La bande bitmap est copiée lors de la fusion et non extraites à partir des ressources de la DLL. Lorsqu'un `href` argument est fourni, le `usedList` argument est facultatif, et tous les emplacements dans la bande bitmap sont considérées comme utilisé.  
  
 Toutes les valeurs GUID et l'ID doivent être définis à l'aide de noms symboliques. Ces noms peuvent être définis dans les fichiers d'en\-tête ou dans les sections VSCT \< symboles \>. Les noms symboliques doivent être locales, inclus dans les éléments \< Include \> ou référencés par les éléments \< Extern \>. Un nom symbolique est importé à partir d'un fichier d'en\-tête spécifié dans un élément \< Extern \> s'il suit le modèle simple de \#define valeur du symbole. La valeur peut être un autre symbole tant que ce symbole a été défini précédemment. Définitions de GUID doivent suivre le format OLE ou du C\+\+. Valeurs d'ID peuvent être des chiffres décimaux ou hexadécimaux qui est précédés de 0 x, comme indiqué dans les lignes suivantes :  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0x62, 0xc8}}  
  
 Commentaires XML peuvent être utilisés, mais les outils d'interface graphique utilisateur graphique aller\-retour peuvent ignorer les. Le contenu des éléments de \< Annotation \> est assuré d'être conservée, quelle que soit le format.  
  
## Hiérarchie de schéma  
 Un fichier .vsct possède les éléments principaux suivants.  
  
 [Élément de CommandTable](../extensibility/commandtable-element.md)  
  
 [Élément de extern](../extensibility/extern-element.md)  
  
 [Élément Include](../extensibility/include-element.md)  
  
 [Définir l'élément](../extensibility/define-element.md)  
  
 [Élément Commands](../extensibility/commands-element.md)  
  
 [Élément de CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Élément de VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Élément de thèmes](../extensibility/keybindings-element.md)  
  
 [Élément de UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Parent, élément](../extensibility/parent-element.md)  
  
 [Icon, élément](../extensibility/icon-element.md)  
  
 [Élément de chaînes](../extensibility/strings-element.md)  
  
 [Élément indicateur de commande](../extensibility/command-flag-element.md)  
  
 [Élément de symboles](../extensibility/symbols-element.md)  
  
 [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans les packages VS](../extensibility/internals/command-routing-in-vspackages.md)