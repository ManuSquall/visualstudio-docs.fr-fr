---
title: Conception de la table de commandes XML (. Fichiers vsct) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196846"
---
# <a name="designing-xml-command-table-vsct-files"></a>Conception de fichiers XML Command Table (.Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fichier de table de commandes XML (. vsct) décrit la disposition et l’apparence des éléments de commande pour un VSPackage. Les éléments de commande incluent des boutons, des zones de liste modifiable, des menus, des barres d’outils et des groupes d’éléments de commande. Cette rubrique décrit les fichiers de table de commandes XML, comment ils affectent les éléments de commande et les menus, et comment les créer.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Commandes, menus, groupes et le fichier. vsct  
 les fichiers. vsct sont organisés autour des commandes, des menus et des groupes de commandes. Les balises XML dans le fichier. vsct représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que les boutons de commande, le positionnement des commandes et les bitmaps.  
  
 Lorsque vous créez un nouveau VSPackage en exécutant le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modèle de package, le modèle génère un fichier. vsct avec les éléments nécessaires pour une commande de menu, une fenêtre outil ou un éditeur personnalisé, en fonction de vos sélections. Ce fichier. vsct peut ensuite être modifié pour répondre aux exigences d’un VSPackage spécifique. Pour obtenir des exemples de modification d’un fichier. vsct, consultez les exemples dans [extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Pour créer un nouveau fichier. vsct vide, consultez [Comment : créer un. Fichier vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, vous ajoutez des éléments, des attributs et des valeurs XML au fichier pour décrire la disposition des éléments de commande. Pour obtenir un schéma XML détaillé, consultez la [référence de schéma XML vsct](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers. CTC et. vsct  
 Bien que la signification derrière les balises XML dans un fichier. vsct est identique à celle du format de fichier. CTC maintenant déconseillé, leur implémentation est légèrement différente.  
  
- La nouvelle **\<extern>** balise vous permet de référencer d’autres fichiers. h à compiler, tels que ceux de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barre d’outils.  
  
- Tandis que les fichiers. vsct prennent en charge l’instruction **/include** , comme le font les fichiers. CTC, il comprend également un nouvel \<**import> élément * *. La différence est, **/include** apporte **toutes** les informations, mais \<**import> * * apporte uniquement les noms.  
  
- Bien que les fichiers. CTC requièrent un fichier d’en-tête dans lequel vous définissez vos directives de préprocesseur, il n’est pas nécessaire pour les fichiers. vsct. Placez plutôt vos directives dans la table de symboles, situées dans les **\<Symbol>** éléments, situées en bas du fichier. vsct.  
  
- les fichiers. vsct intègrent une **\<Annotation>** balise, qui vous permet d’incorporer toutes les informations de votre choix, telles que des notes ou même des images.  
  
- Les valeurs sont stockées en tant qu’attributs sur l’élément.  
  
- Les indicateurs de commande peuvent être stockés individuellement ou empilés.  Toutefois, IntelliSense ne fonctionne pas sur les indicateurs de commande empilés. Pour plus d’informations sur les indicateurs de commande, consultez l' [élément indicateur de commande](../../extensibility/command-flag-element.md).  
  
- Vous pouvez spécifier plusieurs types, par exemple fractionner les listes déroulantes, combos, etc.  
  
- Les GUID ne sont pas validés.  
  
- Chaque élément d’interface utilisateur a une chaîne qui représente le texte qui s’affiche avec lui.  
  
- Le parent est facultatif. En cas d’omission, la valeur « Group Unknown » est utilisée.  
  
- L’argument Icon est facultatif.  
  
- La section bitmap, identique à un fichier. CTC, sauf que vous pouvez maintenant spécifier un nom de fichier via href qui sera extrait par le compilateur vsct.exe au moment de la compilation.  
  
- ResID : l’ancien ID de ressource bitmap peut être utilisé et fonctionne toujours de la même façon que dans les fichiers. CTC.  
  
- HRef : nouvelle méthode qui vous permet de spécifier un nom de fichier pour la ressource bitmap. Il part du principe que tous les sont utilisés, vous pouvez donc omettre la section used. Le compilateur recherche d’abord des ressources locales pour le fichier, puis sur tous les partages réseau et toutes les ressources définies par le commutateur/I.  
  
- KeyBinding : vous n’avez plus besoin de spécifier un émulateur. Si vous en spécifiez une, le compilateur suppose que l’éditeur et l’émulateur sont identiques.  
  
- Keycorde--a été supprimé. Le nouveau format est Key1, MOD1, key2, MOD2.  Vous pouvez spécifier une constante de type caractère, hexadécimal ou VK.  
  
  Le nouveau compilateur, vsct.exe, compile les fichiers. CTC et. vsct. Toutefois, l’ancien compilateur de ctc.exe ne reconnaît pas et ne compile pas les fichiers. vsct.  
  
  Vous pouvez utiliser le compilateur vsct.exe pour convertir un fichier. Directeur existant en fichier. vsct. Pour plus d’informations à ce sujet, consultez [Comment : créer un. Fichier vsct à partir d’un existant. Fichier de directeur technique](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Éléments du fichier. vsct  
 La table de commandes contient la hiérarchie et les éléments suivants :  
  
 [Élément CommandTable](../../extensibility/commandtable-element.md) : représente l’ensemble des commandes, groupes de menus et menus associés au VSPackage.  
  
 [Élément extern](../../extensibility/extern-element.md) : référence tous les fichiers. h externes que vous souhaitez fusionner avec le fichier. vsct.  
  
 [Élément Include](../../extensibility/include-element.md) : référence tous les fichiers d’en-tête (. h) supplémentaires que vous souhaitez compiler avec votre fichier. vsct. Un fichier. vsct peut inclure des fichiers. h contenant des constantes qui définissent des commandes, des groupes de menus et des menus fournis par l’IDE ou un autre VSPackage.  
  
 [Commands, élément](../../extensibility/commands-element.md) : représente toutes les commandes qui peuvent être exécutées. Chaque commande possède les quatre éléments enfants suivants :  
  
 [Élément menus](../../extensibility/menus-element.md) : représente tous les menus et barres d’outils du VSPackage. Les menus sont des conteneurs pour les groupes de commandes.  
  
 [Groups, élément](../../extensibility/groups-element.md) : représente tous les groupes du VSPackage. Les groupes sont des collections de commandes individuelles.  
  
 [Élément Buttons](../../extensibility/buttons-element.md) : représente tous les boutons de commande et les éléments de menu du VSPackage. Les boutons sont des contrôles visuels qui peuvent être associés à des commandes.  
  
 [Bitmaps (élément](../../extensibility/bitmaps-element.md) ) : représente toutes les bitmaps de tous les boutons du VSPackage. Les bitmaps sont des images qui s’affichent en regard de ou sur les boutons de commande, selon le contexte.  
  
 [Élément CommandPlacements](../../extensibility/commandplacements-element.md) : indique les emplacements supplémentaires où les commandes individuelles doivent être site dans les menus de votre VSPackage.  
  
 [Élément VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : spécifie si une commande s’affiche à tout moment ou uniquement dans certains contextes, par exemple lorsqu’une boîte de dialogue ou une fenêtre particulière est affichée. Les menus et les commandes qui ont une valeur pour cet élément s’affichent uniquement lorsque le contexte spécifié est actif. Le comportement par défaut consiste à afficher la commande à tout moment.  
  
 [KeyBindings (élément](../../extensibility/keybindings-element.md) ) : spécifie les combinaisons de touches pour les commandes. Autrement dit, une ou plusieurs combinaisons de touches qui doivent être enfoncées pour exécuter la commande, telles que **CTRL + S**.  
  
 [Élément UsedCommands](../../extensibility/usedcommands-element.md) : informe l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement que même si la commande spécifiée est implémentée par un autre code, lorsque le VSPackage actuel est actif, il fournit l’implémentation de la commande.  
  
 `Symbols Element` : Contient les noms de symboles et les ID de GUID pour toutes vos commandes dans le package.  
  
## <a name="vsct-file-design-guidelines"></a>. Instructions pour la conception de fichiers vsct  
 Pour concevoir correctement un fichier. vsct, suivez ces instructions.  
  
- Les commandes peuvent être placées uniquement dans des groupes, les groupes ne peuvent être placés que dans des menus, et les menus ne peuvent être placés que dans des groupes. Seuls les menus sont affichés dans l’IDE, les groupes et les commandes ne le sont pas.  
  
- Les sous-menus ne peuvent pas être directement attribués à un menu, mais ils doivent être assignés à un groupe, qui est à son tour affecté à un menu.  
  
- Les commandes, les sous-menus et les groupes peuvent être attribués à un groupe ou à un menu parent à l’aide du champ parent de leur directive de définition.  
  
- L’organisation d’une table de commandes uniquement via les champs parents dans les directives a une limitation significative. Les directives qui définissent des objets ne peuvent prendre qu’un seul argument parent.  
  
- La réutilisation des commandes, des groupes ou des sous-menus requiert l’utilisation d’une nouvelle directive pour créer une nouvelle instance de l’objet avec sa propre `GUID:ID` paire.  
  
- Chaque `GUID:ID` paire doit être unique. La réutilisation d’une commande qui a, par exemple, été placée dans un menu, une barre d’outils ou un menu contextuel, est gérée par l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
- Les commandes et les sous-menus peuvent également être affectés à plusieurs groupes, et les groupes peuvent être affectés à plusieurs menus à l’aide de l' [élément Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notes de fichier vsct  
 Si vous apportez des modifications à un fichier. vsct après la compilation et le placement dans une DLL satellite native, vous devez exécuter **devenv.exe/Setup/nosetupvstemplates**. Cela force la relecture des ressources VSPackage spécifiées dans le registre expérimental et la base de données interne qui décrit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour être reconstruite.  
  
 Pendant le développement, il est possible de créer et d’enregistrer plusieurs projets VSPackage dans la ruche expérimentale du Registre, ce qui peut entraîner des confusions dans l’IDE. Pour résoudre ce problème, vous pouvez rétablir les paramètres par défaut de la ruche expérimentale pour supprimer tous les VSPackages inscrits et toute modification apportée à l’IDE. Pour réinitialiser la ruche expérimentale, utilisez l’outil CreateExpInstance.exe fourni avec le kit de développement logiciel (SDK) Visual Studio. Vous pouvez le trouver à l’adresse  
  
 **% PROGRAMFILES (x86)% \ Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Exécutez l’outil à l’aide de la ligne de commande **CreateExpInstance/Reset**. N’oubliez pas que cet outil supprime de la ruche expérimentale tous les VSPackages inscrits qui ne sont pas normalement installés avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md)
