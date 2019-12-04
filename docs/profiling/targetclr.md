---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771599"
---
# <a name="targetclr"></a>TargetCLR
L’option **TargetCLR** spécifie la version du common language runtime (CLR) à profiler quand plusieurs versions du CLR sont chargées dans une application.

 Par défaut, les Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ciblent la première version du CLR qui est chargée par l’application.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parameters
 `ClrVersion` Numéro de version du CLR. Utilisez le format de version **vN.N.NNNNN**.

## <a name="required-options"></a>Options obligatoires
 L’option **TargetCLR** peut être utilisée seulement avec l’option **Launch** ou **Attach**.

 **Launch :** `AppName` démarre l’application spécifiée et démarre le profilage.

 **Attacher :** `PID` démarre le profilage du processus spécifié.

## <a name="example"></a>Exemple
 Dans cet exemple, l’option TargetCLR est utilisée pour profiler la version 4.0.11003 du CLR.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
