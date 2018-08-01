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
ms.openlocfilehash: 018d94f2952b8169890377410ff00baf1a80fd41
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176383"
---
# <a name="showwebbrowser-command"></a>Afficher le navigateur Web, commande

Affiche l’URL spécifiée dans une fenêtre de navigateur web au sein ou en dehors de l’environnement de développement intégré (IDE).

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

 Facultative. Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’environnement IDE.

## <a name="remarks"></a>Notes
 L’alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.

## <a name="example"></a>Exemple
 L’exemple suivant affiche la page d’accueil de MSDN Online dans un navigateur web en dehors de l’environnement IDE. S’il y a déjà une instance du navigateur web ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.

```cmd
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)