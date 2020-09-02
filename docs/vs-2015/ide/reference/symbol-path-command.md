---
title: Chemin d’accès aux symboles, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651002"
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit la liste des répertoires où le débogueur recherche des symboles.

## <a name="syntax"></a>Syntaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
 `pathname` Facultatif. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.

## <a name="remarks"></a>Notes
 Si aucun `pathname` n’est spécifié, la commande répertorie les chemins des symboles actuels.

## <a name="example"></a>Exemple
 Cet exemple ajoute deux chemins à la liste des répertoires de symboles.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Exemple
 Cet exemple affiche une liste de chemins des symboles actuels délimités par des points-virgules.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) de la [fenêtre commande](../../ide/reference/command-window.md)
