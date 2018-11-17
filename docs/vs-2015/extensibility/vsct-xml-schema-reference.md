---
title: Référence du schéma XML VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bff3fb766c11987b84ba88b5c86ab3c8d24dbc94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755864"
---
# <a name="vsct-xml-schema-reference"></a>Informations de référence sur le schéma XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fournit un tableau d’éléments de schéma du compilateur de Table de commande, avec enfant autorisé éléments et attributs pour chacun.  
  
 Un fichier de configuration (.vsct) de table de commande basé sur XML définit les éléments de commande qui fournit un VSPackage à l’environnement de développement intégré (IDE). Ces éléments incluent les éléments de menu, des menus, des barres d’outils et des zones de liste déroulante.  
  
> [!NOTE]
>  Le compilateur VSCT peut exécuter un préprocesseur sur le fichier .vsct. Comme il s’agit en général le préprocesseur, que vous pouvez définir C++ inclut et macros qui ont la même syntaxe que celle qui est utilisée dans des fichiers C++. Des exemples sont fournis dans le fichier .vsct de fichiers qui le **nouveau projet** Assistant créer un projet VSPackage.  
  
## <a name="optional-elements"></a>Éléments facultatifs  
 Certains éléments VSCT sont facultatifs. Si un `Parent` argument n’est pas spécifié, Group_Undefined:0 sera être implicite. Si un `Icon` argument n’est pas spécifié, guidOfficeIcon:msotcidNoIcon sera être implicite. Lorsqu’une touche de raccourci est définie, l’émulation, qui est généralement inutilisée, est facultative.  
  
 Éléments de bitmap peuvent être incorporés au moment de la compilation en spécifiant l’emplacement de la bande de bitmaps dans le `href` argument. La bande de bitmaps est copiée lors de la fusion et non extraites à partir des ressources de la DLL. Quand un `href` argument est fourni, le `usedList` argument devient facultatif, et tous les emplacements dans la bande de bitmaps sont considérés comme utilisé.  
  
 Toutes les valeurs GUID et l’ID doivent être définis à l’aide des noms symboliques. Ces noms peuvent être définies dans les fichiers d’en-tête ou dans VSCT \<symboles > sections. Les noms symboliques doivent être locales, inclus dans le cadre \<Include > éléments, ou référencé par \<Extern > éléments. Un nom symbolique est importé à partir d’un fichier d’en-tête spécifié dans un \<Extern > élément s’il suit le modèle simple de #define valeur du symbole. La valeur peut être un autre symbole, que ce symbole a été défini précédemment. Définitions de GUID doivent suivre le format OLE ou du C++. Les valeurs d’ID peuvent être chiffres décimaux ou hexadécimaux qui est précédés de 0 x, comme indiqué dans les lignes suivantes :  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0 x 62, 0xc8}}  
  
  Commentaires XML peuvent être utilisés, mais les outils d’interface (GUI) utilisateur graphique aller-retour peuvent les ignorer. Le contenu de \<Annotation > éléments sont garanties pour être conservée, quel que soit le format.  
  
## <a name="schema-hierarchy"></a>Hiérarchie de schéma  
 Un fichier .vsct a les éléments principaux suivants.  
  
 [Élément CommandTable](../extensibility/commandtable-element.md)  
  
 [Élément Extern](../extensibility/extern-element.md)  
  
 [Élément Include](../extensibility/include-element.md)  
  
 [Élément Define](../extensibility/define-element.md)  
  
 [Élément Commands](../extensibility/commands-element.md)  
  
 [Élément CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Élément KeyBindings](../extensibility/keybindings-element.md)  
  
 [Élément UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Élément Parent](../extensibility/parent-element.md)  
  
 [Élément Icon](../extensibility/icon-element.md)  
  
 [Élément Strings](../extensibility/strings-element.md)  
  
 [Élément Command Flag](../extensibility/command-flag-element.md)  
  
 [Élément Symbols](../extensibility/symbols-element.md)  
  
 [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans VSPackages](../extensibility/internals/command-routing-in-vspackages.md)

