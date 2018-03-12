---
title: Afficher le navigateur web, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="remarks"></a>Notes  
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
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)