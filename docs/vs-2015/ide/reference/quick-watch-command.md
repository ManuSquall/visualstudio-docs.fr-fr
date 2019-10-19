---
title: Espion express, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665667"
---
# <a name="quick-watch-command"></a>Espion express, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche le texte sélectionné ou spécifié dans le champ Expression de la boîte de dialogue [Espion express](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Vous pouvez utiliser cette boîte de dialogue pour calculer la valeur actuelle d’une variable ou d’une expression reconnue par le débogueur, ou le contenu d’un Registre. Vous pouvez aussi modifier la valeur de toute variable non constante ou le contenu de tout Registre.

## <a name="syntax"></a>Syntaxe

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments
 `text` Facultatif. Texte à ajouter à la boîte de dialogue **Espion express**.

## <a name="remarks"></a>Remarques
 Si l’argument `text` est omis, le texte ou mot sélectionné au niveau du curseur est ajouté dans la fenêtre Espion.

## <a name="example"></a>Exemples

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Voir aussi
 [Comment : utiliser la boîte de dialogue Espion express](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
