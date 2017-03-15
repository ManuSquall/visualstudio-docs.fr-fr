---
title: WaitStart | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4b06fbd524d38e339a8196842200ec3743ee31f4
ms.lasthandoff: 02/22/2017

---
# <a name="waitstart"></a>WaitStart
Quand l’option WaitStart est utilisée, la sous-commande VSPerfCmd.exe Start est retournée uniquement après l’initialisation du profileur ou après le nombre spécifié de secondes. Par défaut, la commande Start est retournée immédiatement. Si la sous-commande Start est retournée sans initialiser le profileur, une erreur est retournée. Si le nombre de secondes n’est pas spécifié, la commande Start attend indéfiniment.  
  
 L’option WaitStart est utile dans les fichiers de commandes pour vérifier que le profileur a été initialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Seconds`  
 Nombre de secondes d’attente avant que la sous-commande Start ne soit retournée.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option WaitStart ne peut être utilisée qu’avec la sous-commande Start.  
  
 **Output:** `filename`  
 Spécifie le nom du fichier de sortie.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Dans cet exemple de fichier de commandes, la commande Start attend 5 secondes que le profileur s’initialise.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```
