---
title: GUIDs et IDs de Visual Studio Commands (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708251"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs et IDs des commandes Visual Studio
Les valeurs GUID et ID des commandes incluses dans l’environnement de développement intégré Visual Studio (IDE) sont définies dans les fichiers .vsct qui sont installés dans le cadre du Visual Studio SDK. Pour plus d’informations, consultez les [commandes, les menus et les groupes définis par l’IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Pour plus d’informations sur la façon de travailler avec des objets IDE qui sont définis dans des fichiers *.vsct,* voir [Les menus et les commandes Extend](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Trouver une définition de commande
 Parce que Visual Studio définit plus de 1000 commandes, il n’est pas pratique de les énumérer tous ici. Au lieu de cela, suivez ces étapes pour localiser la définition d’une commande.

### <a name="to-locate-a-command-definition"></a>Pour localiser une définition de commande

1. Dans Visual Studio, ouvrez les fichiers suivants dans le *<Visual Studio SDK trajectoire\>\\ d’installation 'VisualStudioIntegration’Common’Inc* dossier: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    La plupart des commandes Visual Studio sont définies dans *SharedCmdDef.vsct* et *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* définit les commandes qui se rapportent au débbugger, et *Venusmenu.vsct* définit les commandes qui sont spécifiques au développement Web.

2. Si la commande est un élément de menu, notez le texte exact de l’élément de menu. Si la commande est un bouton sur une barre d’outils, notez le texte de pointe qui apparaît lorsque vous vous arrêtez dessus.

3. Appuyez sur **Ctrl**+**F** pour ouvrir la boîte de dialogue **Find.**

4. Dans la **boîte Trouver quelle** boîte, tapez le texte que vous avez noté à l’étape 2.

5. Vérifiez que **tous les documents ouverts** sont affichés dans le Look **in** box.

6. Cliquez sur le bouton **Trouver ensuite** `<Strings>` jusqu’à ce que le texte soit sélectionné dans la section d’un [élément Bouton](../../extensibility/button-element.md).

    L’élément `<Button>` dans lequel la commande apparaît est la définition de commande.

   Lorsque vous avez trouvé la définition de commande, vous pouvez mettre une copie de la commande `guid` sur `id` un autre menu ou barre d’outils en créant un [élément CommandPlacement](../../extensibility/commandplacement-element.md) qui a les mêmes valeurs que la commande. Pour plus d’informations, voir [Créer des groupes réutilisables de boutons](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Cas particuliers
 Dans les cas suivants, le texte du menu ou le texte de l’outil peut ne pas correspondre exactement à ce qui se trouve dans la définition de commande.

- Éléments de menu qui comprennent un caractère souligné, comme la commande **d’impression** sur le menu **Fichier,** dans lequel le *P* est souligné.

     Les caractères précédés par le caractère ampersand (&) dans les noms d’éléments de menu sont affichés comme souligné. Cependant, les fichiers *.vsct* sont écrits dans XML, qui utilise le caractère ampersand (&) pour indiquer des caractères spéciaux et exige qu’un ampersand à afficher doit être précisé comme * &amp;ampli;*. Par conséquent, dans un fichier *.vsct,* la commande **d’impression** apparaît comme * &amp;ampli; Imprimer*.

- Commandes qui ont un texte **Save** \<dynamique, comme\>Enregistrer le nom de fichier actuel , et les éléments de menu générés dynamiquement, tels que les éléments de la liste **des fichiers récents.**

     Il n’existe aucun moyen fiable de rechercher sur le texte dynamique. Au lieu de cela, trouver un groupe qui héberge la commande souhaitée en consultant [GUIDs et ID de menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs et ID de barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), et la recherche sur l’ID de ce groupe. Si la définition de commande n’a pas le groupe comme [élément Parent,](../../extensibility/parent-element.md)recherche *SharedCmdPlace.vsct* et *ShellCmdPlace.vsct* (ou *VsDbgCmdPlace.vsct* pour les commandes de débbugger) pour un `<CommandPlacement>` élément qui définit le parent de la commande. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, et *VsDbgCmdPlace.vsct* sont dans le * \<chemin\>d’installation Visual Studio\\ SDK 'VisualStudioIntegration’Common’Inc* dossier.

## <a name="see-also"></a>Voir aussi

- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML référence schéma](../../extensibility/vsct-xml-schema-reference.md)
