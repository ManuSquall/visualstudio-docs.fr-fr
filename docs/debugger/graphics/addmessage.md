---
title: AddMessage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0050f5022b31020879b45e45da48546e5a7caa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="addmessage"></a>AddMessage
Ajoute un message personnalisé pour les diagnostics graphiques *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 Le message à ajouter au HUD.  
  
## <a name="remarks"></a>Notes  
 Le HUD de diagnostics graphiques s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant cette fonction.  
  
 Pour ajouter un message pour le HUD, vous n’êtes pas obligé de capturer activement les informations graphiques, autrement dit, un message peut être ajouté via une instance de la `VsgDbg` (classe), mais la [Init](init.md) fonction membre ne pas être appelé en premier. Les messages sont affichés dans le HUD, elles ne sont pas enregistrées dans le fichier journal de graphisme.