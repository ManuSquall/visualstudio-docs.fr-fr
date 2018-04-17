---
title: Référence du schéma XML de VSCT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8b8b796f4b5740f90a8755bdf158735387eaa90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="vsct-xml-schema-reference"></a>Référence du schéma XML de VSCT
Fournit un tableau d’éléments de schéma du compilateur Table de commande, avec l’enfant autorisé éléments et attributs pour chacun.  
  
 Un fichier de configuration (.vsct) de table de commande XML définit les éléments de la commande par un VSPackage à l’environnement de développement intégré (IDE). Ces éléments incluent les éléments de menu, des menus, des barres d’outils et des zones de liste déroulante.  
  
> [!NOTE]
>  Le compilateur VSCT peut exécuter un préprocesseur sur le fichier .vsct. Comme il s’agit généralement le préprocesseur, que vous pouvez définir C++ inclut et macros qui ont la même syntaxe qui est utilisée dans des fichiers C++. Des exemples sont fournis dans le .vsct de fichiers qui le **nouveau projet** Assistant créer un projet VSPackage.  
  
## <a name="optional-elements"></a>Éléments facultatifs  
 Certains éléments VSCT sont facultatifs. Si un `Parent` argument n’est pas spécifié, Group_Undefined:0 sera être déduit. Si un `Icon` argument n’est pas spécifié, guidOfficeIcon:msotcidNoIcon sera être déduit. Lorsqu’une touche de raccourci est définie, l’émulation, qui est généralement inutilisée, est facultative.  
  
 Éléments de l’image bitmap peuvent être incorporées au moment de la compilation en spécifiant l’emplacement de la bande de la bitmap dans le `href` argument. La bande de la bitmap est copiée lors de la fusion plutôt qu’extraites à partir des ressources de la DLL. Lorsqu’un `href` argument est fourni, le `usedList` argument est facultatif, et tous les emplacements dans la bande de bitmap sont considérés comme utilisé.  
  
 Toutes les valeurs GUID et l’ID doivent être définis à l’aide des noms symboliques. Ces noms peuvent être définies dans les fichiers d’en-tête ou dans VSCT \<symboles > sections. Les noms symboliques doivent être locales, inclus via \<Include > éléments, ou référencée par \<Extern > éléments. Un nom symbolique est importé à partir d’un fichier d’en-tête spécifié dans un \<Extern > élément si elle suit le modèle simple de #define valeur de symbole. La valeur peut être un autre symbole tant que ce symbole a été défini précédemment. Définitions de GUID doivent suivre le format OLE ou du C++. Les valeurs de code peuvent être des chiffres décimaux ou chiffres hexadécimaux qui sont précédées de 0 x, comme indiqué dans les lignes suivantes :  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0x62, 0xc8}}  
  
 Commentaires XML peuvent être utilisés, mais les outils de l’interface (GUI) d’aller-retour graphique utilisateur peuvent les ignorer. Le contenu de \<Annotation > éléments sont garantis être conservée, quelle que soit le format.  
  
## <a name="schema-hierarchy"></a>Hiérarchie de schéma  
 Un fichier .vsct possède les éléments principaux suivants.  
  
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
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans VSPackages](../extensibility/internals/command-routing-in-vspackages.md)