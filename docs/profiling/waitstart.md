---
title: WaitStart | Microsoft Docs
description: Découvrez que l’option WaitStart provoque le retour de la sous-commande VSPerfCmd.exe Start uniquement lorsque le profileur a été initialisé ou que le nombre de secondes spécifié est écoulé.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911479"
---
# <a name="waitstart"></a>WaitStart
Quand l’option WaitStart est utilisée, la sous-commande Start de *VSPerfCmd.exe* est retournée uniquement après l’initialisation du profileur ou après le nombre spécifié de secondes. Par défaut, la commande Start est retournée immédiatement. Si la sous-commande Start est retournée sans initialiser le profileur, une erreur est retournée. Si le nombre de secondes n’est pas spécifié, la commande Start attend indéfiniment.

 L’option WaitStart est utile dans les fichiers de commandes pour vérifier que le profileur a été initialisé.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Paramètres
 `Seconds` Nombre de secondes d’attente avant que la sous-commande Start ne soit retournée.

## <a name="required-options"></a>Options obligatoires
 L’option WaitStart ne peut être utilisée qu’avec la sous-commande Start.

 **Sortie :** `filename` Spécifie le nom du fichier de sortie.

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
