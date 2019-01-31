---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf17eb7a07a253aba8e82bd12cdb26d18f14dcb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946631"
---
# <a name="waitstart"></a>WaitStart
Quand l’option WaitStart est utilisée, la sous-commande Start de *VSPerfCmd.exe* est retournée uniquement après l’initialisation du profileur ou après le nombre spécifié de secondes. Par défaut, la commande Start est retournée immédiatement. Si la sous-commande Start est retournée sans initialiser le profileur, une erreur est retournée. Si le nombre de secondes n’est pas spécifié, la commande Start attend indéfiniment.  
  
 L’option WaitStart est utile dans les fichiers de commandes pour vérifier que le profileur a été initialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```