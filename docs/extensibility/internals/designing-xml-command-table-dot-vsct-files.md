---
title: Conception de la table de commandement XML (. Vsct) Fichiers (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708751"
---
# <a name="design-xml-command-table-vsct-files"></a>Concevoir des fichiers de table de commande XML (.vsct)
Un fichier XML de commande *(.vsct)* décrit la disposition et l’apparence des éléments de commande d’un VSPackage. Les éléments de commande comprennent des boutons, des boîtes combo, des menus, des barres d’outils et des groupes d’éléments de commande. Cet article décrit les fichiers de table de commande XML, comment ils affectent les éléments de commande et les menus, et comment les créer.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Commandes, menus, groupes et le fichier .vsct
 Les fichiers *.vsct* sont organisés autour des commandes, des menus et des groupes de commandement. Les balises XML dans le fichier *.vsct* représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que les boutons de commande, le placement de commande et les bitmaps.

 Lorsque vous créez un nouveau VSPackage en exécutant le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de paquet, le modèle génère un fichier *.vsct* avec les éléments nécessaires pour une commande de menu, une fenêtre d’outil ou un éditeur personnalisé, selon vos sélections. Ce fichier *.vsct* peut ensuite être modifié pour répondre aux exigences d’un VSPackage spécifique. Pour des exemples de la façon de modifier un fichier *.vsct,* voir [Extend menus et commandes](../../extensibility/extending-menus-and-commands.md).

 Pour créer un nouveau fichier *.vsct* vierge, voir [Comment : Créer un fichier *.vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, vous ajoutez des éléments, des attributs et des valeurs XML au fichier pour décrire la disposition de l’élément de commande. Pour un schéma XML détaillé, voir la [référence VSCT XML schéma](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers .ctc et .vsct
 Alors que le sens derrière les balises XML dans un fichier *.vsct* sont les mêmes que ces balises dans le format de fichier *.ctc* maintenant déprécié, leur implémentation est un peu différente:

- La ** \<** nouvelle>balise est l’endroit où vous faites référence à d’autres fichiers *.h* à compiler, tels que ces fichiers pour la barre d’outils. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- Bien que les fichiers *.vsct* prennent en charge **l’énoncé /inclure,** comme le font les fichiers *.ctc,* il dispose également d’un nouvel ** \<élément>d’importation.** La différence est, **/inclure** apporte *toutes les* informations, tandis que ** \<l’importation>** apporte seulement les noms.

- Bien que les fichiers *.ctc* nécessitent un fichier d’en-tête dans lequel vous définissez vos directives de préprocesseur, on n’est pas nécessaire pour les fichiers *.vsct.* Placez plutôt vos directives dans le ** \<** tableau des symboles, situé dans le symbole>éléments, situés au bas du fichier *.vsct.*

- Les fichiers *.vsct* disposent d’une ** \<balise Annotation>,** qui vous permet d’intégrer toutes les informations que vous aimez, telles que des notes ou même des photos.

- Les valeurs sont stockées comme attributs sur l’élément.

- Les drapeaux de commande peuvent être stockés individuellement ou empilés.  IntelliSense, cependant, ne fonctionne pas sur des drapeaux de commandement empilés. Pour plus d’informations sur les drapeaux de commandement, voir [l’élément CommandFlag](../../extensibility/command-flag-element.md).

- Vous pouvez spécifier plusieurs types, tels que les décrocheurs fractionnés, les combos, etc.

- Les GUID ne valident pas.

- Chaque élément d’interface utilisateur a une chaîne qui représente le texte qui est affiché avec elle.

- Le parent est facultatif. Si omis, la valeur *Group Unknown* est utilisée.

- *L’argument Icon* est facultatif.

- Section Bitmap: Cette section est la même que dans un fichier *.ctc,* sauf que vous pouvez maintenant spécifier un nom de fichier via Href qui sera tiré par le *compilateur vsct.exe* au moment de compiler.

- ResID: L’id de ressources bitmap vieux peut être utilisé et fonctionne toujours le même que dans les fichiers *.ctc.*

- HRef: Une nouvelle méthode qui vous permet de spécifier un nom de fichier pour la ressource bitmap. Il suppose que tous sont utilisés, de sorte que vous pouvez omettre la section utilisée. Le compilateur recherche d’abord les ressources locales pour le fichier, puis sur les actions nettes, et toutes les ressources définies par le **commutateur /I.**

- Keybinding: Vous n’avez plus à spécifier un émulateur. Si vous en spécifiez un, le compilateur supposera que l’éditeur et l’émulateur sont les mêmes.

- Keychord: Keychord a été abandonné. Le nouveau format est *Key1,Mod1,Key2,Mod2*.  Vous pouvez spécifier soit un personnage, hexadecimal, ou VK constante.

Le nouveau compilateur, *vsct.exe*, compile à la fois les fichiers *.ctc* et *.vsct.* L’ancien *compilateur ctc.exe,* cependant, ne reconnaîtra pas ou compilera des fichiers *.vsct.*

Vous pouvez utiliser le *compilateur vsct.exe* pour convertir un fichier *.cto* existant en fichier *.vsct.* Pour plus d’informations, voir [Comment : Créer un fichier .vsct à partir d’un fichier .cto existant](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Les éléments du fichier .vsct
 Le tableau de commande a la hiérarchie et les éléments suivants :

- [Élément De la carte](../../extensibility/commandtable-element.md): Représente toutes les commandes, les groupes de menu et les menus associés à l’emballage VS.

- [Élément extern](../../extensibility/extern-element.md): Références à tous les fichiers externes .h que vous souhaitez fusionner avec le fichier *.vsct.*

- [Inclure l’élément](../../extensibility/include-element.md): Références à tous les fichiers d’en-tête supplémentaires (.h) que vous souhaitez compiler avec votre fichier *.vsct.* Un fichier *.vsct* peut inclure des fichiers *.h* contenant des constantes qui définissent les commandes, les groupes de menu et les menus que l’IDE ou un autre VSPackage fournit.

- [Élément de commande](../../extensibility/commands-element.md): Représente toutes les commandes individuelles qui peuvent être exécutées. Chaque commande comporte les quatre éléments suivants :

- [Élément menus](../../extensibility/menus-element.md): Représente tous les menus et barres d’outils du VSPackage. Les menus sont des conteneurs pour les groupes de commandes.

- [Élément des groupes](../../extensibility/groups-element.md): Représente tous les groupes du VSPackage. Les groupes sont des collections de commandes individuelles.

- [Élément boutons](../../extensibility/buttons-element.md): Représente tous les boutons de commande et les éléments de menu dans le VSPackage. Les boutons sont des commandes visuelles qui peuvent être associées aux commandes.

- [Bitmaps élément](../../extensibility/bitmaps-element.md): Représente toutes les bitmaps pour tous les boutons de la VSPackage. Les bitmaps sont des images qui s’affichent à côté ou sur les boutons de commande, selon le contexte.

- [Élément CommandPlacements](../../extensibility/commandplacements-element.md): Indique des emplacements supplémentaires où les commandes individuelles doivent être placées dans les menus de votre VSPackage.

- [VisibilitéConstraints élément](../../extensibility/visibilityconstraints-element.md): Précise si une commande s’affiche en tout temps, ou seulement dans certains contextes, comme lorsqu’une boîte de dialogue ou une fenêtre particulière est affichée. Les menus et les commandes qui ont une valeur pour cet élément ne s’afficheront que lorsque le contexte spécifié est actif. Le comportement par défaut est d’afficher la commande en tout temps.

- [Élément KeyBindings](../../extensibility/keybindings-element.md): Specifie toutes les liaisons clés pour les commandes. C’est-à-dire, une ou plusieurs combinaisons clés qui doivent être pressées pour exécuter la commande, comme **Ctrl**+**S**.

- [Élément UtiliséCommands](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Informe l’environnement que bien que la commande spécifiée soit implémentée par d’autres codes, lorsque le VSPackage actuel est actif, il fournit la mise en œuvre de la commande.

- [Élément symbole](../../extensibility/symbols-element.md): Contient les noms de symbole et les interfaces utilisateur guiD pour toutes vos commandes dans le paquet.

## <a name="vsct-file-design-guidelines"></a>lignes directrices de conception de fichiers .vsct
 Pour concevoir avec succès un fichier *.vsct,* suivez ces lignes directrices.

- Les commandes ne peuvent être placées qu’en groupes, les groupes ne peuvent être placés que dans les menus et les menus ne peuvent être placés qu’en groupes. Seuls les menus sont effectivement affichés dans l’IDE, les groupes et les commandes ne le sont pas.

- Submenus ne peut pas être directement affecté à un menu, mais doit être affecté à un groupe, qui est à son tour affecté à un menu.

- Les commandes, les sous-menus et les groupes peuvent être assignés à un groupe ou à un menu parental en utilisant le champ parent de leur directive déterminante.

- L’organisation d’un tableau de commandement uniquement dans les domaines parentaux dans les directives a une limitation importante. Les directives qui définissent les objets ne peuvent prendre qu’un seul argument parent.

- La réutilisation des commandes, des groupes ou des sous-hommes nécessite l’utilisation `GUID:ID` d’une nouvelle directive pour créer une nouvelle instance de l’objet avec sa propre paire.

- Chaque `GUID:ID` paire doit être unique. La réutilation d’une commande qui a, par exemple, été placée sur un menu, une barre d’outils ou sur un menu contextuelle, est gérée par l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

- Les commandes et le sous-présage peuvent également être affectés à plusieurs groupes, et les groupes peuvent être affectés à plusieurs menus en utilisant [l’élément Commandes](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>notes de fichier .vsct
 Si vous faites des modifications à un fichier *.vsct* après que vous le compilez et le placez dans un satellite natif DLL, vous devriez exécuter **devenv.exe /setup /nosetupvstemplates**. Cela oblige les ressources VSPackage spécifiées dans le registre expérimental à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] être relues et la base de données interne qui décrit à être reconstruite.

 Pendant le développement, il est possible que plusieurs projets VSPackage soient créés et enregistrés dans la ruche expérimentale qui peut conduire à un encombrement déroutant dans l’IDE. Pour résoudre ce problème, vous pouvez réinitialiser la ruche expérimentale dans les paramètres par défaut pour supprimer tous les VSPackages enregistrés et les modifications qu’ils peuvent avoir apportées à l’IDE. Pour réinitialiser la ruche expérimentale, utilisez l’outil CreateExpInstance.exe qui est livré avec le Visual Studio SDK. Vous pouvez le trouver à:

 *%PROGRAMFILES (x86)- Version\\\<Studio visuelle> SDK-VisualStudioIntegration-Tools-Bin-CreateExpInstance.exe*

 Exécutez l’outil en utilisant la commande **CreateExpInstance /Reset**. Rappelez-vous que cet outil supprime de la ruche expérimentale tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackages enregistrés normalement pas installé avec .

## <a name="see-also"></a>Voir aussi
- [Étendre les menus et les commandes](../../extensibility/extending-menus-and-commands.md)
