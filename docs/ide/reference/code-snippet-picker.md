---
title: "S&#233;lecteur d&#39;extraits de code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.expansionpicker"
helpviewer_keywords: 
  - "Sélecteur d'extraits de code"
  - "extraits de code, Sélecteur d'extraits de code"
  - "extraits de code IntelliSense, Sélecteur d'extraits de code"
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# S&#233;lecteur d&#39;extraits de code
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'éditeur de code [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un **sélecteur d'extraits de code** qui vous permet, en quelques clics de souris, d'insérer des blocs de code prêts à l'emploi dans le document actif.  
  
 La procédure d'affichage du **sélecteur d'extrait de code** varie en fonction du langage que vous utilisez.  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, et sélectionnez **Insérer un extrait**.  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] \- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] \- Le **sélecteur d'extrait de code** n'est pas disponible.  
  
-   Visual F\# \- Le **Sélecteur d'extrait de code** n'est pas disponible.  
  
-   [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] \-\- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   XML \- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   HTML \- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   SQL \- Cliquez avec le bouton droit à l'emplacement voulu dans l'éditeur de code pour afficher le menu contextuel, et sélectionnez **Insérer un extrait**.  
  
 Dans la plupart des langages de développement Visual Studio, vous pouvez utiliser le  **Code Snippets Manager** pour ajouter des dossiers à la  **Liste des dossiers** qui le  **Sélecteur d'extrait de Code** analyse les fichiers d'extrait de code XML.  Vous pouvez également créer vos propres extraits de code à ajouter à la liste.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un extrait de code](../../ide/walkthrough-creating-a-code-snippet.md).  
  
## Liste UIElement  
 Nom de l'élément  
 Un champ de texte modifiable qui affiche le nom de l'élément sélectionné dans la **Liste d'éléments**.  Pour effectuer une recherche incrémentielle de l'élément que vous souhaitez, commencez à taper son nom dans ce champ.  Continuez d'ajouter des lettres jusqu'à ce que l'élément voulu soit sélectionné dans la **Liste d'éléments**.  
  
 Liste d'éléments  
 Une liste d'extraits de code disponible pouvant être insérés, ou une liste de dossiers contenant des extraits de code.  Pour insérer un extrait de code ou développer un dossier, sélectionnez l'élément concerné et appuyez sur Entrée.  
  
## Voir aussi  
 [Meilleures pratiques pour l'utilisation des extraits de code](../../ide/best-practices-for-using-code-snippets.md)   
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)   
 [Comment : utiliser des extraits de code Entourer de](../Topic/How%20to:%20Use%20Surround-with%20Code%20Snippets.md)