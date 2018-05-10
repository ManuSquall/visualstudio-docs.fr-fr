---
title: Afficher le navigateur Web, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4beed25b1cdbc9f298df32743b9fec2e59fcdd8b
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="showwebbrowser-command"></a>Afficher le navigateur Web, commande
Affiche l’URL que vous spécifiez dans une fenêtre de navigateur web au sein de l’environnement de développement intégré (IDE) ou externe à l’IDE.

## <a name="syntax"></a>Syntaxe

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
 `URL`

 Obligatoire. URL (Uniform Resource Locator) du site web.

## <a name="switches"></a>Commutateurs
 /new

 Facultative. Spécifie que la page s’affiche dans une nouvelle instance du navigateur web.

 /ext

 Facultative. Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’IDE.

## <a name="remarks"></a>Notes
 L’alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.

## <a name="example"></a>Exemple
 L’exemple suivant affiche la page d’accueil de MSDN Online dans un navigateur web en dehors de l’IDE. Si une instance du navigateur web est déjà ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.

```cmd
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)