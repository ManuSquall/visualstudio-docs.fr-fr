---
title: Afficher le navigateur Web, commande
description: En savoir plus sur la commande Afficher le navigateur Web et sur l’affichage de l’URL que vous spécifiez dans une fenêtre de navigateur Web, dans l’IDE ou externe à l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9117360d795a8027812b2534311a846d0ee56e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957606"
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

Facultatif. Spécifie que la page s’affiche dans une nouvelle instance du navigateur web.

/ext

Facultatif. Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’environnement IDE.

## <a name="remarks"></a>Notes
L’alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.

## <a name="example"></a>Exemple
L’exemple suivant affiche la page d’accueil de Microsoft Docs dans un navigateur web en dehors de l’IDE. S’il y a déjà une instance du navigateur web ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)