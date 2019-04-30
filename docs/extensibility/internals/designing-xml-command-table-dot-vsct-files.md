---
title: Conception de Table de commande XML (. Fichiers VSCT) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e70a64e01e388af61127fd76f4a2fcee8e5a9b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910768"
---
# <a name="design-xml-command-table-vsct-files"></a>Concevoir des fichiers XML command table (.vsct)
Une table de commande XML (*.vsct*) fichier décrit la disposition et l’apparence des éléments de commande pour un VSPackage. Éléments de commande incluent des boutons, des zones de liste déroulante, des menus, des barres d’outils et des groupes d’éléments de la commande. Cet article décrit les fichiers de table de commande XML, comment elles affectent les menus et éléments de commande et comment les créer.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Commandes, menus, groupes et le fichier .vsct
 Le *.vsct* fichiers sont organisés autour des commandes, des menus et des groupes de commandes. Les balises XML dans le *.vsct* représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que des boutons de commande, le placement de commande et les bitmaps de fichiers.

 Lorsque vous créez un nouveau VSPackage s’affiche en exécutant la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de package, le modèle génère un *.vsct* fichier avec les éléments nécessaires pour une commande de menu, une fenêtre outil ou un éditeur personnalisé, en fonction de vos sélections. Cela *.vsct* fichier peut ensuite être modifié pour répondre aux exigences d’un VSPackage spécifique. Pour obtenir des exemples montrant comment modifier un *.vsct* de fichiers, consultez [étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md).

 Pour créer un nouveau, vide *.vsct* de fichiers, consultez [Comment : Créer un *.vsct* fichier](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, ajoutez les éléments XML, les attributs et les valeurs dans le fichier pour décrire la disposition d’élément de commande. Pour un schéma XML détaillé, consultez le [référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers .ctc et .vsct
 Tandis que la signification derrière le code XML des balises dans un *.vsct* fichier sont les mêmes que ces balises dans désormais déconseillé *.ctc* format de fichier, leur implémentation est un peu différente :

- La nouvelle  **\<extern >** balise est où vous font référence à d’autres *.h* fichiers à compiler, tels que ces fichiers pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barre d’outils.

- Tandis que *.vsct* fichiers de prise en charge la **/ include** instruction, en tant que *.ctc* font des fichiers, il comporte également un nouveau  **\<Importer >** élément. La différence est, **/ include** permet d’utiliser *tous les* des informations, tandis que  **\<Importer >** permet d’utiliser uniquement les noms.

- Bien que *.ctc* fichiers nécessitent un fichier d’en-tête dans lequel vous définissez vos directives de préprocesseur, un n’est pas obligatoire pour *.vsct* fichiers. Au lieu de cela, placez vos directives dans la table de symboles, située dans le  **\<symbole >** éléments, situés en bas de la *.vsct* fichier.

- *.VSCT* fonctionnalité des fichiers d’un  **\<Annotation >** balise, qui vous permet d’incorporer des informations que vous le souhaitez, telles que des notes ou même d’images.

- Les valeurs sont stockées en tant qu’attributs sur l’élément.

- Indicateurs de commande peuvent être stockées individuellement ou empilés.  Toutefois, IntelliSense, ne fonctionne pas sur les indicateurs de commande empilées. Pour plus d’informations sur les indicateurs de commande, consultez le [CommandFlag élément](../../extensibility/command-flag-element.md).

- Vous pouvez spécifier plusieurs types, tels que les listes déroulantes de fractionnement, combos, etc.

- Ne valident pas les GUID.

- Chaque élément d’interface utilisateur a une chaîne qui représente le texte qui s’affiche avec lui.

- Le parent est facultatif. Si omis, la valeur *groupe inconnu* est utilisé.

- Le *icône* argument est facultatif.

- Section de bitmap : Cette section est le même que dans un *.ctc* de fichiers, à ceci près que vous pouvez désormais spécifier un nom de fichier par le biais de Href qui est extraites à par le *vsct.exe* compilateur au moment de la compilation.

- ResID : L’ancien bitmap resource ID peut être utilisé et toujours sur le fonctionnement identique à celui de *.ctc* fichiers.

- HRef : Une nouvelle méthode qui vous permet de spécifier un nom de fichier pour la ressource bitmap. Il suppose que toutes sont utilisées, donc vous pouvez omettre la section utilisée. Le compilateur recherche tout d’abord pour les ressources locales pour le fichier, puis sur tous les partages réseau, et toutes les ressources définies par le **/I** basculer.

- Combinaison de touches : Ne plus avoir à spécifier un émulateur. Si vous ne spécifiez pas un, le compilateur suppose que l’éditeur et l’émulateur sont les mêmes.

- Keychord : Keychord a été supprimé. Le nouveau format est *Mod1, Key1, Key2, le Mod2*.  Vous pouvez spécifier un caractère, hexadécimal ou constante VK.

Le nouveau compilateur *vsct.exe*, compile les deux *.ctc* et *.vsct* fichiers. L’ancien *ctc.exe* compilateur, toutefois, ne reconnaissent pas ou ne sera pas compiler *.vsct* fichiers.

Vous pouvez utiliser la *vsct.exe* compilateur de convertir un existant *.cto* de fichiers dans un *.vsct* fichier. Pour plus d'informations, voir [Procédure : Créer un fichier .vsct à partir d’un fichier .cto existant](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Les éléments du fichier .vsct
 La table de commande présente la hiérarchie et les éléments suivants :

- [Élément CommandTable](../../extensibility/commandtable-element.md): Représente toutes les commandes, les groupes de menus et les menus associés le VSPackage.

- [Élément extern](../../extensibility/extern-element.md): Fait référence à tous les fichiers .h externe que vous voulez fusionner avec le *.vsct* fichier.

- [Élément include](../../extensibility/include-element.md): Fait référence à tous les fichiers supplémentaires en-tête (.h) pour effectuer une compilation avec votre *.vsct* fichier. Un *.vsct* fichier peut inclure *.h* fichiers contenant des constantes qui définissent des commandes, les groupes de menus et les menus qui fournit de l’IDE ou un autre package Visual Studio.

- [Élément Commands](../../extensibility/commands-element.md): Représente toutes les commandes individuelles qui peuvent être exécutés. Chaque commande possède les quatre éléments enfants suivants :

- [Élément menus](../../extensibility/menus-element.md): Représente tous les menus et barres d’outils dans le VSPackage. Les menus sont des conteneurs de groupes de commandes.

- [Élément Groups](../../extensibility/groups-element.md): Représente tous les groupes dans le VSPackage. Les groupes sont des ensembles de commandes individuelles.

- [Élément Buttons](../../extensibility/buttons-element.md): Représente tous les boutons de commande et les éléments de menu dans le VSPackage. Boutons sont des contrôles visuels qui peuvent être associés à des commandes.

- [Élément bitmaps](../../extensibility/bitmaps-element.md): Représente tous les bitmaps pour tous les boutons dans le VSPackage. Les images bitmap sont des images apparaissant à côté ou sur les boutons de commande, en fonction du contexte.

- [Élément CommandPlacements](../../extensibility/commandplacements-element.md): Indique les emplacements supplémentaires où chaque commande doit être placé dans les menus de votre VSPackage.

- [Élément VisibilityConstraints](../../extensibility/visibilityconstraints-element.md): Spécifie si une commande affiche tout fois ou uniquement dans certains contextes, par exemple quand une boîte de dialogue particulière ou une fenêtre s’affiche. Menus et commandes qui ont une valeur pour cet élément affiche uniquement lorsque le contexte spécifié est actif. Le comportement par défaut consiste à afficher la commande à tout moment.

- [Élément KeyBindings](../../extensibility/keybindings-element.md): Spécifie les combinaisons de touches pour les commandes. Autrement dit, un ou plusieurs combinaisons de touches qui doivent être activées pour exécuter la commande, telles que **Ctrl**+**S**.

- [Élément UsedCommands](../../extensibility/usedcommands-element.md): Informe le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement que bien que la commande spécifiée est implémentée par un autre code, lorsque le VSPackage actuel est actif, il fournit l’implémentation de la commande.

- [Élément Symbols](../../extensibility/symbols-element.md): Contient les noms de symboles et les ID de GUID pour toutes vos commandes dans le package.

## <a name="vsct-file-design-guidelines"></a>instructions de conception du fichier .vsct
 À la conception avec succès un *.vsct* de fichiers, suivez ces instructions.

- Commandes peuvent être placés uniquement dans les groupes, groupes peuvent être placés uniquement dans les menus et menus peuvent être placés uniquement dans les groupes. Uniquement les menus sont réellement affichées dans l’IDE, les groupes et les commandes ne sont pas.

- Sous-menus ne peut pas être directement attribués à un menu, mais doivent être attribués à un groupe, qui est assigné à son tour à un menu.

- Commandes, des sous-menus et des groupes peuvent avoir à un groupe de parentage ou menu à l’aide du champ parent de leur définition directive.

- Organisation d’une table de commande uniquement via les champs dans les directives parent a une limitation importante. Les directives qui définissent des objets peuvent prendre l’argument qu’un seul parent.

- Réutilisation des commandes, des groupes ou des sous-menus requiert l’utilisation d’une directive de nouveau pour créer une nouvelle instance de l’objet avec son propre `GUID:ID` paire.

- Chaque `GUID:ID` paire doit être unique. Réutilisation d’une commande, par exemple, placée dans un menu, une barre d’outils, ou dans un menu contextuel, est gérée par le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.

- Commandes et sous-menus peuvent également être affectés à plusieurs groupes et les groupes peuvent être affectés à plusieurs menus en utilisant la [élément Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>notes de fichiers .vsct
 Si vous apportez des modifications à un *.vsct* fichier une fois que vous les compilez et placez dans une DLL satellite native, vous devez exécuter **devenv.exe /setup /nosetupvstemplates**. Ainsi, les ressources de VSPackage spécifiées dans le Registre expérimental d’être relus et de la base de données interne qui décrit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à reconstruire.

 Pendant le développement, il est possible pour plusieurs projets de VSPackage peuvent être créés et enregistrés dans la ruche expérimentale du Registre pouvant conduire à un encombrement à confusion dans l’IDE. Pour résoudre ce problème, vous pouvez réinitialiser la ruche expérimentale pour supprimer toutes les modifications qu’ils peuvent avoir apportées à l’IDE et des VSPackages enregistrés tous les paramètres par défaut. Pour réinitialiser la ruche expérimentale, utilisez l’outil CreateExpInstance.exe fourni avec le SDK Visual Studio. Vous trouverez à l’adresse :

 *% PROGRAMFILES (x 86) %\Visual Studio\\\<version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Exécutez l’outil à l’aide de la commande **CreateExpInstance /Reset**. N’oubliez pas que cet outil supprime la ruche expérimentale tous des VSPackages enregistrés normalement pas installés avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Voir aussi
- [Étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md)