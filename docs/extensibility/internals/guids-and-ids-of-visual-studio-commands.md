---
title: GUID et ID des commandes de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35e2c354293679d9cb6044b0c5f21b77aadb7f52
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220158"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Commandes de GUID et ID de Visual Studio
Les valeurs GUID et l’ID de commandes incluses dans l’environnement de développement intégré (IDE) Visual Studio sont définies dans les fichiers .vsct qui sont installés dans le cadre du SDK Visual Studio. Pour plus d’informations, consultez [commandes définies par l’IDE, les menus et les groupes](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Pour plus d’informations sur l’utilisation des objets d’IDE qui sont définis dans *.vsct* de fichiers, consultez [étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="find-a-command-definition"></a>Rechercher une définition de commande  
 Étant donné que Visual Studio définit des commandes de plus de 1000, il n’est pas pratique de tous les répertorier ici. Au lieu de cela, suivez ces étapes pour rechercher la définition d’une commande.  
  
### <a name="to-locate-a-command-definition"></a>Pour localiser une définition de commande  
  
1. Dans Visual Studio, ouvrez les fichiers suivants dans le *< chemin d’installation de Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\*  dossier : *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.  
  
    La plupart des commandes de Visual Studio sont définies dans *SharedCmdDef.vsct* et *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* définit des commandes qui se rapportent au débogueur, et *Venusmenu.vsct* définit des commandes qui sont spécifiques au développement Web.  
  
2. Si la commande est un élément de menu, notez le texte exact de l’élément de menu. Si la commande est un bouton sur une barre d’outils, notez le texte d’info-bulle qui apparaît lorsque vous pointez sur elle.  
  
3. Appuyez sur **Ctrl**+**F** pour ouvrir le **trouver** boîte de dialogue.  
  
4. Dans le **rechercher** , tapez le texte que vous avez noté à l’étape 2.  
  
5. Vérifiez que **tous les Documents ouverts** s’affiche dans le **Regarder dans** boîte.  
  
6. Cliquez sur le **suivant** jusqu'à ce que le texte est sélectionné dans le `<Strings>` section d’un [élément Button](../../extensibility/button-element.md).  
  
    Le `<Button>` élément apparaissant dans la commande est la définition de commande.  
  
   Lorsque vous avez trouvé la définition de commande, vous pouvez placer une copie de la commande sur un autre menu ou une barre d’outils, en créant un [élément CommandPlacement](../../extensibility/commandplacement-element.md) qui a le même `guid` et `id` valeurs en tant que la commande. Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Cas particuliers  
 Dans les cas suivants, le texte de menu ou le texte d’info-bulle peut pas correspondre exactement à ce qui figure dans la définition de commande.  
  
-   Les éléments de menu qui incluent un caractère souligné, telles que la **impression** commande sur le **fichier** menu, dans lequel le *P* est souligné.  
  
     Les caractères qui sont précédés de l’esperluette (&) caractères dans les noms d’élément de menu sont affichées comme souligné. Toutefois, *.vsct* fichiers sont écrits en XML, qui utilise le caractère esperluette (&) pour indiquer les caractères spéciaux et nécessite qu’une esperluette à afficher doit être développée en tant que  *&amp;amp ;*. Par conséquent, dans un *.vsct* fichier, le **impression** commande apparaît sous la forme  *&amp;amp ; Impression*.  
  
-   Les commandes qui ont un texte dynamique, tel que **enregistrer** \<nom de fichier actuel\>et généré dynamiquement des éléments de menu, tels que des éléments sur le **fichiers récents** liste.  
  
     Il n’existe aucun moyen fiable pour effectuer une recherche sur texte dynamique. Au lieu de cela, rechercher un groupe qui héberge la commande souhaitée en consultant [menus GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [barres d’outils de GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)et la recherche de l’ID de ce groupe. Si la définition de la commande n’a pas le groupe que sa [élément Parent](../../extensibility/parent-element.md), recherche *SharedCmdPlace.vsct* et *ShellCmdPlace.vsct* (ou  *VsDbgCmdPlace.vsct* pour les commandes de débogueur) pour un `<CommandPlacement>` élément qui définit le parent de la commande. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, et *VsDbgCmdPlace.vsct* se trouvent dans le *\<chemin d’installation de Visual Studio SDK\>\ VisualStudioIntegration\Common\Inc\\* dossier.  
  
## <a name="see-also"></a>Voir aussi  
 [MenuCommands et OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
