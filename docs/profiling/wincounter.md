---
title: WinCounter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9455d596e27526f6075ad3b667ac441b12511d58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779842"
---
# <a name="wincounter"></a>WinCounter
L’option **WinCounter** spécifie un compteur de performances Windows ou d’application à collecter à des intervalles définis pendant l’exécution du profil. Les compteurs de performances Windows et d’application sont répertoriés en tant que marques dans le fichier de données de profilage. Vous pouvez spécifier plusieurs compteurs de performances à collecter dans des options distinctes.

 Par défaut, les compteurs sont collectés toutes les 500 millisecondes. Utilisez l’option **AutoMark** pour spécifier un autre intervalle de collecte.

 Une seule option **AutoMark** est utilisée. Si plusieurs options **AutoMark** sont spécifiées, seule la dernière est utilisée.

 L’option **WinCounter** peut être utilisée seulement avec l’option **Start**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Paramètres
 `Path` Compteur de performances Windows au format de chemin de compteur PDH.

## <a name="required-options"></a>Options obligatoires
 L’option **WinCounter** peut être utilisée seulement avec l’option **Start**.

 **Démarrage :** `Method` **L’option Démarrer** initialise le profileur à la méthode de profilage spécifiée.

## <a name="exclusive-options"></a>Options exclusives
 L’option **AutoMark** peut être utilisée seulement avec l’option **WinCounter**.

 **AutoMark :** `Milliseconds` Specifie le nombre de millisecondes entre la collecte de données du compteur de performances Windows.

## <a name="example"></a> Exemple
 Dans l’exemple suivant, deux compteurs de performance Windows sont configurés être collectés à un intervalle de 1 000 millisecondes.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
