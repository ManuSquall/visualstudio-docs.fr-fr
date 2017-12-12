---
title: Afficher le navigateur web, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a54023892d1432639fd1211273195b941e8f081
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="showwebbrowser-command"></a>Afficher le navigateur Web, commande
Affiche l’URL que vous spécifiez dans une fenêtre de navigateur web au sein de l’environnement de développement intégré (IDE) ou externe à l’IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Arguments  
 `URL`  
 Obligatoire. URL (Uniform Resource Locator) du site web.  
  
## <a name="switches"></a>Commutateurs  
 /new  
 Facultatif. Spécifie que la page s’affiche dans une nouvelle instance du navigateur web.  
  
 /ext  
 Facultatif. Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’IDE.  
  
## <a name="remarks"></a>Remarques  
 L’alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche la page d’accueil de MSDN Online dans un navigateur web en dehors de l’IDE. Si une instance du navigateur web est déjà ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)