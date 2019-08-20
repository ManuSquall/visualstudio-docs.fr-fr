---
title: Rechercher/Commande, zone | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8bddc27eb4a59b65796c7837ae4561e5d56a5d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160679"
---
# <a name="findcommand-box"></a>zone Rechercher/Commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rechercher des commandes Visual Studio de texte et d’exécution à partir de la zone **Rechercher/Commande**. La zone **Rechercher/Commande** reste disponible en tant que contrôle de barre d’outils, mais n’est plus visible par défaut. Vous pouvez afficher la zone **Rechercher/Commande** en choisissant **Ajouter ou supprimer des boutons** dans la barre d’outils **Standard**, puis en choisissant **Rechercher**.  
  
 Pour exécuter une commande [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], faites-la précéder d’un signe > (supérieur à).  
  
 La zone **Rechercher/Commande** conserve les 20 derniers éléments entrés et les affiche dans une liste déroulante. Vous pouvez parcourir la liste à l’aide des touches de direction.  
  
 ![Zone Rechercher& #47;Commande](../ide/media/findcommandbox.png "FindCommandBox")  
zone Rechercher/Commande  
  
## <a name="searching-for-text"></a>Recherche de texte  
 Par défaut, quand vous spécifiez du texte dans la zone **Rechercher/Commande**, puis que vous choisissez la touche Entrée, Visual Studio recherche dans la fenêtre de document ou Outil actuelle en utilisant les options spécifiées dans la boîte de dialogue **Rechercher dans les fichiers**. Pour plus d’informations, consultez [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Entrée de commandes  
 Si vous voulez utiliser la zone **Rechercher/Commande** pour émettre une commande ou un alias [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unique plutôt que de rechercher du texte, entrez la commande [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] précédée du signe > (supérieur à). Par exemple :  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Vous avez également la possibilité d’utiliser la fenêtre Commande pour entrer et exécuter une ou plusieurs commandes. Certaines commandes ou certains alias peuvent être entrés et exécutés sans aucun argument, alors que d’autres ont des arguments obligatoires dans leur syntaxe. Pour obtenir la liste des commandes qui ont des arguments, consultez [Commandes Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Caractères d’échappement  
 La présence d’un signe d’insertion (^) dans une ligne de commande signifie que le caractère situé juste après ce signe est interprété littéralement, et non comme un caractère de contrôle. Ceci permet d’incorporer des guillemets ("), des espaces, des barres obliques, des accents circonflexes ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur, à l’exception des noms de commutateur. Par exemple :  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Un accent circonflexe fonctionne de la même façon, qu’il soit à l’intérieur ou en dehors des guillemets. Si un accent circonflexe est le dernier caractère de la ligne, il est ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Commande](../ide/reference/command-window.md)   
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)
