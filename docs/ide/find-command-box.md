---
title: "Zone Rechercher/Commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "zone Rechercher/Commande"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Zone Rechercher/Commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rechercher des commandes Visual Studio de texte et de passage de la zone **Rechercher\/Commande**.  La zone **Rechercher\/Commande** reste disponible comme contrôle ToolBar, mais n'est plus visible par défaut.  Vous pouvez afficher la zone **Rechercher\/Commande** en sélectionnant **Ajouter\/supprimer des boutons** dans la barre d'outils **Standard** puis **Rechercher**.  
  
 Pour exécuter une commande d'[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], préfacez\- la avec un supérieur à \(\>\) le signe.  
  
 La zone **Rechercher\/Commande** mémorise les 20 derniers éléments entrés, qu'elle affiche dans une liste déroulante.  Vous pouvez parcourir la liste en choisissant les touches de direction.  
  
 ![Zone Rechercher&#47;Commande](~/docs/ide/media/findcommandbox.png "FindCommandBox")  
Zone Rechercher\/Commande  
  
## Rechercher du texte  
 Par défaut, lorsque vous spécifiez le texte dans la zone **Rechercher\/Commande** puis choisissez la touche ENTRÉE, Visual Studio recherche le document actif ou la fenêtre Outil à l'aide des options spécifiées dans la boîte de dialogue **Rechercher dans les fichiers**.  Pour plus d'informations, consultez [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md).  
  
## Entrée de commandes  
 Pour utiliser la zone **Rechercher\/Commande** pour publier une commande unique de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou alias plutôt que rechercher du texte, sélectionnez la commande de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], préfacée avec un supérieur à \(\>\) le symbole.  Par exemple :  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Ou bien, vous pouvez utiliser la fenêtre Commande pour entrer et exécuter une ou plusieurs commandes.  Certaines commandes ou certains alias peuvent être entrés et exécutés sans aucun argument, alors que d'autres nécessitent des arguments précis dans leur syntaxe.  Pour obtenir la liste des commandes qui possèdent des arguments, consultez [Commandes Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## Caractères d'échappement  
 La présence d'un signe d'insertion \(^\) dans une ligne de commande signifie que le caractère situé juste après ce signe est interprété littéralement, et non comme un caractère de contrôle.  Cela permet d'incorporer des guillemets \("\), des espaces, des barres obliques de début, des signes d'insertion ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur \(mais pas dans les noms de commutateurs\).  Par exemple :  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Un signe d'insertion a la même fonction qu'il soit ou non placé entre guillemets.  Si le signe d'insertion est le dernier caractère de la ligne de commande, il est ignoré.  
  
## Voir aussi  
 [Commande, fenêtre](../ide/reference/command-window.md)   
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)