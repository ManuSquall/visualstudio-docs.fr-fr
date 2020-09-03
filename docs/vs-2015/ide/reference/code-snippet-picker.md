---
title: Sélecteur d’extraits de code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2918826d6923efa3db42f4f572c416b9668513a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660899"
---
# <a name="code-snippet-picker"></a>Sélecteur d'extraits de code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’éditeur de code [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit un **sélecteur d’extraits de code** qui vous permet, en quelques clics de souris, d’insérer des blocs de code prêts à l’emploi dans le document actif.

 La procédure d’affichage du **sélecteur d’extraits de code** varie en fonction du langage que vous utilisez.

- [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel et sélectionnez **Insérer un extrait**.

- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] : le **sélecteur d’extraits de code** n’est pas disponible.

- Visual F# : le **sélecteur d’extraits de code** n’est pas disponible.

- [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] --Cliquez avec le bouton droit à l’emplacement de votre choix dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **entourer de**.

- XML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- HTML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- SQL : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait**.

  Dans la plupart des langages de développement Visual Studio, vous pouvez utiliser le **Gestionnaire des extraits de code** pour ajouter des dossiers à la **Liste des dossiers** dans laquelle le **sélecteur d’extraits de code** recherche les fichiers d’extraits XML. Vous pouvez également créer vos propres extraits à ajouter à la liste. Pour plus d’informations, consultez [Procédure pas à pas : création d’un extrait de code](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 Nom d’élément champ de texte modifiable qui affiche le nom de l’élément sélectionné dans la **liste d’éléments**. Pour effectuer une recherche incrémentielle de l’élément souhaité, commencez à taper son nom dans ce champ. Continuez d’ajouter des lettres jusqu’à ce que l’élément voulu soit sélectionné dans la **liste d’éléments**.

 Liste d’éléments liste des extraits de code disponibles pour l’insertion, ou liste de dossiers contenant des extraits de code. Pour insérer un extrait ou développer un dossier, sélectionnez l’élément voulu et appuyez sur Entrée.

## <a name="see-also"></a>Voir aussi
 [Meilleures pratiques pour l’utilisation d’extraits de code Visual Basic les](../../ide/best-practices-for-using-code-snippets.md) [extraits de code IntelliSense](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [définition de signets dans le code](../../ide/setting-bookmarks-in-code.md) [Comment : utiliser des extraits de code entourer](../../ide/how-to-use-surround-with-code-snippets.md) de
