---
title: VsCT XML Schema Référence (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697901"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML référence schéma
Fournit une table d’éléments de schéma compilateur de table de commandement, avec des éléments et des attributs autorisés pour chaque enfant.

 Un fichier de configuration de table de commande (.vsct) basé sur XML définit les éléments de commande qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Ces éléments comprennent des éléments de menu, des menus, des barres d’outils et des boîtes combo.

> [!NOTE]
> Le compilateur VSCT peut exécuter un préprocesseur sur le fichier .vsct. Étant donné qu’il s’agit généralement du préprocesseur C, vous pouvez définir les éléments inclus et les macros qui ont la même syntaxe qui est utilisée dans les fichiers C. Des exemples de cela sont fournis dans le fichier .vsct que l’assistant **du nouveau projet** crée pour un projet VSPackage.

## <a name="optional-elements"></a>Éléments facultatifs
 Certains éléments VSCT sont facultatifs. Si `Parent` un argument n’est pas précisé, Group_Undefined:0 sera implicite. Si `Icon` un argument n’est pas spécifié, guidOfficeIcon:msotcidNoIcon sera implicite. Lorsqu’une clé de raccourci est définie, l’émulation, qui est généralement inutilisée, est facultative.

 Les éléments Bitmap peuvent être intégrés au moment de la compilation `href` en spécifiant l’emplacement de la bande de bitmap dans l’argument. La bande de bitmap est copiée pendant la fusion plutôt que extraite des ressources de la DLL. Lorsqu’un `href` argument est `usedList` fourni, l’argument devient facultatif, et toutes les fentes dans la bande de bitmap sont considérées comme utilisées.

 Toutes les valeurs DE GUID et d’identification doivent être définies en utilisant des noms symboliques. Ces noms peuvent être définis dans \<les fichiers d’en-tête ou dans les symboles VSCT> sections. Les noms symboliques doivent \<être locaux, inclus par l’intermédiaire d’éléments de> inclus, ou référencés par \<Extern> éléments. Un nom symbolique est importé d’un \<fichier d’en-tête spécifié dans un élément externe> s’il suit le modèle simple de #define SYMBOL VALUE. La valeur peut être un autre symbole tant que ce symbole a été défini précédemment. Les définitions DE GUID doivent suivre le format OLE ou CMD. Les valeurs d’identification peuvent être soit des chiffres décimales, soit des chiffres hexadecimals qui sont précédés de 0x, comme le montrent les lignes suivantes :

- 6D484634-E53D-4a2c-ADCB-55145C9362C8

- 0x6d484634, 0xe53d, 0x4a2c, 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 .

  Les commentaires XML peuvent être utilisés, mais les outils d’interface utilisateur graphique (GUI) aller-retour peuvent les jeter. Le contenu \<d’Annotation> éléments sont garantis pour être maintenus quel que soit le format.

## <a name="schema-hierarchy"></a>Hiérarchie de schéma
 Un fichier .vsct a les éléments majeurs suivants.

- [Élément CommandTable](../extensibility/commandtable-element.md)

- [Élément extern](../extensibility/extern-element.md)

- [Inclure l’élément](../extensibility/include-element.md)

- [Définir l’élément](../extensibility/define-element.md)

- [Élément de commande](../extensibility/commands-element.md)

- [Élément CommandPlacements](../extensibility/commandplacements-element.md)

- [VisibilityConstraints élément](../extensibility/visibilityconstraints-element.md)

- [Élément KeyBindings](../extensibility/keybindings-element.md)

- [Élément Decommands usagé](../extensibility/usedcommands-element.md)

- [Élément parent](../extensibility/parent-element.md)

- [Élément d’icône](../extensibility/icon-element.md)

- [Élément cordes](../extensibility/strings-element.md)

- [Élément de drapeau de commande](../extensibility/command-flag-element.md)

- [Élément symbole](../extensibility/symbols-element.md)

- [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Itinéraire de commande dans VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
