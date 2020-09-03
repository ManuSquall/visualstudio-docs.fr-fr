---
title: Afficher le navigateur web, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663520"
---
# <a name="showwebbrowser-command"></a>Afficher le navigateur Web, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche l’URL que vous spécifiez dans une fenêtre de navigateur web au sein de l’environnement de développement intégré (IDE) ou externe à l’IDE.

## <a name="syntax"></a>Syntaxe

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
 `URL` Obligatoire. URL (Uniform Resource Locator) du site web.

## <a name="switches"></a>Commutateurs
 /New facultatif. Spécifie que la page s’affiche dans une nouvelle instance du navigateur web.

 /ext (facultatif). Spécifie que la page s’affiche dans le navigateur web par défaut en dehors de l’IDE.

## <a name="remarks"></a>Notes
 L’alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.

## <a name="example"></a>Exemple
 L’exemple suivant affiche la page d’accueil de MSDN Online dans un navigateur web en dehors de l’IDE. Si une instance du navigateur web est déjà ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
