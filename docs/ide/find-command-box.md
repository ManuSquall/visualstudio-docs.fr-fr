---
title: Zone Rechercher/Commande
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591526"
---
# <a name="findcommand-box"></a>zone Rechercher/Commande

Vous pouvez rechercher des commandes Visual Studio de texte et d’exécution à partir de la zone **Rechercher/Commande**. La zone **Rechercher/Commande** reste disponible en tant que contrôle de barre d’outils, mais n’est plus visible par défaut. Vous pouvez afficher la zone **Rechercher/Commande** en choisissant **Ajouter ou supprimer des boutons** dans la barre d’outils **Standard**, puis en choisissant **Rechercher**.

Pour exécuter une [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] commande, faites-la précéder d’un signe supérieur à ( **>** ).

La zone **Rechercher/Commande** conserve les 20 derniers éléments entrés et les affiche dans une liste déroulante. Vous pouvez parcourir la liste à l’aide des **touches fléchées**.

![Zone Rechercher&#47;Commande](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Recherche de texte

Par défaut, lorsque vous spécifiez du texte dans la zone **Rechercher/commande** , puis que vous appuyez sur la touche **entrée** , Visual Studio recherche dans la fenêtre du document ou de l’outil en cours à l’aide des options spécifiées dans la boîte de dialogue **Rechercher dans les fichiers** . Pour plus d’informations, consultez [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Entrée de commandes

Si vous voulez utiliser la zone **Rechercher/Commande** pour envoyer un alias ou une commande [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unique au lieu de rechercher du texte, faites précéder la commande du signe « supérieur à » (**>**). Par exemple :

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Vous avez également la possibilité d’utiliser la fenêtre **Commande** pour entrer et exécuter une ou plusieurs commandes. Certaines commandes ou certains alias peuvent être entrés et exécutés sans aucun argument, alors que d’autres ont des arguments obligatoires dans leur syntaxe. Pour obtenir la liste des commandes qui ont des arguments, consultez [Commandes Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Caractères d'échappement

Un **^** caractère d’insertion () dans une commande signifie que le caractère qui le suit immédiatement est interprété littéralement, et non comme un caractère de contrôle. Ceci permet d’incorporer des guillemets (**"**), des espaces, des barres obliques, des accents circonflexes ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur, à l’exception des noms de commutateur. Par exemple :

```
>Edit.Find ^^t /regex
```

Un accent circonflexe fonctionne de la même façon, qu’il soit à l’intérieur ou en dehors des guillemets. Si un accent circonflexe est le dernier caractère de la ligne, il est ignoré.

## <a name="see-also"></a>Voir aussi

- [Fenêtre Commande](../ide/reference/command-window.md)
- [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)
