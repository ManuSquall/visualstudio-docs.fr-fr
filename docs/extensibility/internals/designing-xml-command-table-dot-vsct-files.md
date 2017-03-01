---
title: Conception de Table de commande XML (. Les fichiers VSCT) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>Conception de Table de commande XML (. Fichiers VSCT)
Un fichier de table (.vsct) de commande XML décrit la disposition et l’apparence des éléments de commande pour un VSPackage. Éléments de commande incluent des boutons, zones de liste déroulante, menus, barres d’outils et groupes d’éléments de commande. Cette rubrique décrit les fichiers de la table commandes XML, comment elles affectent les menus et éléments de commande et comment les créer.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Le fichier .vsct, les Menus, les groupes et commandes  
 fichiers .vsct sont organisés autour des commandes, des menus et des groupes de commandes. Les balises XML dans le fichier .vsct représentent chacun de ces éléments, ainsi que d’autres éléments associés tels que des boutons de commande, le placement de la commande et les bitmaps.  
  
 Lorsque vous créez un nouveau VSPackage en exécutant la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de Package, le modèle génère un fichier .vsct les éléments nécessaires pour une commande de menu, une fenêtre outil ou un éditeur personnalisé, en fonction de vos sélections. Ce fichier .vsct puis modifiables pour répondre aux exigences d’un VSPackage spécifique. Pour obtenir des exemples de modification d’un fichier .vsct, consultez les exemples dans [extension des Menus et des commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Pour créer un fichier .vsct vierge, consultez [Comment : créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Une fois créé, vous ajouter éléments, attributs et valeurs XML pour le fichier afin de décrire la disposition d’éléments de commande. Pour un schéma XML détaillé, consultez la [VSCT référence de schéma XML](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Différences entre les fichiers .ctc et .vsct  
 Si la signification des balises XML dans un fichier .vsct est les mêmes que celles figurant dans le présent déconseillée le format de fichier .ctc, leur implémentation est légèrement différente.  
  
-   La nouvelle ** \<extern >** balise est où vous référencez autres fichiers .h compilé, telles que celles de le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barre d’outils.  
  
-   Alors que la prise en charge des fichiers .vsct les **/ include** instruction, comme les fichiers .ctc, il comporte également un nouveau \< **importer >** élément. La différence est, **/ include** réunit **tous les** des informations, mais \< **importer >** apporte uniquement les noms.  
  
-   Tandis que les fichiers .ctc nécessitent un fichier d’en-tête dans lequel vous définissez les directives de préprocesseur, un n’est pas obligatoire pour les fichiers .vsct. Au lieu de cela, placez vos directives dans la table de symboles, située dans le ** \<symbole >** éléments, situés en bas du fichier .vsct.  
  
-   fonctionnalité de fichiers .vsct un ** \<Annotation >** balise, qui vous permet d’incorporer les informations de votre choix, tel que les notes ou même d’images.  
  
-   Les valeurs sont stockées en tant qu’attributs sur l’élément.  
  
-   Les indicateurs de commande peuvent être stockées individuellement ou empilés.  Toutefois, IntelliSense ne fonctionne pas sur les indicateurs de commande empilées. Pour plus d’informations sur les indicateurs de commande, consultez le [élément indicateur de commande](../../extensibility/command-flag-element.md).  
  
-   Vous pouvez spécifier plusieurs types, tels que les listes déroulantes de fractionnement, combinés, etc..  
  
-   GUID ne valide pas.  
  
-   Chaque élément d’interface utilisateur a une chaîne qui représente le texte affiché avec lui.  
  
-   Parent est facultatif. Si omis, la valeur « Groupe inconnu » est utilisée.  
  
-   L’icône est facultatif.  
  
-   La section bitmap--identique à un .ctc, sauf que vous pouvez désormais spécifier un nom de fichier via href qui est extraites par le compilateur vsct.exe au moment de la compilation du fichier.  
  
-   ResID--l’ID de ressource bitmap ancien peut être utilisé et le même fonctionne toujours comme dans les fichiers .ctc.  
  
-   HRef--une nouvelle méthode qui permet de spécifier un nom de fichier pour la ressource bitmap. Il part du principe que tous sont utilisés, donc vous pouvez omettre la section utilisée. Le compilateur recherche d’abord les ressources locales pour le fichier, puis sur tous les partages réseau et les ressources définies par le commutateur /I.  
  
-   KeyBinding : Vous n’avez plus à spécifier un émulateur. Si vous ne spécifiez pas un, le compilateur suppose que l’éditeur et l’émulateur sont identiques.  
  
-   Keychord--a été supprimé. Le nouveau format est Key1, Mod1, Key2, Mod2.  Vous pouvez spécifier un caractère, hexadécimal ou constante VK.  
  
 Le nouveau compilateur, vsct.exe, compile les fichiers .ctc et .vsct. L’ancien compilateur ctc.exe, toutefois, est reconnaît ni compiler les fichiers .vsct.  
  
 Vous pouvez utiliser le compilateur vsct.exe pour convertir un fichier .cto existant dans un fichier .vsct. Pour plus d’informations, consultez [Comment : créer un. Fichier VSCT d’un existant. Fichier de directeur technique](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Les éléments du fichier .vsct  
 Le tableau de commande présente la hiérarchie et les éléments suivants :  
  
 [Élément de CommandTable](../../extensibility/commandtable-element.md) , représente toutes les commandes, les groupes de menus et les menus associés le VSPackage.  
  
 [Extern élément](../../extensibility/extern-element.md) : fait référence à tous les fichiers .h externe que vous souhaitez fusionner avec le fichier .vsct.  
  
 [Élément include](../../extensibility/include-element.md) : fait référence à tous les fichiers d’en-tête supplémentaires (.h) à compiler avec your.vsct fichier. Un fichier .vsct peut inclure les fichiers .h qui contient les constantes qui définissent les commandes, les groupes de menus et les menus qui fournit l’IDE ou un autre VSPackage.  
  
 [Commandes d’élément](../../extensibility/commands-element.md) , représente toutes les commandes individuelles qui peuvent être exécutés. Chaque commande possède les éléments quatre enfants suivants :  
  
 [Élément de menus](../../extensibility/menus-element.md) — représente tous les menus et les barres d’outils dans le VSPackage. Menus sont des conteneurs de groupes de commandes.  
  
 [Élément groupes](../../extensibility/groups-element.md) — représente tous les groupes dans le VSPackage. Les groupes sont des ensembles de commandes individuelles.  
  
 [Boutons d’élément](../../extensibility/buttons-element.md) — représente tous les boutons de commande et les éléments de menu dans le VSPackage. Boutons sont des contrôles visuels qui peuvent être associés à des commandes.  
  
 [Élément de bitmaps](../../extensibility/bitmaps-element.md) : représente l’ensemble des bitmaps pour tous les boutons dans le VSPackage. Les images bitmap sont des images affichées à côté ou sur les boutons de commande, en fonction du contexte.  
  
 [Élément de CommandPlacements](../../extensibility/commandplacements-element.md) — indique les emplacements supplémentaires où chaque commande doit être placé dans les menus de votre VSPackage.  
  
 [Élément de VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) — spécifie ou non une commande affiche tout fois ou uniquement dans certains contextes, tels que lorsqu’une fenêtre ou boîte de dialogue particulière s’affiche. Menus et les commandes qui ont une valeur de cet élément seront affichent uniquement lorsque le contexte spécifié est actif. Le comportement par défaut consiste à afficher la commande à tout moment.  
  
 [Élément de thèmes](../../extensibility/keybindings-element.md) — spécifie les combinaisons de touches pour les commandes. Autrement dit, une ou plusieurs combinaisons de touches qui doivent être utilisées pour exécuter la commande, telle que **CTRL + S**.  
  
 [Élément de UsedCommands](../../extensibility/usedcommands-element.md) — Informs le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement que bien que la commande spécifiée est implémentée par un autre code, lorsque le VSPackage actuels est actif, il fournit l’implémentation de la commande.  
  
 `Symbols Element`: Contient les noms de symboles et les ID de GUID pour toutes les commandes dans le package.  
  
## <a name="vsct-file-design-guidelines"></a>. Instructions de conception de fichier VSCT  
 Pour concevoir un fichier .vsct, suivez ces instructions.  
  
-   Commandes peuvent être placés dans les groupes, les groupes peuvent être placés dans les menus et menus peuvent être placés dans des groupes. Uniquement les menus sont affichent en fait dans l’IDE, les groupes et les commandes ne sont pas.  
  
-   Sous-menus ne peut pas être directement affectés à un menu, mais doivent être affectés à un groupe, qui est ensuite attribué à un menu.  
  
-   Commandes, des sous-menus et des groupes peuvent affectés à un groupe de parenté ou un menu à l’aide du champ parent de leur définition directive.  
  
-   Organisation d’une table de commandes uniquement via les champs parent dans les directives a un frein important. Les directives qui définissent les objets peuvent prendre l’argument qu’un seul parent.  
  
-   Réutilisation des commandes, des groupes ou des sous-menus requiert l’utilisation d’une nouvelle directive pour créer une nouvelle instance de l’objet avec son propre `GUID:ID` paire.  
  
-   Chaque `GUID:ID` paire doit être unique. Réutilisation d’une commande, par exemple, placée dans un menu, une barre d’outils, ou dans un menu contextuel, est gérée par le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   Commandes et les sous-menus peuvent également être affectés à plusieurs groupes et les groupes peuvent être affectés à plusieurs menus à l’aide de la [élément Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notes du fichier VSCT  
 Si vous apportez des modifications dans un fichier .vsct une fois que vous le compiler et placez dans une DLL satellite native, vous devez exécuter **devenv.exe /setup /nosetupvstemplates**. Cette opération force les ressources VSPackage spécifiés dans le Registre d’être relus expérimental et la base de données interne qui décrit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à reconstruire.  
  
 Pendant le développement, il est possible pour plusieurs projets VSPackage doit être créé et enregistré dans la ruche expérimentale risque de confusion l’encombrement dans l’IDE. Pour résoudre ce problème, vous pouvez réinitialiser la ruche expérimentale sur les paramètres par défaut pour supprimer les VSPackages enregistrer et toutes les modifications qu'ont apportées à l’IDE. Pour réinitialiser la ruche expérimentale, utilisez l’outil CreateExpInstance.exe fourni avec le Kit de développement Visual Studio. Vous trouverez à l’adresse  
  
 **% PROGRAMFILES (x&86;) %\Visual Studio \<version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Exécutez l’outil à l’aide de la ligne de commande **CreateExpInstance /MMC**. N’oubliez pas que cet outil supprime la ruche expérimentale tous les packages enregistrés VS ne sont pas normalement installés avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md)
