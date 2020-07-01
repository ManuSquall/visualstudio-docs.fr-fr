---
title: Afficher le navigateur Web, commande
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8266a7c70544d8a320658fcd8b9f5ad249162fe
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769571"
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

facultatif. Spécifie que la page s’affiche dans une nouvelle instance du navigateur web.

/ext

facultatif. Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’environnement IDE.

## <a name="remarks"></a>Remarques
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