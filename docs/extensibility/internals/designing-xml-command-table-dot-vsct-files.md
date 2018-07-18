---
title: Conception de Table de commande XML (. Fichiers VSCT) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 865baa3f7b4b0fe4cbbaf2cdf34e9e8041d5c121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133357"
---
# <a name="designing-xml-command-table-vsct-files"></a>Conception de Table de commande XML (. Fichiers VSCT)
Un fichier de table (.vsct) de commande XML décrit la disposition et l’apparence des éléments de commande pour un VSPackage. Les éléments de commande incluent des boutons, des zones de liste déroulante, des menus, des barres d’outils et des groupes d’éléments de la commande. Cette rubrique décrit les fichiers de la table commandes XML, comment ils affectent les menus et éléments de commande et comment les créer.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Commandes, Menus, groupes et le fichier .vsct
 les fichiers .vsct sont organisés autour des commandes, des menus et des groupes de commandes. Les balises XML dans le fichier .vsct représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que les boutons de commande, le placement de commande et les bitmaps.

 Lorsque vous créez un nouveau VSPackage en exécutant la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de Package, le modèle génère un fichier .vsct avec les éléments nécessaires pour une commande de menu, une fenêtre outil ou un éditeur personnalisé, selon vos sélections. Ce fichier .vsct peut ensuite être modifié pour satisfaire les exigences d’un VSPackage spécifique. Pour obtenir des exemples de modification d’un fichier .vsct, consultez les exemples de [étendant les Menus et commandes](../../extensibility/extending-menus-and-commands.md).

 Pour créer un fichier .vsct vierge, consultez [Comment : créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, ajoutez les éléments XML, les attributs et les valeurs dans le fichier pour décrire la disposition d’élément de commande. Pour un schéma XML détaillé, consultez le [référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers .ctc et .vsct
 Alors que la signification des balises XML dans un fichier .vsct est les mêmes que celles figurant dans le présent déconseillée le format de fichier .ctc, leur implémentation est légèrement différente.

-   La nouvelle  **\<extern >** balise est où vous les autres fichiers .h à compiler, telles que celles pour référencer le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barre d’outils.

-   Lors de la prise en charge des fichiers .vsct le **/ inclure** instruction, comme les fichiers .ctc, il comporte également un nouveau \< **Importer >** élément. La différence est, **/ inclure** permet de bénéficier de **tous les** des informations, mais \< **Importer >** affiche uniquement les noms.

-   Bien que .ctc fichiers nécessitent un fichier d’en-tête dans lequel vous définissez les directives de préprocesseur, un n’est pas obligatoire pour les fichiers .vsct. Au lieu de cela, placez vos directives dans la table de symboles, située dans le  **\<symbole >** éléments, situés en bas du fichier .vsct.

-   fonctionnalité des fichiers .vsct un  **\<Annotation >** balise, qui vous permet d’incorporer toutes les informations que vous le souhaitez, telles que des notes ou même d’images.

-   Les valeurs sont stockées en tant qu’attributs sur l’élément.

-   Les indicateurs de commande peuvent être stockées individuellement ou empilés.  Toutefois, IntelliSense, ne fonctionne pas sur les indicateurs de commande empilées. Pour plus d’informations sur les indicateurs de commande, consultez le [élément indicateur de commande](../../extensibility/command-flag-element.md).

-   Vous pouvez spécifier plusieurs types, tels que les listes déroulantes de fractionnement, combinés, etc.

-   Ne pas valider les GUID.

-   Chaque élément d’interface utilisateur a une chaîne qui représente le texte qui s’affiche avec lui.

-   Parent est facultatif. Si omis, la valeur « Groupe inconnu » est utilisée.

-   L’argument de l’icône est facultatif.

-   La section bitmap--identique à un .ctc de fichiers, à ceci près que vous pouvez maintenant spécifier un nom de fichier via href qui est extraites par le compilateur vsct.exe au moment de la compilation.

-   ResID--l’ID de ressource bitmap ancien peut être utilisé et fonctionne toujours de la même que dans les fichiers .ctc.

-   HRef : une nouvelle méthode qui vous permet de spécifier un nom de fichier pour la ressource bitmap. Il suppose que toutes les sont utilisées, donc vous pouvez omettre la section utilisée. Le compilateur recherche d’abord les ressources locales pour le fichier, puis sur tous les partages réseau et les ressources définies par le commutateur /I.

-   KeyBinding--Vous n’avez plus à spécifier un émulateur. Si vous ne spécifiez pas un, le compilateur suppose que l’éditeur et l’émulateur sont identiques.

-   Keychord--a été supprimé. Le nouveau format est Mod1, Key1, Key2, le Mod2.  Vous pouvez spécifier un caractère, hexadécimal ou constante VK.

 Le nouveau compilateur, vsct.exe, compile les fichiers .ctc et .vsct. L’ancien compilateur ctc.exe, toutefois, sera reconnaît ni compiler des fichiers .vsct.

 Vous pouvez utiliser le compilateur vsct.exe pour convertir un fichier .cto existant dans un fichier .vsct. Pour plus d’informations, consultez [Comment : créer un. Fichier VSCT d’un existant. Fichier CTO](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Les éléments du fichier .vsct
 La table de commande présente la hiérarchie et les éléments suivants :

 [Élément de CommandTable](../../extensibility/commandtable-element.md) : représente l’ensemble de commandes, des groupes de menus et des menus associés le VSPackage.

 [Élément de extern](../../extensibility/extern-element.md) : fait référence à tous les fichiers .h externe que vous souhaitez fusionner avec le fichier .vsct.

 [Élément include](../../extensibility/include-element.md) : fait référence à des fichiers supplémentaires en-tête (.h) à compiler en même temps que le fichier de your.vsct. Un fichier .vsct peut inclure les fichiers .h contenant des constantes qui définissent des commandes, les groupes de menus et les menus qui fournit de l’IDE ou un autre VSPackage.

 [Commandes d’élément](../../extensibility/commands-element.md) , représente toutes les commandes individuelles qui peuvent être exécutés. Chaque commande possède les éléments quatre enfants suivants :

 [Élément de menus](../../extensibility/menus-element.md) : représente tous les menus et barres d’outils dans le VSPackage. Les menus sont des conteneurs pour les groupes de commandes.

 [Élément groupes](../../extensibility/groups-element.md) : représente tous les groupes dans le VSPackage. Les groupes sont des ensembles de commandes individuelles.

 [Boutons d’élément](../../extensibility/buttons-element.md) : représente tous les boutons de commande et éléments de menu dans le VSPackage. Boutons sont des contrôles visuels qui peuvent être associés à des commandes.

 [Élément de bitmaps](../../extensibility/bitmaps-element.md) : représente tous les bitmaps pour tous les boutons dans le VSPackage. Les images bitmap sont des images affichées à côté ou sur les boutons de commande, en fonction du contexte.

 [Élément de CommandPlacements](../../extensibility/commandplacements-element.md) — indique les autres emplacements où chaque commande doit être placé dans les menus de votre VSPackage.

 [Élément de VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) — spécifie ou non une commande affiche à toutes les heures, ou uniquement dans certains contextes, tels que lorsqu’une boîte de dialogue particulière ou d’une fenêtre s’affiche. Menus et commandes qui ont une valeur de cet élément affiche uniquement lorsque le contexte spécifié est actif. Le comportement par défaut consiste à afficher de la commande à tout moment.

 [Élément de combinaisons de touches](../../extensibility/keybindings-element.md) : Spécifie les combinaisons de touches pour les commandes. Autrement dit, une ou plusieurs combinaisons de touches sur lesquelles appuyer pour exécuter la commande, telles que **CTRL + S**.

 [Élément de UsedCommands](../../extensibility/usedcommands-element.md) — Informs le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement que bien que la commande spécifiée est implémentée par un autre code, quand le VSPackage actuel est actif, il fournit l’implémentation de la commande.

 `Symbols Element` : Contient les noms de symboles et d’un ID de GUID pour toutes les commandes dans le package.

## <a name="vsct-file-design-guidelines"></a>. Règles de conception de fichier VSCT
 Pour concevoir un fichier .vsct, suivez ces instructions.

-   Commandes peuvent être placés uniquement dans les groupes, les groupes peuvent être placés uniquement dans les menus et menus peuvent être placés uniquement dans les groupes. Uniquement les menus sont réellement affichées dans l’IDE, les groupes et les commandes ne sont pas.

-   Sous-menus ne peut pas être directement attribués à un menu, mais doivent être affectés à un groupe, qui est ensuite assigné à un menu.

-   Groupes, des commandes et des sous-menus attribuable à un groupe de parenté ou un menu à l’aide du champ parent de leur définition directive.

-   Organisation d’une table de commandes uniquement via les champs parent dans les directives a une limitation importante. Les directives qui définissent des objets peuvent prendre l’argument qu’un seul parent.

-   Réutilisation des commandes, des groupes ou des sous-menus requiert l’utilisation d’une directive de nouveau pour créer une nouvelle instance de l’objet avec son propre `GUID:ID` paire.

-   Chaque `GUID:ID` paire doit être unique. Réutilisation d’une commande, par exemple, placée dans un menu, une barre d’outils, ou dans un menu contextuel, est gérée par le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.

-   Commandes et des sous-menus peuvent également être affectés à plusieurs groupes et les groupes peuvent être affectés à plusieurs menus à l’aide de la [élément Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>. Notes sur le fichier VSCT
 Si vous apportez des modifications à un fichier .vsct une fois que vous le compiler et placez dans une DLL satellite de native, vous devez exécuter **devenv.exe /setup /nosetupvstemplates**. Cette opération force les ressources VSPackage spécifiés dans le Registre expérimental d’être relus et la base de données interne qui décrit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à reconstruire.

 Pendant le développement, il est possible pour plusieurs projets VSPackage doit être créé et enregistré dans la ruche du Registre expérimentale pouvant conduire à confusion l’encombrement dans l’IDE. Pour résoudre ce problème, vous pouvez réinitialiser la ruche expérimentale pour les paramètres par défaut pour supprimer tous des VSPackages et toutes les modifications qu’ils ont peuvent apportées à l’IDE. Pour réinitialiser la ruche expérimentale, utilisez l’outil de CreateExpInstance.exe qui est fourni avec le Kit de développement logiciel Visual Studio. Vous trouverez à l’adresse

 **% PROGRAMFILES (x 86) %\Visual Studio \<version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**

 Exécutez l’outil à l’aide de la ligne de commande **CreateExpInstance /Reset**. N’oubliez pas de cet outil supprime de la ruche expérimentale tous les packages enregistrés VS pas normalement installées avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Voir aussi
 [Extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md)