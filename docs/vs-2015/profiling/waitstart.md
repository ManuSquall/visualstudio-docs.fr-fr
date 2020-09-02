---
title: WaitStart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1737f13a5271b2c4012ff6ee957fa08b0b8b7799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164555"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 **Sortie :**`filename`  
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
