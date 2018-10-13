---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b60f8bac24b01e39327357b89e9e96c04765077
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249000"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ajoute un message personnalisé pour les diagnostics graphiques *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 Le message à ajouter à la HUD.  
  
## <a name="remarks"></a>Notes  
 Graphics diagnostics HUD s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant cette fonction.  
  
 Pour ajouter un message au HUD, vous n’êtes pas obligé d’être activement capture d’informations graphiques, autrement dit, un message peut être ajouté via une instance de la `VsgDbg` (classe), mais la [Init](../debugger/init.md) fonction membre n’afin de ne pas être appelée en premier. Les messages sont affichés uniquement dans le HUD, elles ne sont pas enregistrées dans le fichier journal de graphisme.



