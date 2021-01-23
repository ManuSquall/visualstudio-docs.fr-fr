---
title: TargetCLR | Microsoft Docs
description: Découvrez comment l’option TargetCLR spécifie la version du Common Language Runtime à profiler lorsque plusieurs versions du CLR sont chargées dans une application.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dff098dc5b893ce394698118d53ae6a96fc8b28a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719810"
---
# <a name="targetclr"></a>TargetCLR
L’option **TargetCLR** spécifie la version du common language runtime (CLR) à profiler quand plusieurs versions du CLR sont chargées dans une application.

 Par défaut, les Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ciblent la première version du CLR qui est chargée par l’application.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Paramètres
 `ClrVersion` Numéro de version du CLR. Utilisez le format de version **vN.N.NNNNN**.

## <a name="required-options"></a>Options obligatoires
 L’option **TargetCLR** peut être utilisée seulement avec l’option **Launch** ou **Attach**.

 **Lancer :** `AppName` Démarre l’application spécifiée et commence le profilage.

 **Attacher :** `PID` Démarre le profilage du processus spécifié.

## <a name="example"></a>Exemples
 Dans cet exemple, l’option TargetCLR est utilisée pour profiler la version 4.0.11003 du CLR.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
