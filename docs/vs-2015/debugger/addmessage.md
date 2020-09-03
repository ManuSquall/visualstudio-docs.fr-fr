---
title: AddMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f01d4e80c3740ae27b5df8badbc74989c2da2c60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156513"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ajoute un message personnalisé à l’affichage à haute vue de Graphics Diagnostics *(affichage* principal).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 Message à ajouter au HUD.  
  
## <a name="remarks"></a>Notes  
 Le HUD Graphics Diagnostics s’affiche dans l’angle supérieur gauche de l’application exécutée dans Graphics Diagnostics. Il affiche des informations d’exécution sur l’application et sur la capture des informations graphiques, ainsi que des messages ajoutés en appelant cette fonction.  
  
 Pour ajouter un message à HUD, vous n’êtes pas obligé de capturer activement les informations graphiques, autrement dit, un message peut être ajouté par le biais d’une instance de la `VsgDbg` classe, mais la fonction membre [init](../debugger/init.md) ne doit pas être appelée en premier. Les messages s’affichent uniquement dans le HUD, ils ne sont pas enregistrés dans le fichier journal de graphisme.
