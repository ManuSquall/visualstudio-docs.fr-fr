---
title: Méthode IActiveScriptSiteUIControl::GetUIBehavior | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992231"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>IActiveScriptSiteUIControl::GetUIBehavior, méthode
Obtient un [scriptuichandling, énumération](../../winscript/reference/scriptuichandling-enumeration.md) qui représente la façon dont un contrôle d’interface utilisateur doit-elle être traité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>Paramètres  
 `UicItem`  
 Type du contrôle.  
  
 `pUicHandling`  
 La façon dont le contrôle doit être gérée.