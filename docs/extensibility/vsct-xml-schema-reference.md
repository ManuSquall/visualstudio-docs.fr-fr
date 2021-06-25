---
title: Informations de référence sur le schéma XML VSCT | Microsoft Docs
description: Les Articles de référence de schéma XML VSCT décrivent les éléments de schéma du compilateur de table de commandes, avec des attributs et des éléments enfants autorisés pour chacun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d82cda9c91642b094deea50eda02676f9bb73f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905226"
---
# <a name="vsct-xml-schema-reference"></a>Référence du schéma XML VSCT
Fournit un tableau des éléments de schéma du compilateur de table de commandes, avec les éléments enfants et les attributs autorisés pour chacun.

 Un fichier de configuration de table de commandes basé sur XML (. vsct) définit les éléments de commande qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Ces éléments incluent des éléments de menu, des menus, des barres d’outils et des zones de liste modifiable.

> [!NOTE]
> Le compilateur VSCT peut exécuter un préprocesseur sur le fichier. vsct. Étant donné qu’il s’agit généralement du préprocesseur C++, vous pouvez définir des inclusions et des macros dont la syntaxe est identique à celle utilisée dans les fichiers C++. Des exemples sont fournis dans le fichier. vsct que l’Assistant **nouveau projet** crée pour un projet VSPackage.

## <a name="optional-elements"></a>Éléments facultatifs
 Certains éléments VSCT sont facultatifs. Si aucun `Parent` argument n’est spécifié, Group_Undefined : 0 sera implicite. Si un `Icon` argument n’est pas spécifié, guidOfficeIcon : msotcidNoIcon sera implicite. Lorsqu’une touche de raccourci est définie, l’émulation, qui n’est généralement pas utilisée, est facultative.

 Les éléments bitmap peuvent être incorporés au moment de la compilation en spécifiant l’emplacement de la bande de bitmaps dans l' `href` argument. La bande bitmap est copiée au cours de la fusion au lieu d’être extraite des ressources de la DLL. Quand un `href` argument est fourni, l' `usedList` argument devient facultatif et tous les emplacements de la bande bitmap sont considérés comme étant utilisés.

 Toutes les valeurs GUID et ID doivent être définies à l’aide de noms symboliques. Ces noms peuvent être définis dans des fichiers d’en-tête ou dans des \<Symbols> sections vsct. Les noms symboliques doivent être locaux, inclus dans des \<Include> éléments ou référencés par des \<Extern> éléments. Un nom symbolique est importé à partir d’un fichier d’en-tête spécifié dans un \<Extern> élément s’il suit le modèle simple de #define valeur de symbole. La valeur peut être un autre symbole, à condition que ce symbole ait été défini précédemment. Les définitions de GUID doivent suivre le format OLE ou C++. Les valeurs d’ID peuvent être soit des chiffres décimaux, soit des chiffres hexadécimaux précédés de 0x, comme indiqué dans les lignes suivantes :

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xC8}}

  Les commentaires XML peuvent être utilisés, mais les outils d’interface utilisateur graphique (GUI) d’aller-retour peuvent les ignorer. Le contenu des \<Annotation> éléments est garanti être conservé quel que soit le format.

## <a name="schema-hierarchy"></a>Hiérarchie de schéma
 Un fichier. vsct contient les éléments principaux suivants.

- [Élément CommandTable](../extensibility/commandtable-element.md)

- [Élément extern](../extensibility/extern-element.md)

- [Élément Include](../extensibility/include-element.md)

- [Définir l’élément](../extensibility/define-element.md)

- [Élément Commands](../extensibility/commands-element.md)

- [Élément CommandPlacements](../extensibility/commandplacements-element.md)

- [Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [KeyBindings (élément)](../extensibility/keybindings-element.md)

- [Élément UsedCommands](../extensibility/usedcommands-element.md)

- [Élément parent](../extensibility/parent-element.md)

- [Icon, élément](../extensibility/icon-element.md)

- [Élément Strings](../extensibility/strings-element.md)

- [Élément d’indicateur de commande](../extensibility/command-flag-element.md)

- [Élément Symbols](../extensibility/symbols-element.md)

- [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Voir aussi
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans les VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
