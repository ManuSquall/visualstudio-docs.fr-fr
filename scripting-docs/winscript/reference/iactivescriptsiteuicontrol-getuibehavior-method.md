---
title: Méthode IActiveScriptSiteUIControl::GetUIBehavior | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b52c94e9c8b14218362000df401fba24568ea426
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097303"
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