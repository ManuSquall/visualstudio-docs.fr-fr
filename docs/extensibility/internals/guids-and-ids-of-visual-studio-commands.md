---
title: "GUID et ID de commandes de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes"
  - "ID"
  - "emplacement de commande"
  - "commande de Visual studio"
  - "GUID"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# GUID et ID de commandes de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

GUID et les valeurs d'ID des commandes incluses dans l'IDE de Visual Studio \(IDE\) sont définis dans des fichiers de .vsct installés dans le cadre de le kit de développement Visual Studio.  Pour plus d'informations, consultez [Groupes, les Menus et les commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Pour plus d'informations sur l'utilisation des objets de l'IDE définis dans les fichiers de .vsct, consultez [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
## rechercher une définition de commande  
 Étant donné que Visual Studio définit plus " pour mille " commandes, il est impossible de les répertorier toutes ici.  Au lieu de cela, procédez comme suit pour localiser la définition d'une commande.  
  
#### Pour rechercher la définition de commande  
  
1.  dans Visual Studio, ouvrez les fichiers suivants dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration\\Common\\Inc\\ folder: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu .vsct.  
  
     la plupart des commandes de Visual Studio sont définies dans SharedCmdDef.vsct et ShellCmdDef.vsct.  VsDbgCmdUsed.vsct définit les commandes relatives au débogueur, et Venusmenu.vsct définit les commandes qui sont spécifiques à la programmation Web.  
  
2.  Si la commande est un élément de menu, prenez note du texte exact de l'élément de menu.  Si la commande est un bouton sur une barre d'outils, prenez note du texte d'info\-bulle qui s'affiche lorsque vous pointez la souris dessus.  
  
3.  Appuyez sur la combinaison de touches CTRL\+F pour ouvrir la boîte de dialogue de **Rechercher** .  
  
4.  Dans la zone de **Rechercher** , tapez le texte que vous avez indiquée dans l'étape 2.  
  
5.  Vérifiez que **tous les documents ouverts** s'affiche dans la zone de **Regarder dans** .  
  
6.  cliquez sur le bouton de **Suivant** jusqu'à ce que le texte soit sélectionné dans la section d' `<Strings>` de [Élément de bouton](../../extensibility/button-element.md).  
  
     L'élément d' `<Button>` qui la commande apparaît dans est la définition de commande.  
  
 Lorsque vous avez trouvé la définition de commande, vous pouvez ajouter une copie de la commande dans un menu ou une barre d'outils différent en créant [Élément de CommandPlacement](../../extensibility/commandplacement-element.md) qui a mêmes `guid` et valeurs d' `id` que la commande.  Pour plus d'informations, consultez [Création de groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### Cas spéciaux  
 Dans les cas suivants, le texte de menu ou le texte d'info\-bulle ne corresponde pas exactement à celui de la définition de commande.  
  
-   Éléments de menu qui incluent un caractère souligné, telles que l'ordre d' **Imprimer** dans le menu de **Fichier** , dans lequel P est souligné.  
  
     Les caractères qui sont précédés par '&'le caractères dans les noms d'éléments de menu sont affichés comme souligné.  Toutefois, les fichiers de .vsct sont écrits en XML, qui utilise «&le caractère pour indiquer des caractères spéciaux et le requiert qu'un perluète qui doit être affiché doit être défini comme »&amp;».  Par conséquent, dans un fichier de .vsct, la commande d'impression apparaît comme '&amp;Print'.  
  
-   Commandes qui ont le texte dynamique, tel qu' **Enregistrer** *Nom du fichier en cours*, et les éléments de menu générés dynamiquement, tels que les éléments de la liste de **fichiers récents** .  
  
     Il n'existe aucune façon fiable pour la rechercher sur le texte dynamique.  Au lieu de cela, recherchez un groupe qui héberge la commande de mise à jour [GUID et ID de Menus de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) de recherche ou [GUID et ID des barres d'outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), et la recherche sur l'ID de ce groupe.  Si la définition de commande n'a pas le groupe comme [Parent, élément](../../extensibility/parent-element.md), la recherche SharedCmdPlace.vsct et ShellCmdPlace.vsct \(ou VsDbgCmdPlace.vsct pour les commandes du débogueur\) d'un élément de `<CommandPlacement>` qui définit le parent de la commande.  SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct sont dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration\\Common\\Inc \\.  
  
## Voir aussi  
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence de schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)