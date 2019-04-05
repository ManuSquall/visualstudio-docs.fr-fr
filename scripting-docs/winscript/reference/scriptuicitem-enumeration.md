---
title: Énumération SCRIPTUICITEM | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd454780b4360daf844697ad92ab8a4e9da29317
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151984"
---
# <a name="scriptuicitem-enumeration"></a>SCRIPTUICITEM, énumération
Représente le type d’élément d’interface utilisateur. Utilisé dans le [iactivescriptsiteuicontrol::getuibehavior, méthode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
typedef enum tagSCRIPTUICITEM {     SCRIPTUICITEM_INPUTBOX = 1,     SCRIPTUICITEM_MSGBOX = 2,     } SCRIPTUICITEM;   
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTUICITEM_INPUTBOX|Un contrôle d’entrée.|  
|SCRIPTUICITEM_MSGBOX|Une boîte de message.|