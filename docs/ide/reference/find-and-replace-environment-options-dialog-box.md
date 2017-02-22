---
title: "Rechercher et remplacer, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.FindReplace"
  - "VS.ToolsOptionsPages.Environment.FindandReplace"
helpviewer_keywords: 
  - "Rechercher et remplacer, boîte de dialogue Options"
  - "Rechercher et remplacer, personnalisation"
ms.assetid: f804d6d5-6309-46e4-8294-b83e880b5ec9
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Rechercher et remplacer, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez cette page de la boîte de dialogue **Options** pour contrôler des boîtes de message et d'autres aspects d'une opération de recherche et remplacement.  Vous pouvez accéder à cette boîte de dialogue à partir du menu **Outils** en cliquant sur **Options**, en développant **Environnement**, puis en cliquant sur **Rechercher et remplacer**.  Si cette page n'apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Liste UIElement  
 **Afficher des messages d'information**  
 Sélectionnez cette option pour afficher tous les messages d'information Rechercher et remplacer qui ont l'option **Toujours afficher ce message**.  Par exemple, si vous avez choisi de ne pas afficher le message « Le début de la recherche est atteint. », la sélection de cette option entraînerait l'affichage de ce message d'information lors de la prochaine utilisation de la fonction Rechercher et remplacer.  
  
 Si vous ne souhaitez pas voir de messages d'information pour la fonction Rechercher et remplacer, désactivez cette option.  
  
 Lorsque vous avez désactivé l'option **Toujours afficher ce message** pour certains, mais pas tous les messages d'information de **Rechercher et remplacer**, la case à cocher **Afficher des messages d'information** semble activée, mais pas sélectionnée.  Pour restaurer tous les messages **Rechercher et remplacer** facultatifs, désactivez cette option puis sélectionnez\-la à nouveau.  
  
> [!NOTE]
>  Cette option n'affecte aucun message d'information pour la fonction **Rechercher et remplacer** qui n'affichent pas l'option **Toujours afficher ce message**.  
  
 **Afficher des messages d'avertissement**  
 Sélectionnez cette option pour afficher tous les messages d'avertissement pour la fonction Rechercher et remplacer qui ont l'option **Toujours afficher ce message**.  Par exemple, si vous avez choisi de ne pas afficher le message d'avertissement **Remplacer tout** qui apparaît lorsque vous essayez de procéder à des remplacements dans des fichiers qui ne sont pas actuellement ouverts pour être modifiés, la sélection de cette option entraînerait la réapparition du message d'avertissement si vous essayez de Remplacer tout.  
  
 Si vous ne souhaitez pas voir de messages d'avertissement pour la fonction Rechercher et remplacer, désactivez cette option.  
  
 Lorsque vous avez désactivé l'option **Toujours afficher ce message** pour certains, mais pas tous les messages d'avertissement de **Rechercher et remplacer**, la case à cocher **Afficher des messages d'avertissement** semble activée, mais pas sélectionnée.  Pour restaurer tous les messages **Rechercher et remplacer** facultatifs, désactivez cette option puis sélectionnez\-la à nouveau.  
  
> [!NOTE]
>  Cette option n'affecte aucun message d'avertissement pour la fonction **Rechercher et remplacer** qui n'affichent pas l'option **Toujours afficher ce message**.  
  
 **Remplir automatiquement la zone Rechercher à l'aide du texte de l'éditeur**  
 Sélectionnez cette option pour coller le texte de chaque côté du point d'insertion actuel de l'éditeur de la  **Rechercher** de champ lorsque vous sélectionnez un affichage de la  **Rechercher et remplacer** fenêtre à partir de la  **Modifier** menu.  Désactivez cette option pour utiliser le dernier modèle de recherche de la recherche précédente comme chaîne **Rechercher**.  
  
## Voir aussi  
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)