---
title: "Sélecteur d’extraits de code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e352baf834f026462cb35921f7f79e75b3aecd96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="code-snippet-picker"></a>Sélecteur d'extraits de code
L’éditeur de code [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un **sélecteur d’extraits de code** qui vous permet, en quelques clics de souris, d’insérer des blocs de code prêts à l’emploi dans le document actif.  
  
 La procédure d’affichage du **sélecteur d’extraits de code** varie en fonction du langage que vous utilisez.  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel et sélectionnez **Insérer un extrait**.  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] : le **sélecteur d’extraits de code** n’est pas disponible.  
  
-   Visual F# : le **sélecteur d’extraits de code** n’est pas disponible.  
  
-   [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   XML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   HTML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.  
  
-   SQL : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait**.  
  
Dans la plupart des langages de développement Visual Studio, vous pouvez utiliser le **Gestionnaire des extraits de code** pour ajouter des dossiers à la **Liste des dossiers** dans laquelle le **sélecteur d’extraits de code** recherche les fichiers d’extraits XML. Vous pouvez également créer vos propres extraits à ajouter à la liste. Pour plus d’informations, consultez [Procédure pas à pas : création d’un extrait de code](../../ide/walkthrough-creating-a-code-snippet.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
Nom d'élément  
Un champ de texte modifiable qui affiche le nom de l’élément sélectionné dans la **liste d’éléments**. Pour effectuer une recherche incrémentielle de l’élément souhaité, commencez à taper son nom dans ce champ. Continuez d’ajouter des lettres jusqu’à ce que l’élément voulu soit sélectionné dans la **liste d’éléments**.  
  
Liste d’éléments  
Une liste d’extraits de code disponibles pour être insérés, ou une liste de dossiers contenant des extraits de code. Pour insérer un extrait ou développer un dossier, sélectionnez l’élément voulu et appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
[Bonnes pratiques pour l’utilisation des extraits de code](../../ide/best-practices-for-using-code-snippets.md)   
[Extraits de code IntelliSense Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
[Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)   
[Guide pratique pour utiliser des extraits de code Entourer de](../../ide/how-to-use-surround-with-code-snippets.md)