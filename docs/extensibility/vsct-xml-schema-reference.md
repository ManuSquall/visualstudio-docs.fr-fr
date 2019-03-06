---
title: Référence du schéma XML VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2643c88eaf133d41fba7a8112f9b92150be3148
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684635"
---
# <a name="vsct-xml-schema-reference"></a>Référence du schéma XML VSCT
Fournit un tableau d’éléments de schéma du compilateur de Table de commande, avec enfant autorisé éléments et attributs pour chacun.

 Un fichier de configuration (.vsct) de table de commande basé sur XML définit les éléments de commande qui fournit un VSPackage à l’environnement de développement intégré (IDE). Ces éléments incluent les éléments de menu, des menus, des barres d’outils et des zones de liste déroulante.

> [!NOTE]
>  Le compilateur VSCT peut exécuter un préprocesseur sur le fichier .vsct. Comme il s’agit en général le préprocesseur, que vous pouvez définir C++ inclut et macros qui ont la même syntaxe que celle qui est utilisée dans des fichiers C++. Des exemples sont fournis dans le fichier .vsct de fichiers qui le **nouveau projet** Assistant créer un projet VSPackage.

## <a name="optional-elements"></a>Éléments facultatifs
 Certains éléments VSCT sont facultatifs. Si un `Parent` argument n’est pas spécifié, Group_Undefined:0 sera être implicite. Si un `Icon` argument n’est pas spécifié, guidOfficeIcon:msotcidNoIcon sera être implicite. Lorsqu’une touche de raccourci est définie, l’émulation, qui est généralement inutilisée, est facultative.

 Éléments de bitmap peuvent être incorporés au moment de la compilation en spécifiant l’emplacement de la bande de bitmaps dans le `href` argument. La bande de bitmaps est copiée lors de la fusion et non extraites à partir des ressources de la DLL. Quand un `href` argument est fourni, le `usedList` argument devient facultatif, et tous les emplacements dans la bande de bitmaps sont considérés comme utilisé.

 Toutes les valeurs GUID et l’ID doivent être définis à l’aide des noms symboliques. Ces noms peuvent être définies dans les fichiers d’en-tête ou dans VSCT \<symboles > sections. Les noms symboliques doivent être locales, inclus dans le cadre \<Include > éléments, ou référencé par \<Extern > éléments. Un nom symbolique est importé à partir d’un fichier d’en-tête spécifié dans un \<Extern > élément s’il suit le modèle simple de #define valeur du symbole. La valeur peut être un autre symbole, que ce symbole a été défini précédemment. Définitions de GUID doivent suivre le format OLE ou du C++. Les valeurs d’ID peuvent être chiffres décimaux ou hexadécimaux qui est précédés de 0 x, comme indiqué dans les lignes suivantes :

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Commentaires XML peuvent être utilisés, mais les outils d’interface (GUI) utilisateur graphique aller-retour peuvent les ignorer. Le contenu de \<Annotation > éléments sont garanties pour être conservée, quel que soit le format.

## <a name="schema-hierarchy"></a>Hiérarchie de schéma
 Un fichier .vsct a les éléments principaux suivants.

- [Élément CommandTable](../extensibility/commandtable-element.md)

- [Élément extern](../extensibility/extern-element.md)

- [Élément Include](../extensibility/include-element.md)

- [Définir l’élément](../extensibility/define-element.md)

- [Élément Commands](../extensibility/commands-element.md)

- [Élément CommandPlacements](../extensibility/commandplacements-element.md)

- [Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Élément KeyBindings](../extensibility/keybindings-element.md)

- [Élément UsedCommands](../extensibility/usedcommands-element.md)

- [Élément parent](../extensibility/parent-element.md)

- [Élément Icon](../extensibility/icon-element.md)

- [Élément Strings](../extensibility/strings-element.md)

- [Élément Command Flag](../extensibility/command-flag-element.md)

- [Élément Symbols](../extensibility/symbols-element.md)

- [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans VSPackages](../extensibility/internals/command-routing-in-vspackages.md)