---
title: Conception de Table de commande XML (. Fichiers VSCT) | Microsoft Docs
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
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c7a4e07c45c5d651af057e1eb33c23d37601cb3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762805"
---
# <a name="designing-xml-command-table-vsct-files"></a>Conception de Table de commande XML (. Fichiers VSCT)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fichier de table (.vsct) de commande XML décrit la disposition et l’apparence des éléments de commande pour un VSPackage. Éléments de commande incluent des boutons, des zones de liste déroulante, des menus, des barres d’outils et des groupes d’éléments de la commande. Cette rubrique décrit les fichiers de table de commande XML, comment elles affectent les menus et éléments de commande et comment les créer.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Commandes, Menus, groupes et le fichier .vsct  
 fichiers .vsct organisés autour de commandes, des menus et des groupes de commandes. Les balises XML dans le fichier .vsct représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que des boutons de commande, le placement de commande et les bitmaps.  
  
 Lorsque vous créez un nouveau VSPackage s’affiche en exécutant la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modèle de Package, le modèle génère un fichier .vsct avec les éléments nécessaires pour une commande de menu, une fenêtre outil ou un éditeur personnalisé, en fonction de vos sélections. Ce fichier .vsct peut ensuite être modifié pour répondre aux exigences d’un VSPackage spécifique. Pour obtenir des exemples montrant comment modifier un fichier .vsct, consultez les exemples de [extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Pour créer un fichier .vsct vierge, consultez [Comment : créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, ajoutez les éléments XML, les attributs et les valeurs dans le fichier pour décrire la disposition d’élément de commande. Pour un schéma XML détaillé, consultez le [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers .ctc et .vsct  
 La signification derrière les balises XML dans un fichier .vsct est les mêmes que celles figurant dans le présent déconseillée le format de fichier .ctc, leur implémentation est un peu différente.  
  
- La nouvelle  **\<extern >** balise est où vous référencer d’autres fichiers .h à compiler, telles que celles pour le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barre d’outils.  
  
- Lors de prise en charge des fichiers .vsct le **/ include** instruction, comme les fichiers .ctc, il comporte également un nouveau \< **Importer >** élément. La différence est, **/ include** permet d’utiliser **tous les** des informations, mais \< **Importer >** permet d’utiliser uniquement les noms.  
  
- Tandis que les fichiers .ctc nécessitent un fichier d’en-tête dans lequel vous définissez vos directives de préprocesseur, un n’est pas requis pour les fichiers .vsct. Au lieu de cela, placez vos directives dans la table de symboles, située dans le  **\<symbole >** éléments, situés en bas du fichier .vsct.  
  
- fonctionnalité des fichiers .vsct un  **\<Annotation >** balise, qui vous permet d’incorporer des informations que vous le souhaitez, telles que des notes ou même d’images.  
  
- Les valeurs sont stockées en tant qu’attributs sur l’élément.  
  
- Indicateurs de commande peuvent être stockées individuellement ou empilés.  Toutefois, IntelliSense, ne fonctionne pas sur les indicateurs de commande empilées. Pour plus d’informations sur les indicateurs de commande, consultez le [élément Command Flag](../../extensibility/command-flag-element.md).  
  
- Vous pouvez spécifier plusieurs types, tels que les listes déroulantes de fractionnement, combos, etc.  
  
- Ne valident pas les GUID.  
  
- Chaque élément d’interface utilisateur a une chaîne qui représente le texte qui s’affiche avec lui.  
  
- Parent est facultatif. Si omis, la valeur « Groupe inconnu » est utilisée.  
  
- L’argument de l’icône est facultatif.  
  
- La section bitmap--identique à un .ctc de fichiers, à ceci près que vous pouvez désormais spécifier un nom de fichier par le biais de href qui est extraites par le compilateur vsct.exe au moment de la compilation.  
  
- ResID--l’ID de ressource bitmap ancien peut être utilisé et fonctionne toujours comme dans les fichiers .ctc.  
  
- HRef--une nouvelle méthode qui vous permet de spécifier un nom de fichier pour la ressource bitmap. Il suppose que toutes sont utilisées, donc vous pouvez omettre la section utilisée. Le compilateur recherche d’abord les ressources locales pour le fichier, puis sur tous les partages réseau et toutes les ressources définies par le commutateur /I.  
  
- Combinaison de touches--Vous n’avez plus à spécifier un émulateur. Si vous ne spécifiez pas un, le compilateur suppose que l’éditeur et l’émulateur sont les mêmes.  
  
- Keychord--a été supprimé. Le nouveau format est Mod1, Key1, Key2, le Mod2.  Vous pouvez spécifier un caractère, hexadécimal ou constante VK.  
  
  Le nouveau compilateur, vsct.exe, compile les fichiers .ctc et .vsct. L’ancien compilateur ctc.exe, toutefois, sera reconnaître ni compiler des fichiers .vsct.  
  
  Vous pouvez utiliser le compilateur vsct.exe pour convertir un fichier .cto existant dans un fichier .vsct. Pour plus d’informations, consultez [Comment : créer un. Fichier VSCT d’un existant. Fichier de directeur technique](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Les éléments du fichier .vsct  
 La table de commande présente la hiérarchie et les éléments suivants :  
  
 [CommandTable Élément](../../extensibility/commandtable-element.md) — représente toutes les commandes, les groupes de menus et les menus associés le VSPackage.  
  
 [Élément extern](../../extensibility/extern-element.md) : fait référence à tous les fichiers .h externe que vous voulez fusionner avec le fichier .vsct.  
  
 [Élément include](../../extensibility/include-element.md) : fait référence à tous les fichiers supplémentaires en-tête (.h) pour effectuer une compilation en même temps que le fichier de your.vsct. Un fichier .vsct peut inclure les fichiers .h contenant des constantes qui définissent des commandes, les groupes de menus et les menus qui fournit de l’IDE ou un autre package Visual Studio.  
  
 [Commandes élément](../../extensibility/commands-element.md) — représente toutes les commandes individuelles qui peuvent être exécutés. Chaque commande possède les quatre éléments enfants suivants :  
  
 [Élément menus](../../extensibility/menus-element.md) — représente tous les menus et barres d’outils dans le VSPackage. Les menus sont des conteneurs de groupes de commandes.  
  
 [Élément groupes](../../extensibility/groups-element.md) — représente tous les groupes dans le VSPackage. Les groupes sont des ensembles de commandes individuelles.  
  
 [Boutons d’élément](../../extensibility/buttons-element.md) — représente tous les boutons de commande et les éléments de menu dans le VSPackage. Boutons sont des contrôles visuels qui peuvent être associés à des commandes.  
  
 [bitmaps Élément](../../extensibility/bitmaps-element.md) — représente tous les bitmaps pour tous les boutons dans le VSPackage. Les images bitmap sont des images apparaissant à côté ou sur les boutons de commande, en fonction du contexte.  
  
 [CommandPlacements Élément](../../extensibility/commandplacements-element.md) — indique les emplacements supplémentaires où chaque commande doit être placé dans les menus de votre VSPackage.  
  
 [VisibilityConstraints Élément](../../extensibility/visibilityconstraints-element.md) — spécifie ou non une commande affiche tout temps, ou uniquement dans certains contextes, par exemple quand une boîte de dialogue particulière ou une fenêtre s’affiche. Menus et commandes qui ont une valeur pour cet élément affiche uniquement lorsque le contexte spécifié est actif. Le comportement par défaut consiste à afficher la commande à tout moment.  
  
 [KeyBindings Élément](../../extensibility/keybindings-element.md) — indique les combinaisons de touches pour les commandes. Autrement dit, un ou plusieurs combinaisons de touches qui doivent être activées pour exécuter la commande, telles que **CTRL + S**.  
  
 [UsedCommands Élément](../../extensibility/usedcommands-element.md) — Informs le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement que bien que la commande spécifiée est implémentée par un autre code, lorsque le VSPackage actuel est actif, il fournit l’implémentation de la commande.  
  
 `Symbols Element` : Contient les noms de symboles et les ID de GUID pour toutes vos commandes dans le package.  
  
## <a name="vsct-file-design-guidelines"></a>. Instructions de conception de fichier VSCT  
 Pour concevoir un fichier .vsct, suivez ces instructions.  
  
-   Commandes peuvent être placés uniquement dans les groupes, groupes peuvent être placés uniquement dans les menus et menus peuvent être placés uniquement dans les groupes. Uniquement les menus sont réellement affichées dans l’IDE, les groupes et les commandes ne sont pas.  
  
-   Sous-menus ne peut pas être directement attribués à un menu, mais doivent être attribués à un groupe, qui est assigné à son tour à un menu.  
  
-   Commandes, sous-menus et groupes peuvent être affectés à un groupe de parentage ou menu à l’aide du champ parent de leur définition directive.  
  
-   Organisation d’une table de commande uniquement via les champs dans les directives parent a une limitation importante. Les directives qui définissent des objets peuvent prendre l’argument qu’un seul parent.  
  
-   Réutilisation des commandes, des groupes ou des sous-menus requiert l’utilisation d’une directive de nouveau pour créer une nouvelle instance de l’objet avec son propre `GUID:ID` paire.  
  
-   Chaque `GUID:ID` paire doit être unique. Réutilisation d’une commande, par exemple, placée dans un menu, une barre d’outils, ou dans un menu contextuel, est gérée par le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
-   Commandes et sous-menus peuvent également être affectés à plusieurs groupes et les groupes peuvent être affectés à plusieurs menus en utilisant la [élément Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notes du fichier VSCT  
 Si vous apportez des modifications à un fichier .vsct après avoir compilez-le et placez-le dans une DLL satellite native, vous devez exécuter **devenv.exe /setup /nosetupvstemplates**. Cette opération force les ressources de VSPackage spécifiées dans le Registre expérimental d’être relus et de la base de données interne qui décrit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à reconstruire.  
  
 Pendant le développement, il est possible pour plusieurs projets de VSPackage peuvent être créés et enregistrés dans la ruche expérimentale du Registre pouvant conduire à un encombrement à confusion dans l’IDE. Pour résoudre ce problème, vous pouvez réinitialiser la ruche expérimentale pour supprimer toutes les modifications qu’ils peuvent avoir apportées à l’IDE et des VSPackages enregistrés tous les paramètres par défaut. Pour réinitialiser la ruche expérimentale, utilisez l’outil CreateExpInstance.exe fourni avec le SDK Visual Studio. Vous trouverez à l’adresse  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Exécutez l’outil à l’aide de la ligne de commande **CreateExpInstance /Reset**. N’oubliez pas que cet outil supprime la ruche expérimentale tous des VSPackages enregistrés normalement pas installés avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md)

