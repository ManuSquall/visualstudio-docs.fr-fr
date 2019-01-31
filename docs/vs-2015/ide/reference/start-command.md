---
title: Démarrer, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f08baa8c27debf6493ca090a2a5e80f02b3da982
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774453"
---
# <a name="start-command"></a>Démarrer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Commence le débogage du projet de démarrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Optionnel. Adresse à laquelle le programme suspend son exécution, semblable à un point d’arrêt dans le code source. Cet argument est valide uniquement en mode débogage.  
  
## <a name="remarks"></a>Notes  
 Quand elle est exécutée, la commande **Start** effectue une opération RunToCursor vers l’adresse spécifiée.  
  
## <a name="example"></a>Exemple  
 Cet exemple démarre le débogueur et ignore toute exception qui peut se produire.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
