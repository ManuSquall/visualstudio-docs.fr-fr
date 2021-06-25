---
title: GUID et ID des commandes Visual Studio | Microsoft Docs
description: Découvrez comment localiser les valeurs GUID et ID des commandes incluses dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8442e6430ead8f28d2afc7f51d14968b6999fcd9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898277"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID et ID des commandes Visual Studio
Les valeurs GUID et ID des commandes incluses dans l’environnement de développement intégré (IDE) de Visual Studio sont définies dans les fichiers. vsct installés dans le cadre du kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Pour plus d’informations sur l’utilisation des objets IDE définis dans des fichiers *. vsct* , consultez [étendre des menus et des commandes](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Rechercher une définition de commande
 Étant donné que Visual Studio définit plus de 1000 commandes, il est difficile de les répertorier ici. Au lieu de cela, procédez comme suit pour rechercher la définition d’une commande.

### <a name="to-locate-a-command-definition"></a>Pour rechercher une définition de commande

1. Dans Visual Studio, ouvrez les fichiers suivants dans le *chemin d’installation du kit de développement logiciel (SDK) de Visual studio<dossier \> \VisualStudioIntegration\Common\Inc \\* : *SharedCmdDef. vsct*, *ShellCmdDef. vsct*, *VsDbgCmdUsed. vsct*, *Venusmenu. vsct*.

    La plupart des commandes Visual Studio sont définies dans *SharedCmdDef. vsct* et *ShellCmdDef. vsct*. *VsDbgCmdUsed. vsct* définit les commandes relatives au débogueur, et *Venusmenu. vsct* définit les commandes qui sont spécifiques au développement Web.

2. Si la commande est un élément de menu, notez le texte exact de l’élément de menu. Si la commande est un bouton dans une barre d’outils, notez le texte d’info-bulle qui s’affiche lorsque vous placez le bouton de la flèche dessus.

3. Appuyez sur **CTRL** + **F** pour ouvrir la boîte de dialogue **Rechercher** .

4. Dans la zone **Rechercher** , tapez le texte que vous avez noté à l’étape 2.

5. Vérifiez que **tous les documents ouverts** sont affichés dans la zone **regarder dans** .

6. Cliquez sur le bouton **suivant** jusqu’à ce que le texte soit sélectionné dans la `<Strings>` section d’un [élément bouton](../../extensibility/button-element.md).

    L' `<Button>` élément dans lequel la commande apparaît est la définition de la commande.

   Une fois que vous avez trouvé la définition de la commande, vous pouvez placer une copie de la commande sur un autre menu ou une autre barre d’outils en créant un [élément commandplacement ayant](../../extensibility/commandplacement-element.md) ayant les mêmes `guid` `id` valeurs et que la commande. Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Cas particuliers
 Dans les cas suivants, le texte du menu ou le texte de l’info-bulle peut ne pas correspondre exactement à ce qui se trouve dans la définition de la commande.

- Les éléments de menu qui incluent un caractère souligné, tels que la commande **Imprimer** du menu **fichier** , dans lequel le *P* est souligné.

     Les caractères précédés du caractère esperluette (&) dans les noms des éléments de menu sont affichés sous forme de soulignement. Toutefois, les fichiers *. vsct* sont écrits au format XML, qui utilise le caractère perluète (&) pour indiquer les caractères spéciaux et requiert l’utilisation d’une esperluette pour l' *&amp; affichage.* Par conséquent, dans un fichier *. vsct* , la commande **Imprimer** apparaît en tant que *&amp; amp ; Imprimer*.

- Commandes qui ont du texte dynamique, telles que **Save** \<Current Filename\> , et des éléments de menu générés dynamiquement, tels que les éléments de la liste des **fichiers récents** .

     Il n’existe pas de méthode fiable pour rechercher du texte dynamique. Recherchez plutôt un groupe qui héberge la commande souhaitée en consultant les [GUID et les ID des menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou GUIDs Visual Studio, [ainsi que les ID des barres d’outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), et recherchez l’ID de ce groupe. Si la définition de la commande n’a pas le groupe en tant qu' [élément parent](../../extensibility/parent-element.md), recherchez *SharedCmdPlace. vsct* et *ShellCmdPlace. vsct* (ou *VsDbgCmdPlace. vsct* pour les commandes du débogueur) pour un `<CommandPlacement>` élément qui définit le parent de la commande. *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct* et *VsDbgCmdPlace. vsct* se trouvent dans le dossier *\<Visual Studio SDK installation path\> \VisualStudioIntegration\Common\Inc \\* .

## <a name="see-also"></a>Voir aussi

- [Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
